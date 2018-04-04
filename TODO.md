## High priority

* Figure out data persistance
  * [x] data volumes set up
  * [ ] periodic backup service (in another container that speaks to arango?)
    * arangodump `unix> arangodump --server.database "wl-dev-db" --server.password "password" --output-directory "dump-yyyymmdd"`
      * will fail if the defined dump directory exists
      * when finished it prints out a summary line (TODO: log this!)
    * arangorestore
* Move all the Docker things into the infastructure repo and out the API / react-app repos

**CI/CD**

Push to API repo to kick off:  
 - something that runs a docker DB container then also the API
 - runs the API tests
 - marks if it passes or fails in the API repo

Push to the react-app repo to kick off:
 - something that runs a DB container, the API container, and the react-app container
 - runs the front end tests (todo!) regression / a11y
 - marks if it passes or fails in the react-app repo

(advanced!)  
A successfull test on the API or react-app repo master branches kicks off:
 - something that builds all the containers in the infastructure repo
 - runs end to end tests / performance tests
 - marks if it passes or fails
 
ALTERNATE IDEA
Push to API or react-app repos kicks off a full build in the infastructure repo...

## Medium

* Add auth to the db through (dynamic?) environment variables
* Tidy up the API server.
* Build the docker image through a service with incremental versioning (semantic)
* look at the user system - can it be built as a seperate service and handle auth checking?
* https://youtu.be/j-0Bj40juMI?t=899 CSP additions!
* Set up a Neo4J container again (possibly even other db types!)
  * send data to both Neo & Arango
  * monitor and compare performance

## Low

* golden layout UI? - create an editing mode of WL with that screen thing? For each service :P
* Build WL into one single docker image. (will split up later).

  * Get arangodb installed & running
  * Get the API talking to ArangoDB
  
* Set up a release checklist, eg here's the react one: https://github.com/facebook/react/issues/10620
* I18n repo...?
