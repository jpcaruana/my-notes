Installer docker (cf leur doc sur leur site https://www.docker.io)

Le Dockerfile permet de créer un serveur de base à par d'une ubuntu/precise pour tester des scripts ansible externnes.

On peut se logguer avec le user root (mot de passe toto).

````bash
# build image
docker build -t jpcaruana/baseServer .

# launch 3 servers (daemon mode)
docker run -d -p 22 -t jpcaruana/baseServer -D
docker run -d -p 22 -t jpcaruana/baseServer -D
docker run -d -p 22 -t jpcaruana/baseServer -D

# check for their ssh port
docker ps
CONTAINER ID        IMAGE                         COMMAND             CREATED             STATUS              PORTS                   NAMES
00d153596d54        jpcaruana/baseServer:latest   /usr/sbin/sshd -D   30 minutes ago      Up 30 minutes       0.0.0.0:49164->22/tcp   thirsty_archimedes   
4e676ded037e        jpcaruana/baseServer:latest   /usr/sbin/sshd -D   30 minutes ago      Up 30 minutes       0.0.0.0:49163->22/tcp   kickass_engelbart    
fcd79f94e99e        jpcaruana/baseServer:latest   /usr/sbin/sshd -D   30 minutes ago      Up 30 minutes       0.0.0.0:49162->22/tcp   grave_torvalds       

# check for local docker ip
ifconfig docker0
docker0   Link encap:Ethernet  HWaddr fe:58:a0:c7:e0:dd  
          inet adr:X.Y.Z.K  Bcast:0.0.0.0  Masque:255.255.0.0
          adr inet6: fe80::4c2a:6ff:fe9b:bdf6/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:52675 erreurs:0 :0 overruns:0 frame:0
          TX packets:95227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:3462293 (3.4 MB) Octets transmis:140406957 (140.4 MB)

# log in the first one
ssh root@X.Y.Z.K -p 49162
exit

# play with (well configured) ansible:)
ansible-playbook --connection=ssh --inventory-file=localdocker site.yml
````
