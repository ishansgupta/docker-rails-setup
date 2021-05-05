## Description

Instruction to create a Postgres+Rails docker container

## Setup

1. Build the project

`docker-compose run --no-deps web rails new . --force --database=postgresql`

2. `docker-compose build`

3. Update `config/database.yml`

```
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password: password
  pool: 5

development:
  <<: *default
  database: app_development


test:
  <<: *default
  database: app_test
```

4. Boot the app with with `docker-compose up`

5. Create db (another terminal) `docker-compose run web rake db:create`

6. Launch rails console `docker-compose run web rails console` (Optional)
