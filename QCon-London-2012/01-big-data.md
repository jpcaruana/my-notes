% Big Data - Opening Keynote
% Martin Fowler
% Rebecca Parsons

# Changing nature of data
## Data is growing outside of our control
* Wallmart : 1 million transaction/day
* Facebook : 40 millions photo upload/day
It's a problem for everyone, not just for Google er Amazon

## Data is distributed
98% ot Internet acces in Africa is made on a mobile device

## Data is valuable
US Health $300 millions/year

## Data is urgent
need to respond in real time

## Data is connected
within its ecosystem

# Response to data change
(before -> after)

* 1 huge server -> lots of small boxes
* SQL doesn't work in a cluster -> NoSQL
** Google : BigTable
** Amazon : Dynamo
* NoSQL, Aggregates (from E. Evans' DDD)
** non relational
** open source
** cluster frientdly
** 21st century web
* store aggregates directly, no need to shard -> polyglot persistance
* moving from "Integration DB" to "Application DB"
** one DB/application different than one DB for all applications

# Event sourcing
2 levels of storage :
* in app state
* log
You can rebuild your state with the log.

# Datasources has changed
Now it's text, images, videos, connections.
Analysis will be :
* pattern recognition
* data mining
* chasing connection (via social networks)

This needs different algorithms :
* map-reduce is a very (hard and) different thinking
* visualization data is necessary to understand data

# How do we use data now ?
* data "scientist" -> data journalist
* personalization (see iGoogle)
* data warehouse -> Agile Analitics (Ken Coller)
* crowd sourcing [ushahidicom]
* govs open data
Beware of privacy : protection VS privacy
Developpers have :
* to be careful not to distord information
* the responsability to make accurate connections

