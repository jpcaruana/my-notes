Meetup Docker Paris http://www.meetup.com/Docker-Paris/ http://www.meetup.com/Docker-Paris/events/168190122/

# Docker / SDN / aspcets réseau
    par octo

## Docker
* le réseau = un bridge docker0 monté automatiquement en local
* pas d'isolation entre les conteneurs : tous partagent la meme IP
* il faut publier les ports (typiquement dans le Dockerfile) pour les rendre disponibles en local pour les autres conteneurs
* link des différents conteneurs entre eux, en général par variable d'environnement. Permenntre par exemple à un tomcat de parler à un MySQL
* NAT-PAT pour exposer un port extérieur

## SDN (Software Defined Network
* modèle physique différent du modèle logique : on aimerait pouvoir gérer dynamiquement l'ajout la suppression de réseaux étanches entre eux. Les équipes réseau n'ont pas cette culture.
* avec les VLAN, on a une limite de 2048 réseaux qui est trop basse pour le cloud

SDN:
* massivement multi tenant
* infra as code
* API centric
* infra/vendor agnostique

décorelle les cycles de vie entre l'infrastructure physique et les tenants.

###SDN
* réseaux abstraits (en cours)
* API standardisée : openflow (http://en.wikipedia.org/wiki/OpenFlow) le "cisco killer"
* gestion centralisée

C'est le meme paradigm shift pour les ingés réseau que devops pour les ingés système (mais en pire car au réseau ils partent de plus loin)

Vue du host (hyperviseur ou serveurs accueillant les docker):
* héberger des bridges
* gérer les ACL pour les flux
* mapper les bridges vers le monde extérieur

Vue du réseau:
* utiliser des réseaux de niveau 2 pour faire l'interconnexion
* utiliser des VLAN pour tagguer les flux des différents bridges
* encapsuler le niveau 2 dans du niveau 3 avec des VPLS

on a toujours la limite de 2048 réseaux

### Perspective fullmesh
On tire des tunnels :
* niveau 3
* on ne parle plus de VLAN

* attention au broadcast
* chute du MTU à cause de l'encapsulation niveau 3
 *voir OpenStack Neutron : https://wiki.openstack.org/wiki/Neutron "Neutron is an OpenStack project to provide "networking as a service" between interface devices (e.g., vNICs) managed by other Openstack services (e.g., nova)."
* nécessité d'avoir des routeurs SDN sur les machines physiques

## Docker + SDN
* supprimer le bride de docker (option n=false)
    * trop simpliste
    * un seul par host
* ne pas attacher les conteneurs au bridge
* créer des nouveaux bridges avec openvswitch (http://openvswitch.org/)
* pipework.sh (https://github.com/AnalogJ/depot/tree/master/pipework) pour lier les conteneurs ensemble

Ainsi on est limité à 2^24 ou 2^32 sous réseaux, ce qui laisse le temps de voir venir

# Retour d'expérience de chez Mention : créer des environnements de développement réplicables
http://fr.slideshare.net/arnaudbreton/build-replicable-environments-docker-paris-031314

* un 1er essai avec Vagrant
    * "comme" docker
    * avec l'overhead de la VM
* utilisation des Dockerfile pour avoir un build répétable
    * peut etre long dans certains cas
* 1 conteneur avec toute la stack ou un conteneur par élément ?
    * choix de un seul conteneur (pour le moment) :
        * plus simple
        * utilisé que en dev et dans jenkins
        * difficile d'orchestrer proprement le démarrage des docker pour que ça marche
* utiliser des data contener pour séparer l'applicatif des données

flux RSS sur docker : http://bit.ly/mention-docker

# What’s up in the Docker ecosystem ?
voir https://docs.google.com/presentation/d/1P6y6WdgZwfrG5dZELTgtAPbOUNoPiKy4ib2mquRScTI/edit#slide=id.p

à retenir :
* Flynn (https://flynn.io/) : Heroku-like full docker. Flynn simplifies deploying and maintaining applications. Instead of using complex configuration management systems, Flynn allows self-serve management of containerized deployments, making life easier for ops and developers.
* Fig (http://orchardup.github.io/fig/) : Fast, isolated development environments using Docker. (lier les docker entre eux)
* drone.io (https://drone.io/ et https://github.com/drone/drone) : Continuous Integration platform built on Docker
* http://ctl-c.io/ IaaS + Docker
* http://www.centurylinklabs.com/ : foule de liens sur Docker
