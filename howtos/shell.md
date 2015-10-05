<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [grep](#grep)
  - [grep entre `x` et `y` occurences d'une série de chiffres:](#grep-entre-x-et-y-occurences-dune-s%C3%A9rie-de-chiffres)
- [Splitter une archive trop grosse](#splitter-une-archive-trop-grosse)
  - [Splitter](#splitter)
  - [Remettre ensemble](#remettre-ensemble)
- [Un serveur HTTP en une ligne de shell](#un-serveur-http-en-une-ligne-de-shell)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# grep
## grep entre `x` et `y` occurences d'une série de chiffres:
* échapper les accolades pour le nombres d'occurences
* pas besoin de l'option `-e`

````bash
grep "[0-9]\{x,y\}" file
````

# Splitter une archive trop grosse
d'après http://stackoverflow.com/questions/1120095/split-files-using-tar-gz-zip-or-bzip2


## Splitter 
La limite de taille de fichiers chez Amazon S3 est de 5 Go. Il est agréable parfois de pouvoir envoyer de plus fichiers tgz, mais pour cela il faut faire un split :

````bash
$ fiveGigas=5300000000
$ tar --create --gzip MonDossierVolumineux | split --numeric-suffixes --bytes ${fiveGigas} - fichier.tgz_

$ ls fichier.tgz_*
fichier.tgz_00  fichier.tgz_01  fichier.tgz_02
````

Commande avec les options courtes :

````bash
$ tar cz MonDossierVolumineux | split -d -b ${fiveGigas} - fichier.tgz_
````

## Remettre ensemble 
Options longues :
````bash
cat fichier.tgz_* | tar --extract --gzip
````

Options courtes :
````bash
cat fichier.tgz_* | tar xz
````


# Un serveur HTTP en une ligne de shell
Pratique pour faire un mock HTTP pour pas cher

````bash
$ cat reponse.http
HTTP/1.1 200 OK

hello world

# sur le port 12345 par exemple
$ while [ 1 ]; do cat reponse.http | nc -4Cnl 127.0.0.1 12345; done

$ curl -i http://localhost:12345/
HTTP/1.1 200 OK

hello world
````

Posté sur twitter : https://twitter.com/jpcaruana/status/517350502195949568
