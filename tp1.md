#  Tp Reseau

I. Récolte d'informations


🌞 Adresses IP de ta machine

```
PS C:\Users\titda> ipconfig /all

Configuration IP de Windows


Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : 98-BD-80-D5-2B-BD
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::e6e1:ef7c:e509:f762%3(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.26(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : vendredi 27 septembre 2024 13:35:12
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 13:35:12
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 60341632
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-49-D1-4C-D8-43-AE-D4-F5-E6
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé


Carte Ethernet Ethernet :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . : home
   Description. . . . . . . . . . . . . . : Realtek PCIe GbE Family Controller
   Adresse physique . . . . . . . . . . . : D8-43-AE-D4-F5-E6
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
```

🌞 Si t'as un accès internet normal, d'autres infos sont forcément dispos...

````
PS C:\Users\titda> ipconfig /all

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : 98-BD-80-D5-2B-BD
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::e6e1:ef7c:e509:f762%3(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.26(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : vendredi 27 septembre 2024 13:35:12
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 13:35:12
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 60341632
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-49-D1-4C-D8-43-AE-D4-F5-E6
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
````

🌟 BONUS : Détermine s'il y a un pare-feu actif sur ta machine

````
PS C:\Users\titda> Get-NetFirewallProfile | ft Name,Enabled

Name    Enabled
----    -------
Domain     True
Private    True
Public     True
````


II. Utiliser le réseau

🌞 Envoie un ping vers...

 1.toi-même 

 ````
 PS C:\Users\titda> ping 10.33.77.26

Envoi d’une requête 'Ping'  10.33.77.26 avec 32 octets de données :
Réponse de 10.33.77.26 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.26 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.26 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.26 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.33.77.26:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
````

2. vers l'adresse IP 127.0.0.1

````
PS C:\Users\titda> ping 127.0.0.1

Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
````


🌞 On continue avec ping. Envoie un ping vers...

1.ta passerelle

````
PS C:\Users\titda> ping 10.33.79.254

Envoi d’une requête 'Ping'  10.33.79.254 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 10.33.79.254:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),
````

2. un(e) pote sur le réseau
````
PS C:\Users\titda> ping 10.33.66.78

Envoi d’une requête 'Ping'  10.33.66.78 avec 32 octets de données :
Réponse de 10.33.66.78 : octets=32 temps=116 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=19 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=5 ms TTL=64
Réponse de 10.33.66.78 : octets=32 temps=56 ms TTL=64

Statistiques Ping pour 10.33.66.78:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 5ms, Maximum = 116ms, Moyenne = 49ms
````

3. un site internet
````

PS C:\Users\titda> ping www.thinkerview.com

Envoi d’une requête 'ping' sur www.thinkerview.com [188.114.96.7] avec 32 octets de données :
Réponse de 188.114.96.7 : octets=32 temps=15 ms TTL=55
Réponse de 188.114.96.7 : octets=32 temps=14 ms TTL=55
Réponse de 188.114.96.7 : octets=32 temps=15 ms TTL=55
Réponse de 188.114.96.7 : octets=32 temps=14 ms TTL=55

Statistiques Ping pour 188.114.96.7:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 14ms, Maximum = 15ms, Moyenne = 14ms
````

🌞 Faire une requête DNS à la main

````
PS C:\Users\titda> nslookup www.thinkerview.com
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.thinkerview.com
Addresses:  2a06:98c1:3120::7
          2a06:98c1:3121::7
          188.114.97.7
          188.114.96.7


PS C:\Users\titda> nslookup www.wikileaks.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    wikileaks.org
Addresses:  80.81.248.21
          51.159.197.136
Aliases:  www.wikileaks.org


PS C:\Users\titda> nslookup www.torproject.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.torproject.org
Addresses:  2620:7:6002:0:466:39ff:fe7f:1826
          2620:7:6002:0:466:39ff:fe32:e3dd
          2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
          2a01:4f9:c010:19eb::1
          2a01:4f8:fff0:4f:266:37ff:feae:3bbc
          116.202.120.165
          204.8.99.146
          204.8.99.144
          116.202.120.166
          95.216.163.36
````

III. Sniffer le réseau


IV. Network scanning et adresses IP

🌞 Effectue un scan du réseau auquel tu es connecté

````
PS C:\Users\titda> nmap -sn -PR 10.33.64.0
Starting Nmap 7.95 ( https://nmap.org ) at 2024-09-27 17:27 Paris, Madrid (heure dÆÚtÚ)
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 1.54 seconds
PS C:\Users\titda> nmap -sn -PR 10.33.64.0/20
Starting Nmap 7.95 ( https://nmap.org ) at 2024-09-27 17:29 Paris, Madrid (heure dÆÚtÚ)


Nmap scan report for 10.33.66.78
Host is up (0.090s latency).
MAC Address: E4:B3:18:48:36:68 (Intel Corporate)
Nmap scan report for 10.33.69.82
Host is up (0.35s latency).
MAC Address: 50:A6:D8:A9:55:02 (Apple)
Nmap scan report for 10.33.69.143
Host is up (0.41s latency).
MAC Address: 3C:A6:F6:31:FE:F6 (Apple)
Host is up.
Nmap done: 4096 IP addresses (162 hosts up) scanned in 132.09 seconds
````

🌞 Changer d'adresse IP

````
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : 98-BD-80-D5-2B-BD
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::e6e1:ef7c:e509:f762%3(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.66.80(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 60341632
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-49-D1-4C-D8-43-AE-D4-F5-E6
   Serveurs DNS. . .  . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
````