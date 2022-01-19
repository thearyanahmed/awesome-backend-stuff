# docker-compose

## commands

```bash
docker-compose start
docker-compose stop
docker-compose pause
docker-compose unpause
docker-compose ps
docker-compose up // ups all containers
docker-compose down
```

## file

### Environments
```yml
  environment:
    RACK_ENV: development
  environment:
    - RACK_ENV=development
  # environment vars from file
  env_file: .env
  env_file: [.env, .development.env]
```

### Commands
```yml
  command: bundle exec thin -p 3000
  command: [bundle, exec, thin, -p, 3000]
  # override the entrypoint
  entrypoint: /app/start.sh
  entrypoint: [php, -d, vendor/bin/phpunit]
```

### Dependencies
```yml
  # makes the `db` service available as the hostname `database`
  # (implies depends_on)
  links:
    - db:database
    - redis
  # make sure `db` is alive before starting
  depends_on:
    - db
```

### Volumes & Extending
```yml
  # make this service extend another
  extends:
    file: common.yml  # optional
    service: webapp
  volumes:
    - /var/lib/mysql
    - ./_data:/var/lib/mysql
```

### Volume
```yml
# Mount host paths or named volumes, specified as sub-options to a service
  db:
    image: postgres:latest
    volumes:
      - "/var/run/postgres/postgres.sock:/var/run/postgres/postgres.sock"
      - "dbdata:/var/lib/postgresql/data"

volumes:
  dbdata:
```
### DNS
```yml
services:
  web:
    dns: 8.8.8.8
    dns:
      - 8.8.8.8
      - 8.8.4.4
```