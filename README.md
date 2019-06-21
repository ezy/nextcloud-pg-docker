# Simple Nextcloud with Postgres from docker-compose

This repository contains a Docker compose file which can be used to easily create a Nextcloud instance connected to pg.

- Fully-featured Nextcloud instance backed by a Postgres database
- All volume data stored locally

![](nc_screenshot.png)

## Architecture

Here are the various containers involved.

- `nextcloud`: the Nextcloud server
- `postgres`: the database used by Nextcloud to store its configuration
- `reverse-proxy`: a nginx reverse proxy in front of Nextcloud and doing SSL termination
- `letsencrypt-companion`: an utility container which issues and renews SSL certificates
- `backups`: an utility container which regularly backups the Nextcloud files and database

## Usage

Follow the steps below to get nextcloud running in docker on localhost

- Configure the .env files with the creds for your postgres db and admin user
- Run `docker-compose up` then connect to your postgres instance
- Create your db as per `POSTGRES_DB`
- Restart your nextcloud container
- Run `docker-compose restart`
- Open nextcloud at `localhost:8080` and login with `NEXTCLOUD_ADMIN_USER` and `NEXTCLOUD_ADMIN_PASSWORD`

Run on your server without shell:

```
$ docker-compose up -d
```
