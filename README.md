# Shared MySQL Docker Container

## Setup
- Clone the repository
- Copy `docker-compose.dev.yml` to `docker-compose.override.yml`
- Configure `docker-compose.override.yml`
- Execute `docker-compose up -d`

## Starting the services
Execute `docker-compose start`

## Stopping the services
Execute `docker-compose stop`

## Connecting the project containers
Modify the existing project's `docker-compose.override.yml` file to join the shared MySQL network.

### Add the reference to the shared MySQL network
``` yml
networks:
  shared_db:
    external:
      name: shared-mysql-container_default
```

### Connect the application container to the shared MySQL network
``` yml
app:
    build: .
    ...
    networks:
      - shared_db
```

## Host-to-container connection settings

```
Hostname: 127.0.0.1
Port: 3306
Username: root
Password: password
```

## Container-to-container connection settings

```
Hostname: mysql
Port: 3306
Username: root
Password: password
```
