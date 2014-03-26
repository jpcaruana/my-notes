Lister les indexes:
````js
db.test.getIndexes()
````

Mise à jour de la collection : mettre le contenu du champ `xxx` dans le champ `yyy`

````js
db.collection.find("champ":"filtrage_where"}).forEach(function(doc) {
	doc.yyy = doc.xxx;
	db.collection.save(doc);
})
````

Renommer un champ : `toto` en `titi`

````js
db.collection.update({"champ":"filtrage_where"}, { $rename : { 'toto' : 'titi' }}, false, true)
````
