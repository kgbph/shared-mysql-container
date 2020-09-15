# Shared MySQL Container

## Setup
- Clone repository
- Create and configure `docker-compose.override.yml` file
- Execute `docker-compose up -d`

## Starting services
`docker-compose start`

## Stopping services
`docker-compose stop`

## Configuration for existing projects

Modify the existing project's `docker-compose.yml` or `docker-compose.override.yml` file to join the shared MySQL service's network.

### Define the shared network connections
``` yml
networks:
  shared_db:
    external:
      name: shared-mysql-container_default
```

### Connect the app container to network
``` yml
app:
    build: .
    ...
    networks:
      - shared_db
```

## Connecting app to MySQL service

```
Hostname: mysql
Port: 3306
Username: root
Password: password
```

## Connecting MySQL Workbench to MySQL service

```
Hostname: 127.0.0.1
Port: 3306
Username: root
Password: password
```
