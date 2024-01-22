## Installing docker container
## Running first docker container

## Running Docker container with postgres (Standalone)
``` docker
docker run -it \ 
-e POSTGRES_USER="root"\
-e POSTGRES_PASSWORD="root"\
-e POSTGRES_DB="ny_taxi" \
-v C:/Users/shres/Documents/DataTalks/Docker_sql/ny_taxi_postgres_data:/var/lib/postgresql/data \
-p 5432:5432 \
postgres:16
```
## Testing the Docker container with postgres

## Running Docker container with pgadmin(standalone)
``` docker
docker run -it \
-e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
-e PGADMIN_DEFAULT_PASSWORD="root" \
-p 8080:80 \
dpage/pgadmin4
## Testing the Docker container with Pgadmin
```

## Building network of the docker container
``` docker
docker network create pg-network
```
## Testing the network 
#### Running docker container with postgres in network
``` docker
docker run -it \
-e POSTGRES_USER="root" \
-e POSTGRES_PASSWORD="root" \
-e POSTGRES_DB="ny_taxi" \
-v C:/Users/shres/Documents/DataTalks/Docker_sql/ny_taxi_postgres_data:/var/lib/postgresql/data\
-p 4532:5432 \
--network=pg-network\
--name pg-database \
postgres:16
```
#### Running docker container with pgadmin in network
``` docker
docker run -it \
-e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
-e PGADMIN_DEFAULT_PASSWORD="root" \
-p 8080:80 \
--network=pg-network \
--name pgadmin \
dpage/pgadmin4
```
## using docker compose to run all container