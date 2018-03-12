## High priority

* Figure out data persistance
  * [x] data volumes set up
  * [ ] periodic backup service (in another container that speaks to arango?)
    * arangodump `unix> arangodump --server.database "wl-dev-db" --server.password "password" --output-directory "dump-yyyymmdd"`
      * will fail if the defined dump directory exists
      * when finished it prints out a summary line (TODO: log this!)
    * arangorestore
* Deploy without https.

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
