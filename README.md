## Онлайн магазин
```bash
docker network create local-apps
```
```bash
docker run --name db-pg13 \
    -e POSTGRES_PASSWORD=postgres \
    -e POSTGRES_INITDB_ARGS="--locale=C.UTF-8" \
    --network="local-apps" \
    --restart always \
    -v ~/Documents/storedata/postgres/:/var/lib/postgresql/data \
    -p 5433:5432 \
    -d postgres:13.0-alpine
```
```sql
CREATE USER store CREATEDB LOGIN PASSWORD 'super_mega_store_password';
CREATE DATABASE store WITH OWNER = store CONNECTION LIMIT = -1;
GRANT ALL PRIVILEGES ON DATABASE store to store;
```