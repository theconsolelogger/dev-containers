# Laravel dev container
Containers for developing and deploying [Laravel](https://laravel.com) projects.

# Starting a new project
First, build and run the workspace image:

```shell
$ docker build -f ./development/workspace/Dockerfile -t <namespace>/workspace:php-8.4 .
$ docker run -it -v <local development path>:/var/www <namespace>workspace:php-8.4
```

Create a new Laravel project using the [Laravel installer](https://laravel.com/docs/12.x/installation#creating-an-application):

```shell
$ laravel new <project name>
```

Change the env vars in the .env to the following:

```
DB_CONNECTION=pgsql
DB_HOST=database
DB_PORT=5432
DB_DATABASE=app
DB_USERNAME=laravel
DB_PASSWORD=secret

# Docker container env vars
UID=<uid>
GID=<gid>
```

> uid and gid can be found using the `id` on macOS.

Run the dev environment:

```shell
$ docker compose -f compose.dev.yml up -d
```

Migrate the database:

```shell
$ docker attach <workspace container name>
$ php artisan migrate
```

The dev environment can be stopped with:

```shell
$ docker compose -f compose.dev.yml down
```

Logs for the dev environment can be seen with:

```shell
$ docker compose -f compose.dev.yml logs -f
```
