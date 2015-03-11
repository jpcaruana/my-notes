http://www.parisjug.org/xwiki/bin/view/Meeting/20150310

#Paris JUG: Soirée RxJava et Kafka

## RxJava
    Hugo Cordier, CTO Melusyn - @HugoCrd
    http://www.parisjug.org/xwiki/bin/view/Speaker/HugoCordier
    https://github.com/Melusyn/ReactiveX-examples

### Promesse de la session
RxJava permet de développer sur la JVM des applications orientées évènements. Cette librairie permet de composer des flux de données de manière simple sans bloquer et sans se soucier de la gestion des threads.

Nous utilisons Rx chaque jour chez Melusyn depuis plus d'un an, en Java et en Groovy. Le but de cette présentation est d'expliquer les concepts des Reactive Extensions, et de montrer en quoi RxJava permet de développer simplement des applications asynchrones sur la JVM. 

### Callback et Futures
En java, il existe 2 façons de faire de l'asynchrone. Elles ont chacune leurs limites :

- callbacks sont totalement illisibles (et donc inutilisables)
- Futures (en particulier les CompletableFutures de java 8) sont chaînables, mais elles ne peuvent retourner qu'une seule valeur et il y est difficile d'y gérer le temps (time outs). En outre, il y a de la gestion de Thread à faire à la main (*Rq: c'est pas vrai*)

### Origine
Erik Meyer a sorti Rx.Net (pour la plateforme Microsoft .Net) en 2012.

NetFlix s'en est très largement inspiré pour sortir en 2013 RxJava.

### Observable
Un Observable est un peu comme une Future mais itérable : elle renvoit en fait un stream d'événements asynchrones.

Un Observable peut envoyer :

- entre 0 et une infinité d'événements
- 1 erreur
- une fin de strean

L'Observable est responsable de savoir où va tourner son code : il est mono threadé par défaut.

### Souscrire à un observable
Il y a 3 methodes pour réagir au événements une fois qu'on a souscrit :

- *onNext*
- *onError*
- onCo*mpleted (peu utilisé)

### Transformer les données avec les opérateurs
Un Opérateur prend en argument un Observable et retourne un Observable. C'est une fonction de transformation

Exemples: 

- *filter*
- *merge* permet de mélanger 2 flux asynchrones de *même* type pour retourner un nouveau flux
- *zip* permet de mélanger 2 flux asynchrones de types *différents* pour retourner un nouveau flux (d'un potentiel 3ème type)
- *flatMap* est équivalent à un *map* suivi d'un *merge*. pratique pour remettre à plat les flux imbriqués

démo : utilisation de swapi.co (Star Wars API) pour aller chercher en asynchrone tous les personnages, leur race et leur planète d'origine des épisodes 4 et 5.  Voir [le code sur github](https://github.com/Melusyn/ReactiveX-examples/blob/master/src/4.%20Async/C_combining.groovy)

### Gestion des erreurs
Toute erreur est "catchée" et envoyée dans le handleError. Par défaut, une erreur arrête immédiatement l'Observable.

Il existe des méthodes pour réagir sur ces erreurs : 

- *onErrorReturn*: retourne une valeur prédéfinie et s'arrête
- *onErrorResumeNext* : permet d'utiliser un nouveau flux de données

### Hot and cold
Une question se pose : à partir de quel moment un Observable va-t-il commencer à émettre des données ?

Par défaut, en mode *cold*.

- **cold** : attend qu'un subscriber soit présent avant d'émettre. Attention cependant, si on souscrit 2 fois à un même observable, cela crée en fait 2 observables
- **hot** : démarre tout de suite sans attendre qu'il y ait des subscribers et continue à émettre quand les subscribers sont partis. Pour créer un observable hot, il faut utiliser les méthodes successives :
    - *publish* : déclare cet Observable comme hot
    - *connect* : démarre l'émission de données

### Back pressure
Une autre question se pose :  que fait-on si on reçoit trop d'événementts par rapport à la capacité de traitement du subscriber ? (par exemple, calculs gourmands en CPU)

Le subscriber peut limiter le flux envoyé par l'Observable. Il existe la méthode *request(n)* qui permet de consommer *n* messages à la demande.

### Scheduler
Par défaut, l'Observable ou le scheduler sont lancés dans le thread courant. Les Schedulers permettent de choisir pluseurs politiques de lancement très facilement (factory), par exemple: 

- *immediate*
- *trampolin* (utilisation d'une queue)
- *newThread*
- *io*...

### Aller plus loin
Rx a été implémenté dans de nombreux autres langages. Du coup une communauté s'est formée et a produit de la documentation détaillée de haute qualité.

- ReactiveX: http://reactivex.io/
- The Reactive Manifesto: http://www.reactivemanifesto.org/

### Mon ressenti
Très bon intervenant. Sujet passionnant que je suis déjà depuis quelques temps (parce que j'utilise Hystrix de NetFlix).

## Kafka
    Jonathan Winandy, co-­fondateur  Valwin - @ahoy_jon
    http://www.parisjug.org/xwiki/bin/view/Speaker/JonathanWinandy

### Promesse de la session
Kafka est un système de messages distribué très performant (faible latence, très forte volumétrie) et il est de plus en plus utilisé en production comme un bus de service “Big Data”.

Après une présentation technique de la technologie, nous allons voir les particularités architecturales de Kafka par rapport à RabbitMq et comment on peut utiliser Kafka pour simplifier la gestion de données à l’échelle. 

### Théorie
Les Streams : notion essentielle pour comprendre Kafka. Les Streams permettent 2 opérations: 

- *append* (écrire)
- *readAt* (lire). Une fois qu'une information a été lue à un endroit, cette information sera toujours disponible à cet endroit.

### Histoire
LinkedIn avait de nembreux systèmes qui produisent beaucoup de données, d'états. Ce système était très complexe et il devenait difficile de maintenir un état dans tous les systèmes. C'est ainsi qu'est apparue la nécessité d'avoir un **journal des événements**.

Cependant, c'est assez difficile d'avoir un *stream* (au sens théorique vu au dessus) dans un système distribué pour les raisons classiques dans ces environnements :

- perte de message
- délai
- duplicats
- non respect de l'ordre

Voir à ce sujet la vidéo de Peter Alvaro ["Outwards from the middle of the maze"](https://www.youtube.com/watch?v=ggCffvKEJmQ&list=PL9Jh2HsAWHxLco7V1SjU9hUzP53CBZOYO) (et un [petit résumé](http://basho.com/peter-alvaro-outwards-from-the-middle-of-the-maze/) par Basho)

Pour un tel système, on recherche **l'idem potence**, sinon le comprtoment est totalement imprévisible.

### Anatomie de Kafka
Pour 1 topic, on peut avoir plusieurs partitions.

Kafka fonctionne avec ZooKeeper. Pour faire un publish, on parle d'abord à ZooKeeper avant de pouvoir parler à un broker.

Le producteur utilise un clef de partition au moment où le message est poussé dans Kafka. Cela permet d'avoir tous les messages d'un même contexte (ex: un utilisateur) sur un même serveur. (*cela m'a fait penser à Cassandra*)

Les consommateurs ont un état local non distribué.

### Mon ressenti
Intervention un peu foireuse (avec en plus le pas de chance pour l'effet démo/Bonaldi) qui ne ma pas convaincu.

Ce que j'en ai compris: Kafka n'est pas un bus de données (malgré ce qui est dit partout), mais un gros journal distribué. En général, on garde au moins 6 mois de données sur Kafka. Ce n'est donc pas un produit pour mon besoin actuel, mais c'est intéressant comme concept.

N'a pas parlé de RabbitMq malgré la promesse, ce qui a rendu la compréhension assez difficile.
