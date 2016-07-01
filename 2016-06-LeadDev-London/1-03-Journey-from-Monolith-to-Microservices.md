# Journey from Monolith to Microservices 

    Mike Gehard
    slides: https://github.com/mikegehard/journeyFromMonolithToMicroservicesSlides/tree/leadDev

see http://www.appcontinuum.io/

Which comes first ? The monolith of the microservices ? -> get started with **domain bounded context** (SOA was without domain bounded context).

## 1. write (API level) tests
- don't break client behaviour
- high level tests that reflect reality
- use Pact (https://github.com/realestate-com-au/pact) to write contract in json and generate clients ( Enables consumer driven contract testing, providing a mock service and DSL for the consumer project, and interaction playback and verification for the service provider project)

## 2. arrange appliction so you can SEE your domain
(Uncle Bob, drill down)

- less costly to evolve and experiment boundaries
- delay architecture decisions, always

## 3. Break out components

- give me more space in code
- solidify dependancies ans boundaries
- DB: migration just touch ONE table, in order to be able to separate data later on

Cost must be > to benefits before moving on

## 4. promote your first microservice

- scale a bounded context
- reuse
- many other reasons

But it comes with additional costs: 

- **service discovery**: new application with 0 business value. Increases flexibility
- **circuit breaker**: new application with 0 business value, too. The "maybe monad" in a distributed system. Increases resilience and the visibility of systems.

## 5. Next steps

- breakup more microservices
- change communication interface (with a queue system)
- don't do anything more: it is up to you
