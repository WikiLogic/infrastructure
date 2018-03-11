# Wikilogic Architecture

## Docker

Chosen because:

* It gives developers the ability to run WL cross platform
* It allows WL to easily take advantage of Kubernetes which appears to be turning into the industry standard
* It detangles service technology and will allow service specific teams

## ArangoDB Vs Neo4J

* Originally built with Neo4J
* Memory problems on the cheaper servers led to the switch to Arango
* Still needs research and a possible switch back to Neo / a more industry standard Graph DB

## Node & Express JS

* Chosen because the original developer (me!) only knew JS in enough depth to make a viable API
* It's popularity gives a wider talent pool from which interested parties may emerge

## Nginx

* Chosen for it's performance
* Popularity == better online documentation, more examples, and easier access to help

## React & MobX

* Chosen for it's ability to cleanly handle complex UI and client side state managment
* Growing popularity of React == bigger talent pool.
