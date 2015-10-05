<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Oxalide - Apéra Tech #10 : Big Data](#oxalide---ap%C3%A9ra-tech-10--big-data)
  - [Introduction](#introduction)
  - [The paradox of Big Data](#the-paradox-of-big-data)
    - [Histoire de la data](#histoire-de-la-data)
    - [Tendances techniques actuelles](#tendances-techniques-actuelles)
    - [En pratique : quelques Use Case de ses clients](#en-pratique--quelques-use-case-de-ses-clients)
      - [Parkeon](#parkeon)
      - [Chronopost](#chronopost)
      - [Pages Jaunes](#pages-jaunes)
    - [Par où commencer ?](#par-o%C3%B9-commencer-)
  - [Retours d'expérience](#retours-dexp%C3%A9rience)
  - [A retenir](#a-retenir)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

http://www.oxalide.com/2014/12/teaser-video-aperotech-oxalide/

# Oxalide - Apéra Tech #10 : Big Data

synthèse : http://www.oxalide.com/wp-content/uploads/2015/01/Oxalide_Aperotech_BigData.pdf

## Introduction
* a lieu tous les 3 mois
* parle de business, de fonctionnel et de technique
* sujets variés d'une session à une autre

Agenda :

1. [un expert](#user-content-the-paradox-of-big-data) (30')
2. [des retours d'expérience croisés](#user-content-retours-dexpérience) (50')
3. un apéro/buffet

(voir [mes points à retenir](#user-content-a-retenir) / mes remarques perso *en italique*)

## The paradox of Big Data
par Florian Douetteau, http://www.dataiku.com/ (le photoshop du Big Data)

(*un peu trop rapide à mon goût: plus de 60 slides en 30 minutes...*)

### Histoire de la data
Le premier disque dur contenait 4 Mo et le temps d'accès moyen était de 1s. La technologie a énormément évolué depuis (stockage, temps d'accès...) (*euphémisme !*)

En 2008, le terme **Big Data** a été inventé.

* **premier paradoxe** : simple, mais complexe. 
* **second paradoxe** : la perception de soi de la part des data scientists. L'impression d'être presque un dieu, alors qu'en fait passe beaucoup de temps à nettoyer les données puis à attendre l'exécution des jobs
* **troisième paradoxe** : où stocker les données ? Les données valent (potentiellement) des millions, mais elles sont copiées dans plusieurs cloud
* **quatrième paradoxe** : rares sont les personnes qui ont besoin de plus de 8 To (la taille maximale d'un disque dur actuelle) et qui pourtant, parlent de Big Data
* **cinquième paradoxe** : on veut tout automatiser avec du machine learning, mais au final on fait plein de rapports, souvent à la main

### Tendances techniques actuelles
L'offre des solutions est tellement immense que c'est difficile de faire des choix

Le coût des disques dur et de la RAM ont drastiquement chuté ces dernières années. La taille de la RAM a également beaucoup augmenté, à un tel point que ce qui tenait autrefois sur un disque dur peut tenir intégralement en RAM. Cela va favoriser une transition du Map-Reduce du disque dur vers la RAM (ex: Spark) pour des traitements accélérés. En même temps, le volume des données a lui aussi augmenté significativement, mais celui des données utiles moins. (*il va falloir séparer le bon grain de l'ivraie*). Pour environ 10 To de données brutes, seulement 1 To sont en fait utiles.

Il existe un fort écosystème dans le monde de l'open source, avec de nombreux acteurs importants issus de la Sillicon Valley (avec force de moyens, levées de fonds) qui investissent massivement pour améliorer ces outils. On peut noter en particulier :

* [graphlabs](http://graphlab.com) qui propose un outil de machine learning
* [databricks](https://databricks.com/) qui a créé Spark

[Spark](https://spark.apache.org/) est **la** grosse tendance du moment. Il se décompose un plusieurs composants principaux :

* [Spark SQL](https://spark.apache.org/sql/)  (anciennement shark) : queries en temps réel
* [MLlib](https://spark.apache.org/mllib/) : machine learning en mémoire
* [Steaming](https://spark.apache.org/streaming/) : mises à jour des données en temps réel

![stack spark](https://spark.apache.org/images/spark-stack.png "stack spark")

On note enfin l'arrivée d'équipes orientées "exploitation des données" dont le travail consiste en :

* croiser les données
* faire des outils de reporting
* aider à la prise de décision (stratégique)

### En pratique : quelques Use Case de ses clients
#### Parkeon

Le leader mondial des horodateurs connectés : plus de 400 000 objets connectés de part le monde.

Veulent faire évoluer leur business model pour aider à trouver des places de parkings, selon l'heure et le lieu. Pour cela, ils ont utilisé leur 10 années de données sur les tickets de parkings afin de prédire les places libres.

**Valoriser ses données pour en faire un avantage compétitif.**

#### Chronopost
Chronopost posséde beaucoup de données issues de son historique dans la logistique. L'objectif est de résoudre et d'optimiser le problème du "dernier kilomètre". Avec ces données (saisonalité, adresses professionnelles/personelles), Chronopost est maintenant capable d'estimer au plus juste (et d'optimiser) le coût d'une livraison à un moment donné, à un endroit donné.

#### Pages Jaunes
Mise en place d'un monitoring métier de la performance de leur moteur dans le temps, en particulier dans le passé.

### Par où commencer ?
1. Apprendre
    * python/scikit/pandas
    * R
    * scala
2. Pratiquer
    * participer à un concours en ligne, sur [kaggle](http://www.kaggle.com/) ou sur [datascience.net](https://datascience.net/fr/home/)
    * participer à l'un des nombreux meetups (graphDB, machine learners...)

Un **modèle** est un système automatisé qui permet de prendre des décisions (usr une grande variété de sujets).


## Retours d'expérience
Personnes présentes :

* Jean Noël Rivasseau, CTO et fondateur de [Kameleoon](http://www.kameleoon.com) http://blog.kameleoon.com/kameleoon-present-laperotech-oxalide-big-data/
* [Vente Privée](vente-privee.com)
* [LinkFluence](http://linkfluence.com/)
* Gaelle de [Blablacar](http://www.covoiturage.fr/)
* AXA

**Quel a été le déclencheur pour une démanche Big Data ?**

* **Blablacar** existe depuis 2009 et fait du Big Data depuis 2013. Le premier objectif était de répondre à la question "peut-on aller ailleurs qu'en France ?" pour développer l'entreprise. Maintenant, le but est de donner ces données à différentes entités de l'entreprise
* **Vente privée** a depuis le début de gros volumes de données mais de nombreux confits organisationnels, par exemple entre le marketing et la technique
* **Kameleoon** veut transitionner son modèle de l'AB Testing vers de la personalisation dynamique et a besoin pour cela de beaucoup de données structurées, de récolter de nombreuses données pour les réutiliser
* **LinkFluence** a vu le volume de données à l'arrivée des réseaux sociaux exploser par rapport à son modèle précédent 100% web. Les recettes qui s'appliquaient au monde du web ne fonctionnaient plus avec les réseaux sociaux

**Quelle technologie utilisez-vous ?**

* **LinkFluence** : [Storm](https://storm.apache.org/) est sorti en 2011. Cela a permi de pouvoir traiter plus de données plus vite en ajoutant des serveurs. Continuent la veille technologique sur ce qui se passe aux USA, regarde comment font les "gros"
* **Kameleoon** a fait de nombreux essais, essuyé de nombreux plâtres. Ont choisi Cassandra + Elastic Search. Pour 2015, enviseage sérieusement de passer à une [lambda-architecture](http://lambda-architecture.net/)
* **Vente privée** fait du big date structuré pour le reporting. SE posent encore des questions  : Hadoop ? Cloud/Hybride ? Quid de la sécurité ?
* **Blablacar** utilise 2 flux :
    * flux temps réel : Flume > Hadoop > Pig > Vertica
    * flux pour data scientists : Dataiku > Vertica
* **AXA** hérite d'une infrastructure IT historique (classique pour les banques, assurances et télécom) de type mainframe/gros SQL. Pour éviter de tout casser, utilisation d'une approche "en parallèle" avec création d'un "data lake" avec Hadoop/Spark et MongoDB/ElasticSearch

**Est-ce que c'est en prod ?**

* **Blablacar** fait tout en prod. Les résultats sont utilisés par tous (marketting, community managers...)
* **Kameleoon** : cela reste (pour le moment) cantonné au département R&D. Pour leur métier, le marché a évolué d'une utilisation de Google Analytics vers une demande forte de la part des clients pour un produit maison. Ont commencé par un reporting interne qui a été un peu difficile à mettre en place. Ont observé des bugs à chaque changement d'échelle du volume de leurs données
* **Vente privée** : pas vraiment en prod. courant 2015
* **LinkFluence** (*c'est un peu leur coeur de métier*) Big data en prod **et** sur le chemin critique

**Quel volume de données actuellement ?**

* **LinkFluence** : environ 50 To (20 milliards de documents depuis 2008)
* **Kameleoon** : 1 To actuellement, entre 10-15 To en 2015 (*grosse accélération*)
* **Blablacar** : 1 an de leurs données équivaut à 700 Go, mais le volume des données par année augment énormément. 1 millions de nouveaux membres par mois (*j'ai bien compris ??? ça me semble énorme*). Récupèrent leur legacy-data (5 années) au fur et à mesure

**Comment alimente-t-on son data warehouse ?**

* **Vente privée** est constituée de nombreux silos. la difficulté est de prondre la légitimité pour aller chercher les données existantes. Chaque silo est traité un par un.
* **AXA** : idem Wente Privée (silos...). Est rattaché au plus haut de la hiérarchie, qui ne s'occupe pas que de l'IT ou que du marketting : être le plus transverse possible pour être légitime. Stockent la donnée brute et l'exploitent ensuite

**Comment constituer son équipe Big Data ?**

* **Blablacar** ne recherche pas de profil spécifique, mais des gens qui ont envie. Actuellement, l'équipe = 2 anciens dev + des architectes (pour les serveurs) + des analystes métier
* **Vente privée**
    1. rapprocher les expertises BI dans une même équipe
    2. équipe data science = esprits curieux, un peu geek, avec une grosse sensibilité business et capables de fonctionner en mode "chef de projet" pour mener un projet data jusqu'au bout (*ça fait rêver*)
* **LinkFluence** : des ingénieurs curieux, avec de solides bases en maths et en informatique théorique

**C'est quoi un Data Scientist ?** (*bonne question !*)

* informaticien / matheux
* comprend le business (*peut difficilement être un 100% junior alors*)
* fait du code
* parle au marketting
* est capable de faire des modèles (complexes), de comprendre le machine learning
* une équipe big data, c'est comme un bon quartet de jazz (ie. des compétences variées qui travaillent ensemble)

**Quels sont les freins rencontrés pour traiter la data ?**

* **Kameleoon** : difficile de recruter des Data Scientists, mais encore plus difficile : trouver un Big Data architecte. Il y a en France trés peu d'expérience en Big Data ; c'est à la limite de la R&D dans notre pays. C'est tellement récent que le seul livre parlant de lamdba-architecture est à ce jour en pre-release !
* **Vente privée** : difficile d'accéder aux données à cause des silos (*décidément ils me font rêver*) + le big data n'est pas la priorité opérationnelle du moment
* **LinkFluence** : il faut se donner le temps de faire des essais. Attention aux effets de seuil (de volume). N'ont pas toujours le temps de tout développer
* **Blablacar** n'a pas le temps de tout développer. Difficile de trouver les duplications dans les demandes des différents services
* **AXA** : il existe des freins légaux aux données qu'on peut utiliser. En outre, ces freins sont différents selon les pays concernés ! Les données sont très fractionnées et leur qualité est très variable (données créées pour des anciens SI orientés adminitratif)

**C'est quoi la prochaine étape ?**

*  **AXA** : 2 axes :
    * améliorer la productivité des data scientists (par l'automatisation)
    * mettre toutes ces données à disposition 
* **Blablacar** : plus de machine learning (pour ajouter un moteur de recommandations des trajets)
* **LinkFluence** : 
    - migrer chez AWS pour absorber la charge et baisser les coûts
    - essayer d'autres technos (sont sur Spark depuis 2 semaines seulement)
* **Vente privée**
    - centraliser plus de données
    - transformer les architectes en big data architectes 
* **Kameleoon** 
    - prouver la valeur de leur solution
    - faire beaucoup de machine learning (pour déterminer des segments d'utilisateurs et leur proposer des coupons de réductions ciblés)
    - tous leurs outils sont prêts, mais pas le marché français (ce sera ok pour fin 2015)

**Comment se lancer dans une démarche Big Data ?**

* ne pas avoir peur d'essayer, de casser des choses. "embrace failure"
* ne pas passer trop de temps en études mais plutôt faire des POCs
* ne pas trop écouter les très très très très gros du marché (Google, Facebook, Twitter...) qui ont quand même d'autres problèmes à adresser que la plupart des autres entreprises. Il faut se concentrer sur son Use Case pour avoir des résultats très rapidement (*et itérer*)
* fail / learn / succeed
* s'amuser
* commencer petit, résoudre d'abord **un** problème, puis les autres à la suite


## A retenir
À retenir et/où à suivre (oui, ici c'est la bazar) :

* pertinence de [Spark](https://spark.apache.org/) qui gagne un immense *momentum*
* regarder ce que c'est : [lambda-architecture](http://lambda-architecture.net/)
    * définition rapide et orale : précalculer par block le résultat des requêtes puis combiner le résultat des blocks
* pas mal d'utilisations de [Vertica](http://www.vertica.com/) qui est payant, même dans les startups
* le changement d'échelle (du volume de données) peut tout remettre en question. C'est en outre difficile (impossible ?) à anticiper quand on débute
* data lake, le buzzword du buzzword big data
* les data scientists : le nouveau mouton à 5 pattes que tout le monde recherche. Je pense que ça ne peut être que des profils expérimentés (pas que dans Big Data, au contraire) et pourtant je ne rencontre que des jeunes qui sortent de l'école. Un autre paradoxe ?
* avant il y avait l'architecte, l'urbaniste, maintenant il y a le "Big Data architecte". Big data entraine la création de nombreux nouveaux métiers, mais sont-ils tous si différents de leurs prédécesseurs (arch/big data archi)
