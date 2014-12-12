A chaque `git fetch` ou `git pull --rebase`, j'avais un message agaçant, même quand il n'y avait rien à faire :

````bash
$ igt pull --rebase
Compression automatique du dépôt en tâche de fond pour optimiser les performances.
Voir "git help gc" pour toute information sur le nettoyage manuel.
Already up-to-date.
````

Super énervant.

J'ai tenté des `git gc`, `git gc --auto` et des `git gc --aggressive`, rien n'y faisait.

Après [recherche](http://stackoverflow.com/questions/7392155/why-does-git-run-git-gc-auto-on-every-merge), j'ai trouvé la réponse :

````bash
$ git fsck
Vérification des répertoires d'objet: 100% (256/256), fait.
Vérification des objets: 100% (123706/123706), fait.
$ git repack
Nothing new to pack.
$ git pull --rebase 
La branche courante develop est à jour.
````

A noter que git me parle à la foois en français en en anglais.
