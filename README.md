## Setup

Run `id` commmand on your terminal to find out your UID and GID.

Copy the values for the UID and GID then run the command below
```
docker-compose build --build-arg ARG_UID={UID} ARG_GID={GID} php
```

This will build the php image with a user having the same uid and gid as yours
that would allow the container to create and modify files without any issues.

Copy the `.env.example` file to `.env` and modify the PHP_GID AND PHP_UID as well.

Run `docker-compose up -d`

The access the php container run `docker exec -it putti-app bash` and run `composer install`
