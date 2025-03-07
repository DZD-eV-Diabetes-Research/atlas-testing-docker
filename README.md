# atlas-testing-docker

Docker compose for starting a local [OMOP CDM](https://ohdsi.github.io/CommonDataModel/) Postgres database and a [OHDSI Atlas instance](https://github.com/OHDSI/Atlas)

**Status**: WIP

**Maintainer**: Tim Bleimehl

# Usage

requirements:

- git
- docker with docker compose

## First time setup

- Clone this repo

```bash
git clone git@github.com:DZD-eV-Diabetes-Research/atlas-testing-docker.git
```
- Change to the new dir

```bash
cd atlas-testing-docker
```
- create a `.env` file

```bash
cp sample.env .env
```
Have a look into the `.env` file and adapt it to you needs.

## First time start

- Pull the up2date docker images

```bash
docker compose pull
```
- Start the docker compose

```bash
docker compose up
```
- **Wait** some time to let the database be provisioned (created and filled with data). you will see some log message from `omop-provision-1 | `. If you load a large Athena Vocabulary on a slow machine, you even wait for more than a hour. But you will always see what happening in the log messages.

- When you see log messages from `atlas-testing-docker-webapi-1 | ` **wait at least one more minute**. The Atlas WebAPI will now deploy its database scheme.

- Exit the compose with `ctrl`+`c`

- Shutdown the compose

```bash
docker compose down
```
## Regular start

Your setup is now complete. Your database is ready.
From now on you can simply start and stop the Atlas Setup as you like.

- Start with

```bash
docker compose up -d
```
- Stop with

```bash
docker compose down
```
If you need to troubleshot something check the logs with:

```bash
docker compose logs -f
```
(exit this by pressing the keys `ctrl`+`c`)

## Access Atlas

Now visit http://localhost:8080/atlas/

optional visit http://localhost:8080/WebAPI for inspecting the

# Known issues

- CORS disabled config is not applied by webapi process. At the moment this is mitigated by having an nginx as reverse proxy to server webapi and atlas from the same host.
