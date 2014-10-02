# Splitter une archive trop grosse
d'après http://stackoverflow.com/questions/1120095/split-files-using-tar-gz-zip-or-bzip2

La limite de taille de fichiers chez Amazon S3 est de 5 Go. Il est agréable parfois de pouvoir envoyer de plus fichiers tgz, mais pour cela il faut faire un split :

````bash
$ fiveGigas=5300000000
$ tar --create --gzip MonDossierVolumineux | split --numeric-suffixes --bytes ${fiveGigas} - fichier.tgz_

$ ls fichier.tgz_*
fichier.tgz_00  fichier.tgz_01  fichier.tgz_02
````
