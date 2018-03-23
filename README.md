# Wikilogic Infrastructure

**Clone the repo and it's sub-repos:**

 - git 2.13+ `git clone --recurse-submodules -j8 https://github.com/WikiLogic/infrastructure.git`
 - For older versions of git [see this stackoverflow](https://stackoverflow.com/questions/3796927/how-to-git-clone-including-submodules). `git --version`

**Run WL**

 - `cd _configs/microservice-http`  
 - `docker-compose up`  
 - http://localhost/

Each service (or "cog") is in it's own repository, which is included within this one as a [git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules). Currently there are a couple of different ways to run WL. If you have Docker set up, see each "./\_configs" section below, otherwise you'll have to install node, nginx, and the DB to run the full system. There's also a "Help needed!" section at the end of the readme if you're looking for a way to get involved.

**./\_configs/monolith-http**

Everything is built into a single docker image. This is meant to be the simplest set up to give the development of this project a bit of a kick. It'll also hopefully make deployment & running it quit easy.

* [ ] TODO: Figure out how to get it all running on the one container.

**./\_configs/monolith-https**

* [ ] TODO: set up ssl for the single image version of WL

**./\_configs/microservice-http**

* **nginx**: Reverse proxy the API and serves the static FED assets. Until we do an isomorphic version, then that will get split out into it's own container.
* **api**: Currently an all in one express.js server.
* **arango**: The database server, just the arango docker image

* [ ] TODO: Look into splitting out a data volume container
* [ ] TODO: Orcastration with Kubernetes

**./\_configs/microservice-https**

* [ ] TODO: apply ssl to the microservice version


misc  

* [ ] go through and apply these https://github.com/nodejs/docker-node/blob/master/docs/BestPractices.md


---

## Help needed!

**Build WL into a single docker image**: Running the express server, nginx, and ArangoDB is being worked out in ./\_configs/monolith-http. The motivation for creating a single image is to make it as easy as possible for anyone to host their own version.

**Which Graph DB? ArangoDB vs Neo4J vs ?**: we're not graph DB experts but the project is moving in a direction where one will be needed!

**API Architecture**: Feedback / ideas & reasons for a redesign to make the API more extensible / generally better.

**DevOps challenge: setting up Certbot to run with Docker (& possibly Kubernetes)**: We've put ssl on pause for now to get a basic version up and running faster. But it is a 100% must do thing.

**CI integration & testing**: we haven't got any set up yet!

**Install without Docker documentation**: because not everyone will be running Docker.
