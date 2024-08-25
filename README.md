# ton-docker-ctrl

Tested operating systems:
* Ubuntu 20.04
* Ubuntu 22.04
* Ubuntu 24.04
* Debian 11
* Debian 12

## Prerequisites
To run, you need docker-ce, docker-buildx-plugin, docker-compose-plugin:

* [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
* [Install Docker Engine on Debian](https://docs.docker.com/engine/install/debian/)

Build environment variables (are configured in the .env file):

* **GLOBAL_CONFIG_URL** - URL of the TON blockchain configuration (default: [Mainnet](https://ton.org/global.config.json))
* **MYTONCTRL_VERSION** - MyTonCtrl build branch (default **master**)
* **TELEMETRY** - Enable/Disable telemetry (default **true**)
* **IGNORE_MINIMAL_REQS** - Ignore hardware requirements (default **false**) 
* **MODE** - Install MyTonCtrl with specified mode (validator or liteserver, default **validator**)
* **DUMP** - Use pre-packaged dump. Reduces duration of initial synchronization, but it takes time to download the dump. You can view the download status in the logs `docker compose logs -f`. (default **false**).

## Run MyTonCtrl v2 in docker:
* Run `docker run -d --name ton-node -v /mnt/data/ton-work1:/var/ton-work -it ghcr.io/neodix42/ton-docker-ctrl:v2024.08`

## Build Docker image from sources and run MyTonCtrl v2:

* Clone: `git clone https://github.com/ton-community/ton-docker-ctrl.git && cd ./ton-docker-ctrl`
* Run: `docker compose up --build -d`
* Connect `docker compose exec -it node bash -c "mytonctrl"`

## Upgrade MyTonCtrl docker image from repository:
* Pull docker image: `docker pull docker pull ghcr.io/ton-community/ton-docker-ctrl:latest`

## Upgrade MyTonCtrl docker images from sources:

* Build new image: `docker compose build ton-node`
* Run new version: `docker compose up -d`
