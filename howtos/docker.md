<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Générer une image des dépendances entre les images](#g%C3%A9n%C3%A9rer-une-image-des-d%C3%A9pendances-entre-les-images)
- [Installer son propre registry docker sur Google Cloud avec stockage sur Google Cloud Storage](#installer-son-propre-registry-docker-sur-google-cloud-avec-stockage-sur-google-cloud-storage)
  - [Créer un bucket dédié](#cr%C3%A9er-un-bucket-d%C3%A9di%C3%A9)
  - [Créer une instance de VM](#cr%C3%A9er-une-instance-de-vm)
- [lancer le registry](#lancer-le-registry)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# Générer une image des dépendances entre les images
````bash
docker images -viz | dot -Tpng -o docker.png
````

# Installer son propre registry docker sur Google Cloud avec stockage sur Google Cloud Storage

(une fois qu'on a un compte Google Cloud)

## Créer un bucket dédié

Depuis l'IHM, par exemple `mon_docker` (car le nom de bucket `docker` est interdit/déja pris)

## Créer une instance de VM

On utilise l'image de base de Google pour jouer avec Docker. Il est pré-installé avec Kubernetes

````bash
gcloud compute instances create dockerregistry \
 --image container-vm-v20140929 \
 --image-project google-containers \
 --zone europe-west1-b \
 --machine-type f1-micro
 ````

## Installer Registry
Premièrement, il faut générer un "refresh token" pour pouvoir lire/écrire dans le bucket désiré (bien garder cette string de côté. On l'appellera _your-refresh-token_ dans la suite) :

````bash
gcloud auth print-refresh-token
````

Il faut se logguer sur le serveur

````bash
gcloud compute ssh --zone europe-west1-b dockerregistry
````

Ensuite

Créer le fichier `/var/registry-params.env` (avec sudo) avec le contenu suivant :

````
GCP_OAUTH2_REFRESH_TOKEN=your-refresh-token
GCS_BUCKET=mon_docker
````

````bash
sudo docker pull google/docker-registry   # ça prend un peu de temps...

# lancer le registry
sudo docker run -d --env-file=/var/registry-params.env -p 80:5000 -e STORAGE_PATH=/containers google/docker-registry
````

Bien penser à ouvrir le traffic HTTP pour ce serveur.

A noter : voici les containers qui tournent :

````bash
$ sudo docker ps
CONTAINER ID        IMAGE                           COMMAND               CREATED             STATUS              PORTS                    NAMES
31dfe86363e4        google/docker-registry:latest   "./run.sh"            30 minutes ago      Up 30 minutes       0.0.0.0:80->5000/tcp     mad_poincare
adbc655fec5a        google/cadvisor:latest          "/usr/bin/cadvisor"   43 minutes ago      Up 43 minutes                                k8s--cadvisor.1207d44b--cadvisor_-_agent.file--64870a67
2615e6c34dba        kubernetes/pause:latest         "/pause"              43 minutes ago      Up 43 minutes       0.0.0.0:4194->8080/tcp   k8s--net.46426d55--cadvisor_-_agent.file--04e2edda
````

## Pusher une image

````bash
docker tag groupe/image mon-ip:80/groupe/image
docker push mon-ip:80/groupe/image   # là aussi ça prend un peu de temps...
````

Ensuite, on constate bien que le registry est créé :

````bash
$ gsutil ls gs://mon_docker/containers
gs://mon_docker/containers/images/
gs://mon_docker/containers/repositories/
````

On peut couper la VM pendant qu'on ne s'en sert pas et le registry est toujours présent/persistent.

## Liens
* https://registry.hub.docker.com/u/google/docker-registry/
* http://docs.docker.com/installation/google/
* https://cloud.google.com/compute/docs/containers/container_vms
* http://docs.docker.com/userguide/dockerrepos/#pushing-a-repository-to-docker-hub
