<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Création d'une chroot](#cr%C3%A9ation-dune-chroot)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
