<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breaking the monolith](#breaking-the-monolith)
  - [Systems characteristics](#systems-characteristics)
  - [Rules and guidelines](#rules-and-guidelines)
  - [How to integrate systems ?](#how-to-integrate-systems-)
  - [Summary](#summary)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breaking the monolith
    Stefan Tilkov
    Track: Architectures evolution

(enterprisy stuff)

3 layer architecture means nothing
* UI is not always helpful
* easy: don't have to think

System boundaries
* 1 project == 1 system ? this is the worse approach
* architecture design is different from arbitrary system boundaries

Modularization and size
* SLOC grows when number of modules grows
* there's a size limit to one application : split between different applications

## Systems characteristics
* separate / redundant persistence
* internal separated logic
* domain model : implies strategies
* separated UI
* separate evolution
* autonomous operations
* limited interractions with other systems

Separate between different kind of architectures

Micro architecture (internal) VS Macro architecture (different systems)

Choice of different technologies leads to chaos ?

## Rules and guidelines
Cross systems : decisions stuck with for a decade
* responsabilities
* UI integration
* communication protocols
* data format
* logging, monitoring

Systems internals : will change in the future
* programmation languages
* dev tools
* frameworks
* process / workflow contros
* design patterns
* code guidelines

Don't mix these two levels.

Objectives change over time : change decisions, separated systems.

Overtime, first :
* ease of development
* homogeneity
* cohesion
* simplicity

then
* modularity
* decoupling
* (support for) henerogeneity
* autonomy

It's hard to convince people to do things "first" at the begining of the project (not right first time).

## How to integrate systems ?
Data integration VS data replication : why is it good for me ?
Each application comes with its database but there are dependancies between databases : data copy. Think of event notification

## Summary
* think about the systems that make up your system
* separate macro/micro architectures
* address UI integration and SSO
