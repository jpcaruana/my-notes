http://www.parisjug.org/xwiki/bin/view/Meeting/20150310

#Paris JUG: Soirée RxJava et Kafka

## RxJava
    Hugo Cordier, CTO Melusyn - @HugoCrd
    http://www.parisjug.org/xwiki/bin/view/Speaker/HugoCordier
    https://github.com/Melusyn/ReactiveX-examples

### Callback et Futures
En java, il existe 2 façons de faire de l'asynchrone. Elles ont chacunes leurs limites :

- callbacks: totalement illisible
- Futures (en particulier les CompletableFutures de java 8) sont chaînables, mais elles ne peuvent retourner qu'une seule valeur et il y est difficile d'y gérer le temps (time outs). En outre, il y a de la gestion de Thread à faire à la main (*Rq: c'est pas vrai*)

### Origine
Erik Meyer a sorti Rx.Net (pour la plateforme Microsoft .Net) en 2012.

NetFlix s'en est très largement inspiré pour sortir en 2013 RxJava.

### Observable
Un Observable est un peu comme une Future mais itérable : elle renvoie en fait un stream d'événements asynchrones.

Un Observable pout envoyer :

- entre 0 et une infinité d'événements
- 1 erreur
- une fin de strean

L'Observable est responsable de savoir où va tourner son code : il est mono threadé par défaut. (*Rq: du coup, il faut gérer ses Threads à la main...*)

### Souscrire à un observable
Il y a 3 methodes pour réagir au événements une fois qu'on a souscrit :

- *onNext*
- *onError*
- onCo*mpleted (peu utilisé)

### Transformer les données avec les opérateurs
Un Opérateur prend en argument un Observable et retourne un Observable. C'est une fonction de transformation

Exemples: 

- *filter*
- *merge* permet de mélanger 2 flux asynchrones de même type pour retourner un nouveau flux
- *zip* permet de mélanger 2 flux asynchrones de type *différent* pour retourner un nouveau flux d'un potentiel 3ème type
- *flatMap* est équivalent à un *map* suivi d'un *merge*. pratique pour remettre à plat les flux imbriqués

démo : utilisation de swapi.co (Star Wars API) pour aller chercher en asynchrone tous les personnages, leur race et leur planète d'origine des épisodes 4 et 5.  Voir https://github.com/Melusyn/ReactiveX-examples/blob/master/src/4.%20Async/C_combining.groovy

### Gestion des erreurs
Toute erreur est "catchée" et envoyée dans le handleError. Par défaut, une erreur arrête immédiatement l'Observable.

Il existe des méthodes pour réagir sur ces erreurs : 

- *onErrorReturn*: retourne une valeur prédéfinie et s'arrête
- *onErrorResumeNext* : permet d'utiliser un nouveau flux de données

### Hot and cold
Une question se pose : à partir de quel moment un Observable va-t-il commencer à émettre des données ?

Par défaut, en mode *cold*.

- **cold** : attend qu'un subscriber soit présent avant d'émettre. Attention cependant, si rn souscrit 2 fois à un même observable, cela crée en fait 2 observables
- **hot** : démarre tout de suite sans attendre qu'il y ait des subscribers et continue à émettre quand les subscribers sont partis. Pour créer un observable hot, il faut utiliser les méthodes successives :
    - *publish* : déclare cet Observable comme hot
    - *connect* : démarre l'émission de données

### Back pressure
Une autre question se pose :  que fait-on si on reçoit trop d'événementts par rapport à la capacité de traitement du subscriber ? (par exemple, calculs gourmands en CPU)

Le subscriber peut limiter le flux enoyé par l'Observable. Il existe la méthode *request(n)* qui permet de consommer *n* messages à la demande.

### Scheduler
Par défaut, l'Observable ou le scheduler sont lancés dans le thread courant. Les Schedulers permettent de choisir pluseurs politiques de lancement très facilement (factory), par exemple: *immediate*, *trampolin* (utilisation d'une queue), *newThread*, *io*...

### Aller plus loin
Rx a été implémenté dans de nombreux autres langages. Du coup une communauté s'est formée et a produit de la documentation détaillée de haute qualité.

- ReactiveX: http://reactivex.io/
- The Reactive Manifesto: http://www.reactivemanifesto.org/

## Kafka
