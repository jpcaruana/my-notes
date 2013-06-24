# Création d'une chroot
````bash
sudo debootstrap oneiric chroot
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
