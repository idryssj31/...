# TP2

| Name   | IP | MAC | Fonction |
|----------|---|--------|-------|
|DESKTOP-HJMKB99|10.2.1.1(préféré)|0A-00-27-00-00-0F|

# ip statique

[idryss@localhost network-scripts]$ cat ifcfg-enp0s8
TYPE=Ethernet
BOOTPROTO=static
NAME=enp0s8
DEVICE=enp0s8
ONBOOT=yes

IPADDR=10.2.1.2
NETMASK=255.255.255.0
[idryss@localhost network-scripts]$  ifcfg-enp0s8

sudo nano enp0s8
IPADDR=10.2.1.3
sudo ifdown
 ping 127.0.0.1



# Commande ss:

[idryss@localhost ~]$ ss -l -t -u
Netid  State      Recv-Q Send-Q          Local Address:Port                           Peer Address:Port
udp    UNCONN     0      0                           *:bootpc                                    *:*
tcp    LISTEN     0      100                 127.0.0.1:smtp                                      *:*
tcp    LISTEN     0      128                         *:ssh                                       *:*
tcp    LISTEN     0      100                     [::1]:smtp                                   [::]:*
tcp    LISTEN     0      128                      [::]:ssh                                    [::]:*
[idryss@localhost ~]$

[idryss@localhost ~]$ ss -ltunp
Netid  State      Recv-Q Send-Q            Local Address:Port                           Peer Address:Port
udp    UNCONN     0      0                             *:68                                        *:*
tcp    LISTEN     0      100                   127.0.0.1:25                                        *:*
tcp    LISTEN     0      128                           *:22                                        *:*
tcp    LISTEN     0      100                       [::1]:25                                     [::]:*
tcp    LISTEN     0      128                        [::]:22                                     [::]:*
[idryss@localhost ~]$
## Notion de ports :
Port 22 car par défaut
Pour connaitre l'ip 
commande: ss
commande:  sudo ss -ltnp
commande: ip addr
 ssh 10.2.1.2
local adresse :127.0.0.1
port: 22

## Firewall.
sudo nano /etc/ssh/sshd_config.
je change le port 22 en port 1200.
sudo firewall-cmd --add-port=1200/tcp --permanent.
sudo firewall-cmd --reload.
commande: ss -lntp
local adresse port 127.0.0.1 :25
*:1200


## Netcat.
On installe netcat
:sudo yum install nc
:nc --version
On autorise l’accès au port sudo firewall-cmd --add-port=4000/tcp --permanent.
On poste un message: nc -l -p 4000
ioegb
On ouvre 2 powershell l'un pour recevoir le message l'autre pour verifier la connexion.
commande pour recevoir le message: 10.2.1.2 4000
Dans le deuxième powershell: netstat
 TCP    10.2.1.1:9248          10.2.1.2:ssh           ESTABLISHED
  TCP    10.2.1.1:9423          10.2.1.2:4000          ESTABLISHED
  On échange les rôles entre la vm et les powershells. 
On ne change pas de port juste le message.
ok
## Wireshark
on utilise Wireshark.
Captureglt.PNG


Je n'ai pas d'adaptateur ethernet donc je posterai les commandes et manip a faire mais je ne pourrais pas le faire en pratique.
Pratique Pc1 de théo.
Pc2 de Benjamin.

# Etape 1.
On change la NAT en réseau privé hôte.
On ping avec le PC1 aux PC2.
PC1: 10.2.12.1
PC2: 10.2.12.2
ping  réussi.

La commande **ifconfig** permet de configurer pour chaque carte réseau les paramètres IP (adresse, masque de réseau...).
La commande **ping** permet de tester la connectivité en direction de l'adresse indiquée. 
La commande **route** permet de configurer la table de routage de chaque machine.
La commande **traceroute**  permet de visualiser les routeurs rencontrer pour atteindre l'adresse indiquée. 
La commande **netstat** permet d’afficher les information sur la table de routage du routeur.

Tout les screens sont dans le dossier de théo et benjamin.