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

`git clone git@github.com:DZD-eV-Diabetes-Research/atlas-testing-docker.git`

- Change to the new dir

`cd atlas-testing-docker`

- create a `.env` file

`cp sample.env .env`

Have a look into the `.env` file and adapt it to you needs.

## Start

- Pull the up2date docker images

`docker compose pull`

- Start the docker compose

`docker compose up -d`

- Wait for the whole thing started

You can check what is happening with

`docker compose logs -f` (exit this by pressing the keys `ctrl`+`c`)

If you load vocabulary you maybe have to wait substantial time on the first start. up to an hour if you load a large set of vocabulary.
On next start this is allready done and it will only take 1-2 Minutes for everything to be up.

## Access Atlas

Now visit http://localhost:8080/atlas/

optional visit http://localhost:8080/WebAPI for inspecting the

# Known issues

- CORS disabled config is not applied by webapi process.
