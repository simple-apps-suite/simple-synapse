Simple Synapse
==============

This app is part of the _Simple Apps_ suite: a series of minimal self-hostable
web apps designed to improve your productivity without compromising on security
and privacy.

This is _Simple Synapse_: scripts and configuration files to launch Synapse for
use as the backend service for _Simple Apps_.


## Requirements

This server currently only runs on Linux on [Docker](https://www.docker.com/).


## Getting Started

From this directory execute the following command to generate the default
configuration for a new Synapse server:

```bash
mkdir data
docker compose run -i --rm --user "$(id -u):$(id -g)" -e SYNAPSE_SERVER_NAME=localhost -e SYNAPSE_REPORT_STATS=no synapse generate
```

Wait for the configuration to be generated, then start Synapse with the
following command:

```bash
GID=$(id -g) docker compose up
```

By default, the server will store data on a new local SQLite database, and is
accessible at http://localhost:8008.

To generate a new user run the following command while Synapse is running:

```bash
docker exec -it synapse register_new_matrix_user -c /data/homeserver.yaml
```

For more information about the available settings and commands, see the
[Synapse page on Docker Hub](https://hub.docker.com/r/matrixdotorg/synapse).
