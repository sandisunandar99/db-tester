# db-tester
test database untuk development

## MongoDB local development

Run MongoDB only:

```bash
docker compose -f mongo-docker-compose.yml up -d
```

Run MongoDB + mongo-express:

```bash
docker compose -f mongo-docker-compose.yml --profile tools up -d
```

Optional environment variables:

```bash
MONGO_PORT=27017
MONGO_IMAGE_TAG=4.4.29
MONGO_ROOT_USERNAME=mongodb
MONGO_ROOT_PASSWORD=mongodb
MONGO_DATABASE=app
MONGO_EXPRESS_PORT=8082
MONGO_EXPRESS_USERNAME=admin
MONGO_EXPRESS_PASSWORD=admin
```

Notes:
- Ports are bound to localhost for safer local usage.
- `mongo-express` is disabled by default and enabled via profile `tools`.
- MongoDB container includes a healthcheck and `mongo-express` waits until MongoDB is healthy.
- Default `MONGO_IMAGE_TAG` is `4.4.29` to stay compatible with older local data volumes (FCV 4.2).
- Default mongo-express login: `admin` / `admin` (override with `MONGO_EXPRESS_USERNAME` and `MONGO_EXPRESS_PASSWORD`).
