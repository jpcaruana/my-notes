http://www.oxalide.com/2014/12/teaser-video-aperotech-oxalide/

# Oxalide - Apéra Tech #10 : Big Data

## Introduction
* a lieu tous les 3 mois
* parle de business, de fonctionnel et de technique
* sujets variés d'une session à une autre

Agenda :

1. [un expert](#user-content-the-paradox-of-big-data) (30')
2. [des retours d'expérience croisés](#user-content-retours-d-experience) (50')
3. un apéro/buffet

## The paradox of Big Data
par Florian Douetteau, http://www.dataiku.com/ (le phonoshop du Big Data)

### Histoire de la data
Le premier disque dur contenait 4 Mo et le temps d'accès moyen était de 1s. La technologie a énormément évolué (stockage, temps d'accès...)

En 2008, le terme **Big Data** a été inventé.

* **premier paradoxe** : simple, mais complexe. 
* **second paradoxe** : la perception de soi de la part des data scientists. L'impression d'être presque un dieu, alors qu'en fait passe beaucoup de temps à nettoyer les données puis à attendre l'exécution des jobs
* **troisième paradoxe** : où stocker les données ? Les données vaut (potentiellement) des millions, mais elle est copiée dans plusieurs cloud
* **quatrième paradoxe** : rares sont les personnes qui ont besoin de plus de 8 To (la taille maximale d'un disque dur actuelle)
* **cinquième paradoxe** : on veut tout automatiser avec du machine learning, mais au final on fait plein de rapports, souvent à la main

### Tendances techniques actuelles
L'offre des solutions est tellement immense que c'est difficile de faire des choix

Le coût des disques dur et de la RAM ont drastiquement chuté ces dernières années. La taille de la RAM a également beaucoup augmenté, à un tel point que ce qui tenait autrefois sur un disque dur peut tenir intégralement e RAM. Cela va favoriser un transition du Map-Reduce du disque dur vers la RAM (ex: Spark) pour des traitements accélérés. En même temps, le volume des données a lui aussi augmenté significativement, mail celui des données utiles moins. (il va falloir séparer le bon grain de l'ivraie). Pour enviran 10 To de données brutes, seulement 1 To sont en fait utiles.

Il existe un fort écosystème dans le monde de l'open sourec, avec de nombreux acteurs importants issus de la Sillicon Valley (avec force de moyens, levées de fonds) qui investissent massivement pour améliorer ces outils. On peut noter en particulier :

* (graphlabs)[http://graphlab.com] propose un outil de machine learning
* (databricks)[https://databricks.com/] a créé Spark

(Spark)[https://spark.apache.org/] est **la** grosse tendance du moment. Il se décompose un plusieurs composants principaux :

* (Spark SQL)[https://spark.apache.org/sql/]  (anciennement shark) : queries en temps réel
* (MLlib)[https://spark.apache.org/mllib/] : machine learning en mémoire
* (Steaming)[https://spark.apache.org/streaming/] : mises à jour des données en temps réel

https://spark.apache.org/images/spark-stack.png

On note enfin l'arrivée d'équipes orientées "exploitation des données" dont le travail consiste en :

* croiser les données
* faire des outils de reporting
* aider à la prise de décision (stratégique)

### En pratique : quelques Use Case de ses clients
#### Parkeon

Le leader mondial des horodateurs connectés : plus de 400 000 objets connectés de part le monde.

Veulent faire évoluer leur business model pour aider à trouver des places de parkings, selon l'heure et le lieu. Pour cela, ils ont utilisé leur 10 années de données sur les tickets de parkings ain de prédire les places libres.

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
    * participer à un concours en ligne, sur (kaggle)[http://www.kaggle.com/] ou sur (datascience.net)[https://datascience.net/fr/home/]
    * participer à l'un des nombreux meetups (graphDB, machine learners...)

Un **modèle** est un système automatisé qui permet de prendre des décisions (usr une grande variété de sujets).


## Retours d'expérience
TODO
