# High availability at Heroku
    Mark Mebranaghan
    Track: High available systems

## Architecture
Lots of load balancing.

Embrace crashing and enabling supervision (like erlang):
* distributed supervision
* crashes as code paths
* crashes as hot code paths (exercised a lot)
* keep smaller and smaller kernel : keeps it simple

Message passing (json format). Handle different versions of messages.

Continuously running.

It's a distributed system with granular failure.

Brokered queueing (producer/consumer pattern) :
* RabbitMQ used for a while
* the broker node is a SPOF : publish to one, subscribe to all
* several brokers : load balanced publish to one, all subscribers subscribed to all brokers

Read call-graph partial failure : graceful termination.

Write call-graph de-synchronization : write a ticket (to a local database) to delay write operations when not available.

## Execution (eveything outside architecture)
Evolving socio-technical ecosystems. Most of the problems are :
* failed deploy
* bad visibility
* cascading feedback

Need for a very *repeatable* deploy :
* incremental deploys : deploy to a few nodes and incresing deploy perimeter when confidence grows
* incremental rollouts (features) : feature flags for dev, beta users then all users
* real time visibility : dashboards (60s visibility)
* service level assertions : asserts in code, global level for a service. Assert good things too

Flow control and back pressure : some systems can't absorb all load :
* divert traffic from this system 
* limit message passing (parameters on a file system like /etc/rate/publish)
