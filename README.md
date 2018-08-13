# composer

Dockerized PHP composer built on php:7.2-alpine image for cloud builds.

## environment variables
TOKEN: oAuth_token_string

allows Composer to access private packages.

## example docker-compose.yaml
```
version: "3"

services:

  composer:
    hostname: composer
    container_name: composer
    image: crunchgeek/composer:7.2
    working_dir: /app
    command: [ "install" ]
    volumes:
      - ./app:/app:cached
      - composer:/app/vendor
    networks:
      - backend
    # composer access token for Laravel Spark private repo
    environment:
      - TOKEN=GITHUB_TOKEN_HERE

volumes:
  composer:
    driver: "local"
```
