# Docker compose
## Build

Just unquote everything in "docker-compose.yml" and use 

```
docker-compose build
```

## Run

For start service with backend.v1 just quote part with second service in "docker-compose.yml" and run

```
docker-compose up -d
```

and you can go http://localhost:4100


## reload and update

```
docker-compose down
```

Then quote v1 and unqote v2, and tehen 

```
docker-compose up -d
```