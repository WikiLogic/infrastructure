# Wikilogic Infrastructure

Pulls together the WL cogs into one big pretty engine

Each service (or "cog") is in it's own repository, which is included within this one as a [git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

## ./\_configs

There are a few variations of server set up for WL, the configuration files for each are in `./_configs` - they also happen to kind of reflect the architectural roadmap.

### monolith-http

Everything is built into a single docker image. This is meant to be the simplest set up to give the development of this project a bit of a kick. It'll also hopefully make deployment & running it quit easy.

TODO: Figure out how to get it all running on the one container.

### monolith-https

TODO: set up ssl for the single image version of WL

### microservice-http

* **nginx**: Reverse proxy the API and serves the static FED assets. Until we do an isomorphic version, then that will get split out into it's own container.
* **api**: Currently an all in one express.js server.
* **arango**: The database server, just the arango docker image

TODO: Look into splitting out a data volume container
TODO: Orcastration with Kubernetes

### microservice-https

TODO: apply ssl to the microservice version
