# Mettre sa machine Linux en hibernation depuis la ligne de commande

La commande à lancer est la suivante :
````bash
sudo pm-suspend
````

Mais à la sortie d'hibernation l'écran n'est pas locké, ce qui n'est pas très sécurisé. Il faut donc le locker *avant* (j'utilise xscreensaver) :
````bash
xscreensaver-command -lock & sudo pm-suspend
````
Le soucis est que l'OS locke l'écran puis demande *ensuite* le mot de passe sudo. On n'entre donc pas en hibernation.

Il y a 2 solutions:
* faire un *sudo une commande quelconque* avant de lancer la commande et profiter de la durée de validité du sudo pour lancer la suite (c'est moche)
* ne pas avoir besoin de mot de passe pour cette commande

Pour la dernière solution, qui me semble plus élégante, il faut éditer le fichier */etc/sudoers* et y ajouter la ligne (pour le user jpcaruana) :
````
jpcaruana   ALL=(root) NOPASSWD:/usr/sbin/pm-suspend
````

Comme je n'ai pas de mémoire, je me suis fait un petit alias :
````bash
alias hibernate='xscreensaver-command -lock &  sudo pm-suspend'
````

Enfin, on peut mapper la commande sur un raccourci clavier (selon son environement de bureau) : j'ai choisi pour ma part Ctrl+Alt+Desktop.
