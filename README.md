# docker-rails

Steps followed creating a rails project using docker.

## 1 Build the image

```bash
docker build -t rails-toolbox \
       --build-arg USER_ID=$(id -u)  \
       --build-arg GROUP_ID=$(id -g) \
       -f Dockerfile.rails .
```

## 2 Create new rails app

-T ignores minitest
-d sets database to postgresql

```bash
docker run -it \
    -v $PWD:/opt/app \
    rails-toolbox rails new --skip-bundle drkiq -T -d=postgresql

rm -rf drkiq/.git
```

Copy the `env-example` file to `.env` and customise it as necessary.

*Change the `SECRET_TOKEN` **before** you do anything else*.

Current state: borked, but not as bad.

```bash
nginx_1     | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
nginx_1     | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
nginx_1     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
nginx_1     | 10-listen-on-ipv6-by-default.sh: info: IPv6 listen already enabled
nginx_1     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
nginx_1     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
nginx_1     | /docker-entrypoint.sh: Configuration complete; ready for start up
nginx_1     | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
nginx_1     | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
nginx_1     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
drkiq_1     | I, [2021-03-07T18:49:08.633782 #6]  INFO -- : Refreshing Gem list
nginx_1     | 10-listen-on-ipv6-by-default.sh: info: IPv6 listen already enabled
nginx_1     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
nginx_1     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
nginx_1     | /docker-entrypoint.sh: Configuration complete; ready for start up


``
