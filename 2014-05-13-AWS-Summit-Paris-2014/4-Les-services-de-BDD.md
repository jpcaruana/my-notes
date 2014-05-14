# Votre deuxième semaine avec AWS : services de bases de données
    David De Santiago, AWS Business Development Manager (sous coke)

## Pourquoi un base de données en mode hébergé ?
Quand on héberge soi-même ses données, il faut penser à tout :
* la haute dispo
* les sauvegardes
* la réplication
* les patchs applicatifs (montée de version de la BDD)
* les mises à jour d'OS...

Tout ce temps n'est pas consacré à apporter de la valeur à vos clients.


Deux choix possibles avec AWS :

1. installer sa BDD sur des instances EC2
2. en mode managé : il ne reste plus qu'a écrire le logiciel qui apporte de la valeur aux clients

Les différents cas d'usage couverts pas AWS :
* Amazon RDS pour le SQL
* Amazon DynamoDB pour le NoSQL en mode clef/valeur
* Amazon ElastiCache pour le cache en mémoire (memcached ou redis)
* Amazon Redshift pour le data warehouse et l'OLAP

## Amazon RDS: Relational Database Service
* simple et rapide à régler
* au choix : MySQL, PostgreSQL, Oracle ou SQLServer
* amazon gère les patches, la sauvegarde, la réplication
* simple et rapide à redimentionner

Possibilité d'utiliser les backup pour tester le nouveau code dans un autre environnement

Choix des machines: CPU, RAM, stockage iOPS. Possibilité de migrer le hardware des instances en live sans interruption de service.

Sauvegardes :
* automatiques et conservées 35 jours (sans aucun coût)
* manuelles (simple clic ou API) conservées dans S3

Option multi-AZ (availibility zones):
*  meilleure disponibilité
* meilleure durabilité

Impossible de bouger les données entre les régions. Par contre, on peut copier les snapshot avec S3

Avec MySQL, il est possible de créer autant de Read Replicat pour scaler en lecture. (en 1 click au lieu de plus de 150 commandes pour le faire soi-même). Un Read Replicat peut être inter-région et peut devenir master.

## Amazon DynamoDB
BDD clef/valeur, schémaless. Inventée avant le terme "NoSQL"

BDD réglable à l'infini (des millions d'iOPS)

Se requête par hash key / range key / LSI (Local Secondary Index) key et GSI (Global Secondary Index) key.

Capacité réglable en unités iOPS
* 1 ko/s en écriture
* 4 ko/s en lecture (en mode eventually consistent)

BDD optimisée pour les développeurs

Possibilité d'utiliser le client AWS JS pour parler directement à DynamoDB sans passer par un serveur.

## Amazon Redshift
* Data Warehouse relationnel et opéré
* BDD en mode colonne 10 fois plus rapide que les DBB traditionnelles.
* Pout stocker jusqu'à 1,6 To de données compressées
* Prix très attractif : 1000 $/an/To (si on réserve sur 3 ans) ou 3400 $/an/To quand on paye à la demande.
* Utilisé par exemple par Foursquare, Nokia, the Financial Times.

Cas d'usages :
* Data Warehouse à très faible coût
* Big data : analyse à grande échelle, reporting
* Saas : analytique "temps réel"

Peut être utilisé avec des outils de BI classiques.

Peut être chargé à partir de fichiers CSV depuis S3 mais aussi a partir de DynamoDB.

Le stockage en colonnes permet :
* la compression des données
* le zonage des données (sharding)
* le stockage des données (HDD ou SSD)

## Texte d'origine
Cette session est recommandée pour ceux qui veulent avoir une vue d’ensemble sur les différents services de base de données offerts par AWS.

AWS offre à ses clients un large choix de base de données. Cela inclut Amazon DynamoDB, un service de base de données NoSQL entièrement géré qui rend simple et économique le stockage et la récupération des données; Amazon Relational Database Service (RDS), un service qui permet de configurer, exploiter et dimensionner simplement une base de données relationnelle dans le cloud avec le support des bases de données MySQL, Microsoft SQL Server, PostgreSQL, et Oracle. Dans cette session, vous aurez un aperçu des différentes options des bases de données proposées par AWS; vous découvrirez comment celles-ci peuvent vous aider à supporter vos applications et vous verrez comment démarrer.
