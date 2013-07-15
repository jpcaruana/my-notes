# Création d'une chroot
````bash
sudo debootstrap oneiric dossier_chroot
sudo chroot dossier_chroot
````

puis dans la chroot

````bash
apt-get install openssh-server
sudo apt-get install vim
sudo apt-get install git
sudo locale-gen fr

useradd toto
passwd toto
````

Changer le port de serveur sshd our éviter un conflit avec le seurveur ssh hôte. Dans le fichier */etc/ssh/sshd_config* :
````
# What ports, IPs and protocols we listen for
Port 220
````

Cette phase se scripte bien (voir [chroot/1erLancementChroot])

L'idéal est de scripter l'installation des utilitaires dans la chroot, par exemple avec ansible (http://wtww.ansibleworks.com).
