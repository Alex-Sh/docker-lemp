# DOCKER LEMP
Simple Docker LEMP stack for development.
- Nginx
- PHP 7.4-fpm
- MySQL 8
- Symfony 5 ready

## Installation

> You need to make sure you have Docker properly setup in your environment. Check official documentation for [Docker](https://docs.docker.com/) and [Docker Compose](https://docs.docker.com/compose/).

Clone this repository:

```bash
git clone https://github.com/Alex-Sh/docker-lemp.git
```
Edit hosts file and add `127.0.0.1 loc.app.com`.

Configure `docker/nginx/app.conf` for your application. Current config is Symfony5 ready.

Put your application into `app` folder and configure database parameters. For example: `DATABASE_URL=mysql://app:app@db:3306/app?serverVersion=8.0`

Run
```bash
docker-compose up
```

*to rebuild*

```bash
docker-compose build
```

You can run commands to build your application using (ex.):
```bash
docker-compose exec php composer install
```

## Project structure

```sh

├── app
├── docker
│   ├── logs
│   │   ├── app
│   │   └── nginx
│   ├── mysql
│   │   └── data
│   ├── nginx
│   │   ├── app.conf
│   │   └── nginx.conf
│   ├── php
│   │   ├── app.ini
│   │   └── Dockerfile
└── docker-compose.yml
```

## WARNING

Servers are configured for developments purposes. Do not deploy this project on production as is.
