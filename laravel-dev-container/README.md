# Laravel dev container
Containers for developing and deploying [Laravel](https://laravel.com) projects.

# Starting a new project
First, build and run the workspace image:

```shell
$ docker build -f ./development/workspace/Dockerfile -t <namespace>/workspace:php-8.4 .
$ docker run -it -v <local development path>:/var/www <namespace>workspace:php-8.4
```

Then, create a new Laravel project using the [Laravel installer](https://laravel.com/docs/12.x/installation#creating-an-application):

```shell
$ laravel new <project name>
```
