<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Du temps réel au Data Warehouse: capturez et analysez en temps réel vos données](#du-temps-r%C3%A9el-au-data-warehouse-capturez-et-analysez-en-temps-r%C3%A9el-vos-donn%C3%A9es)
  - [Kinesis](#kinesis)
  - [retour d'expérience](#retour-dexp%C3%A9rience)
  - [Texte d'origine](#texte-dorigine)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Du temps réel au Data Warehouse: capturez et analysez en temps réel vos données
    Julien Lépine, AWS Solutions Architect

(arrivé en retard, trés mal placé, orateur très speed)

## Kinesis
* 10 000 000 data/s en écriture
* élastique
* décisions en temps réel
* c'est facile de "tout garder"

Usages :
* real time dashboarding
* machine learning en temps réel

Fonctionnement : des applications (des centaines de milliers) envoient de données. Elle sont stockées en moins de 10s dans 3 availability zones différentes. Ces données sont ordonnées (idéal pour l'analyse de navigation sur un site web par exemple).

C'est très simple d'envoyer des données (1 PUT le fait en moins de 10 lignes de js). Par contre, c'est plus difficile pour lire. Il y a donc une librairie open source pour simplifier l'accès en lecture : https://github.com/awslabs/amazon-kinesis-client

vraiment pas cher d'écrire : 1 000 000 de PUT coûte 0,028$

on peut tout utiliser aver tous les services Amazon (EMR, Elastic Map Reduce) pour traiter les données.

Temps réel et traitement en continu.

## retour d'expérience
bonne pratiques garder toutes les données brutes puis faire plusieurs couches aggrégées selon les usages :

1. global KPI layer : BI
2. reporting layer : rapports standards
3. raw data layer : analyse très fine


## Texte d'origine
Cette session est conçue pour toute personne travaillant sur des plateformes d’analyse de données.

Hadoop a permis aux entreprises de toute taille de travailler efficacement sur de grands volumes de données, démocratisant le Big Data en mode batch.

Leurs besoins évoluent continuellement et les entreprises attendent aujourd’hui une meilleure réactivité des applications, de l’analyse en temps-réel ou encore la possibilité de faire du streaming des données. Amazon Elastic MapReduce a rendu l’utilisation d’Hadoop dans le cloud plus simple et plus accessible. Afin de vous permettre de développer une nouvelle classe d’applications Big Data temps-réel, nous avons lancé Amazon Kinesis, un service qui vous permet d’analyser n’importe quel volume de données en temps réel. Nous proposons aussi Amazon Redshift, une plateforme de data-warehousing massivement parallèle, vous permettant d’opérer des bases de données de plus d’un péta-octet. Nous verrons lors de cette session comment concevoir une architecture avec Amazon Kinesis et Amazon Elastic MapReduce pour créer des applications d’analyse temps réel hautement élastiques traitant des téraoctets de données par heure provenant de centaines de milliers de sources différentes. L’intégration avec Amazon Redshift vous permet de valoriser ces données, de générer des rapports pour toute votre entreprise, de découvrir les données et d’effectuer des analyses poussées à grande échelle et haute performance.
