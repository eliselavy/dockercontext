# Docker compose and Django

 Simple Django project connected to PostgresSQL

Look at here:
<https://docs.docker.com/compose/django/>

Some change in the psotgres image: look at here:  <https://hub.docker.com/_/postgres>

With **docker-compose**

```
# Use postgres/example user/password credentials
version: '3.1'

services:

  db:
    image: postgres
    restart: always
    environment:
      POSTGRES_PASSWORD: example
```

Need to define a password, we add also in the settings.py

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'HOST': 'db',
        'PASSWORD': 'root',
        'PORT': 5432,

    }
}
```

 **'HOST': 'db'**  linked to the db service defined in the docker-compose.yml
Need to define the netword bridge in order to have access locally to the db:

```
 ports:
      - "5432:5432"
```

port inside the container: port outside the container