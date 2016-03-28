# Docker registry

The repository contains configuration files necessary to run a standalone docker registry backed by an S3 bucket. The implementation is based on docker-compose.

## Prerequisites

You should install [docker](https://docs.docker.com/engine/installation/) and [docker-compose](https://docs.docker.com/compose/install/) before going any further.

## Repository content

* **compose.yml**: docker compose configuration file running redis container (registry cache) and the registry itself.
* **registry.yml**: docker registry configuration file based on [official documentation](https://docs.docker.com/registry/configuration/)
* **env.sh**: a script injecting environment variables into _registry.yml_ and _compose.yml_ files to build the final configuration (_registry_config.yml_ and _docker_compose.yml_ files).

## Usage howto

In order to run the setup one need to create the following environment variables:

```
CERTS_PATH=%path to the certificates folder%
AUTH_PATH=%path to the basic auth configuration%
S3_ACCESSKEY=%S3 bucket's access key%
S3_ACCESSSECRET=%S3 bucket's access secret%
REGISTRY_SECRET=%random string used as secret between the registry and the cache%
```

The command to launch the registry is (inside the sources folder):

```bash
./env.sh && docker-compose up -d
```
