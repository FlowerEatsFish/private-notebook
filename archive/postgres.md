# To learn how to create PostgreSQL using Docker

- [To learn how to create PostgreSQL using Docker](#to-learn-how-to-create-postgresql-using-docker)
  - [To pull an image](#to-pull-an-image)
  - [To put saved data on host](#to-put-saved-data-on-host)
  - [To create a container via an image and maintain it in running](#to-create-a-container-via-an-image-and-maintain-it-in-running)
    - [Environment Variables](#environment-variables)
  - [To enter a container and run on PostgreSQL environment](#to-enter-a-container-and-run-on-postgresql-environment)
  - [To exit from a container but maintain it in running](#to-exit-from-a-container-but-maintain-it-in-running)

## To pull an image

- Reference: [https://hub.docker.com/_/postgres/](https://hub.docker.com/_/postgres/)

```bash
docker pull postgres:9.6.10-alpine
```

## To put saved data on host

```bash
docker volume create postgres_db
```

## To create a container via an image and maintain it in running

### Environment Variables

    - POSTGRES_PASSWORD
    - POSTGRES_USER
    - PGDATA
    - POSTGRES_DB
    - POSTGRES_INITDB_ARGS
    - POSTGRES_INITDB_WALDIR

```bash
docker run -itd --name database -v postgres_db:/var/lib/postgresql/data/ -e POSTGRES_PASSWORD=mypassword -d -p 5432:5432 postgres:9.6.10-alpine
```

## To enter a container and run on PostgreSQL environment

```bash
docker exec -it database bash
```

```sql
psql -U postgres

CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypassword';

CREATE DATABASE mydatabase;

GRANT ALL PRIVILEGES ON DATABASE mydatabase TO myuser;

\q
```

```sql
psql -d mydatabase -U myuser

CREATE TABLE mytable (
  id SERIAL PRIMARY KEY,
  first_column text
);

INSERT INTO mytable (first_column)
  VALUES ('my_value');

\q
```

## To exit from a container but maintain it in running

```bash
ctrl + d
```
