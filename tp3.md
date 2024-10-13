# Tp 3 reseau


# I. ARP basics

☀️ Avant de continuer...
affichez l'adresse MAC de votre carte WiFi !

```` 
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : 98-BD-80-D5-2B-BD
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::e6e1:ef7c:e509:f762%3(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.26(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : mardi 8 octobre 2024 13:26:42
   Bail expirant. . . . . . . . . . . . . : mercredi 9 octobre 2024 13:26:43
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 60341632
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-49-D1-4C-D8-43-AE-D4-F5-E6
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
   ````

   ☀️ Affichez votre table ARP

   ````
   PS C:\Users\titda> arp -a

Interface : 10.33.77.26 --- 0x3
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  10.33.79.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.56.1 --- 0x7
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
  ````

  ☀️ Déterminez l'adresse MAC de la passerelle du réseau de l'école

  ````
   PS C:\Users\titda> arp -a
   10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
````

☀️ Supprimez la ligne qui concerne la passerelle

````
PS C:\Windows\system32> arp -d 10.33.79.254
````
PS C:\Windows\system32> arp -d 10.33.79.254 ; arp -a
````
Interface : 10.33.77.26 --- 0x3
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.79.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.56.1 --- 0x7
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
````


# II. ARP dans un réseau local

1. Basics

☀️ Déterminer

````
PS C:\Users\titda> ipconfig /all

Configuration IP de Windows

   Nom de l’hôte . . . . . . . . . . : Pc-portable-Theo
   Suffixe DNS principal . . . . . . :
   Type de noeud. . . . . . . . . .  : Hybride
   Routage IP activé . . . . . . . . : Non
   Proxy WINS activé . . . . . . . . : Non

Carte Ethernet Ethernet :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . : home
   Description. . . . . . . . . . . . . . : Realtek PCIe GbE Family Controller
   Adresse physique . . . . . . . . . . . : D8-43-AE-D4-F5-E6
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui

Carte Ethernet Ethernet 2 :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter
   Adresse physique . . . . . . . . . . . : 0A-00-27-00-00-07
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::67f9:6eda:19ac:613%7(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.56.1(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :
   IAID DHCPv6 . . . . . . . . . . . : 688521255
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-49-D1-4C-D8-43-AE-D4-F5-E6
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé

Carte réseau sans fil Connexion au réseau local* 1 :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter
   Adresse physique . . . . . . . . . . . : 98-BD-80-D5-2B-BE
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui

Carte réseau sans fil Connexion au réseau local* 2 :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter #2
   Adresse physique . . . . . . . . . . . : 9A-BD-80-D5-2B-BD
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : 98-BD-80-D5-2B-BD
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2a04:cec0:101b:f5ca:1302:155f:f65d:4b6a(préféré)
   Adresse IPv6 temporaire . . . . . . . .: 2a04:cec0:101b:f5ca:e1fd:d092:9349:8806(préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::e6e1:ef7c:e509:f762%3(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.4(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.240
   Bail obtenu. . . . . . . . . . . . . . : mardi 8 octobre 2024 16:44:49
   Bail expirant. . . . . . . . . . . . . : mercredi 9 octobre 2024 16:44:49
   Passerelle par défaut. . . . . . . . . : fe80::e8a7:30ff:fef0:f164%3
                                       172.20.10.1
   Serveur DHCP . . . . . . . . . . . . . : 172.20.10.1
   IAID DHCPv6 . . . . . . . . . . . : 60341632
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-49-D1-4C-D8-43-AE-D4-F5-E6
   Serveurs DNS. . .  . . . . . . . . . . : fe80::e8a7:30ff:fef0:f164%3
                                       172.20.10.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé

Carte Ethernet Connexion réseau Bluetooth :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Adresse physique . . . . . . . . . . . : 98-BD-80-D5-2B-C1
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   ````

   ☀️ DIY
   ````
   PS C:\Users\titda> ipconfig

Configuration IP de Windows


Carte Ethernet Ethernet :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . : home

Carte Ethernet Ethernet 2 :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::67f9:6eda:19ac:613%7
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.56.1
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :

Carte réseau sans fil Connexion au réseau local* 1 :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :

Carte réseau sans fil Connexion au réseau local* 2 :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6. . . . . . . . . . . . . .: 2a04:cec0:101b:f5ca:1302:155f:f65d:4b6a
   Adresse IPv6 temporaire . . . . . . . .: 2a04:cec0:101b:f5ca:3c6d:e80:df4:dbcd
   Adresse IPv6 de liaison locale. . . . .: fe80::e6e1:ef7c:e509:f762%3
   Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.13
   Masque de sous-réseau. . . . . . . . . : 255.255.255.240
   Passerelle par défaut. . . . . . . . . : fe80::e8a7:30ff:fef0:f164%3

Carte Ethernet Connexion réseau Bluetooth :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
````




   ☀️ Pingz !
   ````
   PS C:\Users\titda> ping 172.20.10.14

Envoi d’une requête 'Ping'  172.20.10.14 avec 32 octets de données :
Réponse de 172.20.10.14 : octets=32 temps=17 ms TTL=128
Réponse de 172.20.10.14 : octets=32 temps=38 ms TTL=128
Réponse de 172.20.10.14 : octets=32 temps=9 ms TTL=128
Réponse de 172.20.10.14 : octets=32 temps=6 ms TTL=128

Statistiques Ping pour 172.20.10.14:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 6ms, Maximum = 38ms, Moyenne = 17ms
PS C:\Users\titda> ping 172.20.10.10

Envoi d’une requête 'Ping'  172.20.10.10 avec 32 octets de données :
Réponse de 172.20.10.10 : octets=32 temps=5 ms TTL=128
Réponse de 172.20.10.10 : octets=32 temps=20 ms TTL=128
Réponse de 172.20.10.10 : octets=32 temps=5 ms TTL=128
Réponse de 172.20.10.10 : octets=32 temps=18 ms TTL=128

Statistiques Ping pour 172.20.10.10:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 5ms, Maximum = 20ms, Moyenne = 12ms
PS C:\Users\titda> ping 172.20.10.2

Envoi d’une requête 'Ping'  172.20.10.2 avec 32 octets de données :
Réponse de 172.20.10.2 : octets=32 temps=6 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=8 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=9 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=3 ms TTL=128

Statistiques Ping pour 172.20.10.2:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 3ms, Maximum = 9ms, Moyenne = 6ms

PS C:\Users\titda> ping google.com

Envoi d’une requête 'ping' sur google.com [2a00:1450:4007:807::200e] avec 32 octets de données :
Réponse de 2a00:1450:4007:807::200e : temps=52 ms
Réponse de 2a00:1450:4007:807::200e : temps=45 ms
Réponse de 2a00:1450:4007:807::200e : temps=102 ms
Réponse de 2a00:1450:4007:807::200e : temps=20 ms

Statistiques Ping pour 2a00:1450:4007:807::200e:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 20ms, Maximum = 102ms, Moyenne = 54ms

````

2. ARP

☀️ Affichez votre table ARP !

````
PS C:\Users\titda> arp -a

Interface : 172.20.10.13 --- 0x3
  Adresse Internet      Adresse physique      Type
  172.20.10.2           e4-c7-67-b5-a2-3e     dynamique
  172.20.10.14          c0-35-32-1c-af-a9     dynamique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique

Interface : 192.168.56.1 --- 0x7
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
````