grep entre `x` et `y` occurences d'une série de chiffres:
* échapper les accolades pour le nombres d'occurences
* pas besoin de l'option `-e`

````bash
grep "[0-9]\{x,y\}" file
````
