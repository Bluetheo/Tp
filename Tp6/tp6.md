# TP6 : Des bo services dans des bo LANs

I. Le setup
2. Marche à suivre

☀️ Prouvez que...

une machine du LAN1 peut joindre internet (ping un nom de domaine)
````
[theo@dhcp ~]$ ping ynov.com
PING ynov.com (104.26.11.233) 56(84) bytes of data.
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=1 ttl=53 time=15.8 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=2 ttl=53 time=16.2 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=3 ttl=53 time=15.5 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=4 ttl=53 time=16.0 ms
^C
--- ynov.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3008ms
rtt min/avg/max/mdev = 15.540/15.895/16.183/0.237 ms
````

une machine du LAN2 peut joindre internet (ping nom de domaine)
````
[theo@dns ~]$ ping google.com
PING google.com (142.251.37.46) 56(84) bytes of data.
64 bytes from mrs09s13-in-f14.1e100.net (142.251.37.46): icmp_seq=1 ttl=112 time=16.8 ms
64 bytes from mrs09s13-in-f14.1e100.net (142.251.37.46): icmp_seq=2 ttl=112 time=21.9 ms
64 bytes from mrs09s13-in-f14.1e100.net (142.251.37.46): icmp_seq=3 ttl=112 time=16.5 ms
64 bytes from mrs09s13-in-f14.1e100.net (142.251.37.46): icmp_seq=4 ttl=112 time=17.0 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3008ms
rtt min/avg/max/mdev = 16.496/18.041/21.929/2.250 ms
````



une machine du LAN1 peut joindre une machine du LAN2 (ping une adresse IP)

````
[theo@dhcp ~]$ ping 10.6.2.12
PING 10.6.2.12 (10.6.2.12) 56(84) bytes of data.
64 bytes from 10.6.2.12: icmp_seq=1 ttl=63 time=1.54 ms
64 bytes from 10.6.2.12: icmp_seq=2 ttl=63 time=0.840 ms
64 bytes from 10.6.2.12: icmp_seq=3 ttl=63 time=0.844 ms
^C
--- 10.6.2.12 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 0.840/1.075/1.542/0.329 ms
````

II. LAN clients

1. Serveur DHCP


2. Client

☀️ Prouvez que..
````
[theo@client1 ~]$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:20:19:a9 brd ff:ff:ff:ff:ff:ff
    inet 10.6.1.37/24 brd 10.6.1.255 scope global dynamic noprefixroute enp0s3
       valid_lft 479sec preferred_lft 479sec
    inet6 fe80::a00:27ff:fe20:19a9/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
````
````
[theo@client1 ~]$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 1.1.1.1
````
````
[theo@client1 ~]$ ip route show
default via 10.6.1.254 dev enp0s3 proto dhcp src 10.6.1.37 metric 100
10.6.1.0/24 dev enp0s3 proto kernel scope link src 10.6.1.37 metric 100
````
````
[theo@client1 ~]$ ping ynov.com
PING ynov.com (104.26.11.233) 56(84) bytes of data.
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=1 ttl=53 time=15.9 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=2 ttl=53 time=16.8 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=3 ttl=53 time=19.4 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=4 ttl=53 time=17.0 ms
^C
--- ynov.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3007ms
rtt min/avg/max/mdev = 15.944/17.281/19.358/1.263 ms
````


III. LAN serveurzzzz

3. Analyse et test

1. Serveur Web

☀️ Déterminer sur quel port écoute le serveur NGINX

````
[theo@web ~]$ sudo ss -lnpt | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1573,fd=6),("nginx",pid=1572,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=1573,fd=7),("nginx",pid=1572,fd=7))
````

☀️ Ouvrir ce port dans le firewall
````
[theo@web ~]$ sudo firewall-cmd --permanent --add-port=80/tcp
success
[theo@web ~]$ sudo firewall-cmd --reload
success
````

☀️ Visitez le site web !

````
[theo@client1 ~]$ curl http://10.6.2.11
<!doctype html>
<html>
  <head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <title>HTTP Server Test Page powered by: Rocky Linux</title>
    <style type="text/css">
      /*<![CDATA[*/

      html {
        height: 100%;
        width: 100%;
      }
````


2. Serveur DNS

☀️ Déterminer sur quel(s) port(s) écoute le service BIND9

````
[theo@dns ~]$ sudo ss -lnpu | grep 53
UNCONN 0      0          10.6.2.12:53        0.0.0.0:*    users:(("named",pid=1891,fd=24))
UNCONN 0      0          127.0.0.1:53        0.0.0.0:*    users:(("named",pid=1891,fd=21))
UNCONN 0      0              [::1]:53           [::]:*    users:(("named",pid=1891,fd=26))
````

☀️ Effectuez une requête DNS manuellement depuis client1.tp6.b1
````
[theo@client1 ~]$ dig dns web.tp6.b1 @10.6.2.12

; <<>> DiG 9.16.23-RH <<>> dns web.tp6.b1 @10.6.2.12
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 62666
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;dns.                           IN      A

;; AUTHORITY SECTION:
.                       85883   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2024102100 1800 900 604800 86400

;; Query time: 23 msec
;; SERVER: 1.1.1.1#53(1.1.1.1)
;; WHEN: Mon Oct 21 16:15:21 CEST 2024
;; MSG SIZE  rcvd: 107

````

☀️ Capturez une requête DNS et la réponse de votre serveur

Voir 

3. Serveur DHCP


☀️ Créez un nouveau client client2.tp6.b1 vitefé

````
[theo@client1 ~]$ curl http://web.tp6.b1
<!doctype html>
<html>
  <head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <title>HTTP Server Test Page powered by: Rocky Linux</title>
    <style type="text/css">
      /*<![CDATA[*/

      html {
        height: 100%;
        width: 100%;
      }
````