# Tp 2 Reseau

1. Quelques pings

🌞 Prouvez que votre configuration est effective

````
theo@theo-ubuntu:~$ ip addr show enp0s8
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:20:5a:9f brd ff:ff:ff:ff:ff:ff
    inet 192.168.56.107/24 brd 192.168.56.255 scope global dynamic noprefixroute enp0s8
       valid_lft 597sec preferred_lft 597sec
    inet6 fe80::1ba3:cff1:ae50:f013/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
````


🌞 Tester que votre LAN + votre adressage IP est fonctionnel

````
PS C:\Users\titda> ping 192.168.56.107

Envoi d’une requête 'Ping'  192.168.56.107 avec 32 octets de données :
Réponse de 192.168.56.107 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.107 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.107 : octets=32 temps<1ms TTL=64
Réponse de 192.168.56.107 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 192.168.56.107:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes
````

🌞 Capture de ping

````
Voir capture wireshark
````



# II. Utilisation des ports

🌞 Sur le PC serveur
````
theo@theo-ubuntu:~$ nc -l 9999
````

🌞 Sur le PC serveur toujours
````
theo@theo-ubuntu:~$ sudo ss -lnpt
[sudo] password for theo:
State        Recv-Q       Send-Q             Local Address:Port               Peer Address:Port       Process
LISTEN       0            4096                  127.0.0.54:53                      0.0.0.0:*           users:(("systemd-resolve",pid=6274,fd=17))
LISTEN       0            4096                   127.0.0.1:631                     0.0.0.0:*           users:(("cupsd",pid=1299,fd=7))
LISTEN       0            4096               127.0.0.53%lo:53                      0.0.0.0:*           users:(("systemd-resolve",pid=6274,fd=15))
LISTEN       0            4096                           *:22                            *:*           users:(("sshd",pid=4404,fd=3),("systemd",pid=1,fd=133))
LISTEN       0            4096                       [::1]:631                        [::]:*
 users:(("cupsd",pid=1299,fd=6))
````

🌞 Sur le PC client
````
PS C:\Users\titda\Downloads\netcat-win32-1.11 (2)\netcat-1.11> .\nc64.exe 192.168.56.107 9999
````

🌞 Echangez-vous des messages
````
PS C:\Users\titda\Downloads\netcat-win32-1.11 (2)\netcat-1.11> .\nc64.exe 192.168.56.107 9999
foeczu
cds
dstest
call of the best
````


🌞 Utilisez une commande qui permet de voir la connexion en cours à faire sur le client ET sur le serveur

Pas reussi


🌞 Faites une capture Wireshark complète d'un échange

🌞 Inversez les rôles

J'ai fait le tp sur une machine virtuelle


# III. Analyse de vos applications usuelles

1. Serveur web

🌞 Utilisez Wireshark pour capturer du trafic HTTP

2. Autres services

🌞 Pour les 5 applications

