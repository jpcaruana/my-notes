# Comment activer HTTPS sur un serveur
## Activer ssl sur apache
````bash
$ sudo a2enmod ssl
````

## Copie des clefs publique/privée
Copier la clef privée myCompany-private.key dans /etc/ssl/private. Ce fichier doit être accessible au user root:ssl-cert, comme ici :
````bash
$ sudo ls -l /etc/ssl/private
-rw-r--r-- 1 root ssl-cert 1704 oct.   8 14:08 myCompany-private.key
````

Copier le certificat public myCompany.crt dans /etc/ssl/certs. Ce fichier doit être accessible au user root:root, comme ici :
````bash
$ sudo ls -l /etc/ssl/certs
-rw-r--r-- 1 root root   1772 oct.   8 14:07 myCompany.crt
````

Faire de même avec le certificat de Gandi (notre fournisseur SSL) dans /etc/ssl/certs/GandiStandardSSLCA.pem :
````bash
$ sudo ls -l /etc/ssl/certs
-rw-r--r-- 1 root root   1667 oct.   8 14:08 GandiStandardSSLCA.pem
````

## Configurer les virtualhost dans apache
Dans /etc/apache2/sites-available, ajouter un fichier site-ssl (en copiant le fichier site par exemple).
````xml
NameVirtualHost adresse_de_mon_site:443
  <VirtualHost adresse_de_mon_site:443>
        ServerName adresse_de_mon_site

        # ici la même chose globalement que ce qu'il y avait dans le fichier site

        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/myCompany.crt
        SSLCertificateKeyFile /etc/ssl/private/myCompany-private.key
        SSLCertificateChainFile /etc/ssl/certs/GandiStandardSSLCA.pem
  </VirtualHost>
````

Activer le site et redémarrer apache :
````bash
$ sudo a2ensite site-ssl
$ sudo service apache2 restart  # interruption de service
````

## Ouvrir le port dans IP Tables
Éditer le fichier /etc/sysctl.d/iptables et ajouter la ligne suivante après la ligne contenant "--dport 80 -j ACCEPT"
````
-A INPUT -i eth0 -p tcp -m tcp --dport 443 -j ACCEPT
````

Relancer iptables :
````bash
$ sudo service iptables restart
````

Voir aussi http://wiki.gandi.net/fr/hosting/using-linux/tutorials/ubuntu/ssl

# Comment créer une clef privée et une demande de certificat
````bash
openssl req -nodes -newkey rsa:2048 -keyout monserveur.key -out serveur.csr
````

Voir aussi http://wiki.gandi.net/fr/ssl/csr
