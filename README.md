# Netwhat
"*A protocol is a set of rules that define how communication occurs in a network"*

Adress mapping = correspondance entre adresse logique IP et adresse physique MAC. 

**ICMP** est un protocole dans la suite protocolaire **TCP-IP** utilisé pour envoyer des messages d'erreurs dans un réseau. Il travaille en partenariat avec le protocole **IP.**

### Qu’est-ce qu’une adresse IP ?

Une Adresse relative au réseau. Moyen d'authentification sur internet.

1. IPv4 : 32 Bits / 4 x 1 octets compris entre 0 et 255, séparés par des points. Ex : 88.45.124.201 ; 255(décimal) = 11111111(bit) = 1(octet)
2. IPv6 : 128 Bits / 8 x 2 octets en hexadécimal séparés par deux points.          Ex : 1fff:0000:0a88:85a3:0000:0000:ac1f:8001 ; ffff = 16bits = 8 octets 

IPv6 est fait pour rendre le transfert de paquets plus sécurisé, Meilleures fonctionnalités de multidiffusion dans le cas de l'IPv6.

Comparaison au numéro de maison

Les adresses IP sont routables. Elles peuvent communiquer avec des machines au delà d'un sous-réseau, contrairement aux adresses MAC

5 classes :

1. A : IP 0.0.0.0 à 127.255.255.255 ; 255.0.0.0 (par défaut masque)
2. B : IP 128.0.0.0 à 191.255.255.255 ; 255.255.0.0
3. C : IP 192.0.0.0 à 223.255.255.255 ; 255.255.255.0
4. D : IP 224.0.0.0 à 239.255.255.255 : adresses de multicast
5. E : IP 240.0.0.0 à 255.255.255.255 : adresses réservées par IETF

Dans une adresse IP, c'est la partie gauche qui correspond à l'identité du réseau, et la partie droite qui correspond à l'identité de l'hôte.

### Qu’est-ce qu’un masque de sous-réseau

Divise une adresse IP en une partie réseau et une partie hôte.

<network><host>

Comparaison au nom d'une rue. C'est une suite de nombres qui dit que telle partie correspond au nom de la rue (au sous-réseau) et telle partie identifie l'hôte (le numéro de la maison)(IP).

Un pays représente dans notre exemple un sous-réseau du réseau télécom mondial et l'indicatif de ce pays (+33) est équivalent au masque du sous-réseau. Le numéro de téléphone pouvant être comparé à l'adresse IP.

Ce masque va définir quelle partie de l'adresse IP identifie le réseau (cette partie est appellée network ID) et quelle partie identifie l'hôte sur le réseau (host ID).

Un masque de sous-réseau définit donc la plage d'adresses IP avec laquelle une carte réseau peut communiquer directement. Pour communiquer avec des adresses IP extérieures à cette plage, elle doit passer par une passerelle par défaut.

Les octets du masque ayant pour valeur **255** sont les mêmes que les octets de l'adresse IP définissant le **network ID**. De même, les octets du masque valant **0** correspondent aux octets de l'adresse IP définissant **l'host ID**

On ne peut pas mélanger les zéros et les autres valeurs. En somme, tous les 255 doivent être à gauche et les zéros à droite

### Qu’est-ce que le sous-réseau d’une IP avec un masque de sous-réseau

<network> <subnet> <host>

L'adresse de sous-réseau est obtenu en appliquant l'opérateur "ET" binaire entre l'adresse IP et le masque de sous-réseau

### Qu’est-ce que l’adresse de ’broadcast’ et celle de ’sous-réseau’ d’un sous-réseau

Est une adresse par laquelle tous les appareils connectés au réseau peuvent recevoir des datagrammes. Un message envoyé à une adresse broadcast peut être reçu par tous les hôtes connectés au réseau

L’adresse IP 255.255.255.255 sert à la diffusion broadcast.

### Quelles sont les différentes manières de représenter une IP avec un masque de sous-réseau

### Quel est la différence entre une IP privée et une IP publique?

Pour permettre à une adresse privée d'accéder à Internet, l'adresse doit être traduite en adresse publique appelée NAT

Les adresses **IP privées** se trouve dans les classes A, B et C, pas utilisables sur internet sans routeur (réseau entreprise ou domestique) les plages sont : 

1. A : 10.0.0.0 à 10.255.255.25
2. B : 172.16.0.0 à 172.31.255.255
3. C : 192.168.1.0 à 192.168.255.255

Une adresse **IP publique** est unique dans le monde alors que pour une adresse IP privée c’est dans le réseau local qu’elle est unique. Fournies par le FAI

Exceptions :

- 127.0.0.1 : réservé pour les tests de boucle locale
- 0.0.0.0 : réservé pour définir une route par défaut sur un routeur

### Quel sont les différentes classes d’IP

dynamiques/variables et statiques/fixes.

Les adresses IP publique peuvent être static ou dynamique :

 

- Une adresse ip statique est inchangée et est souvent utilisée pour host des sites web ou server.
- Une adresse dynamique est attribuée a partir d'une pool d'adresses et peut être changé a chaque connexion.

### Qu’est-ce que le TCP

*Transmission Control Protoco*l

TCP = connection-oriented, vérification periodique de l'état de la session de communication. TCP ne prend pas en charge la diffusion. Et n'est pas orienté datagramme.

TCP fournit des mecanismes de verification d'erreur etendus. C'est parce qu'il fournit le controle de flux et l'acquittement des données.

TCP est comparativement plus lent que UDP. TCP est fiable car il garantit la livraison des donnees au routeur de la destination.

Modele TCP/IP : TCP au dessus de IP

Modele OSI : TCP correspond a la couche de transport

Découpe le flux d'octets en segments.

Une session TCP fonctionne en trois phases :

- l'établissement de la connexion ;
- les transferts de données ;
- la fin de la connexion.

Pendant la phase de transferts de données, certains mécanismes clefs permettent d'assurer la robustesse et la fiabilité de TCP. En particulier, les numéros de séquence sont utilisés afin d'ordonner les segments TCP reçus et de détecter les données perdues, les sommes de contrôle permettent la détection d'erreurs, et les acquittements ainsi que les temporisations permettent la détection des segments perdus ou retardés. Grâce aux numéros de séquence et d'acquittement, les systèmes terminaux peuvent remettre les données reçues dans l'ordre à l'application destinataire.

Dans chaque segment TCP : numéro de séquence et le numéro d'acquittement.

### Qu’est-ce que l’UDP

UDP = connectionless-oriented, **User Datagram Protocol**. UDP est un protocole oriente datagramme.

UDP fournit des mecanismes de verification d'erreur etendus. C'est parce qu'il fournit le controle de flux et l'acquittement des donees

UDP prend en charge la diffusion.

UDP est plus rapide, plus simple et plus efficace que TCP.

UDP : est souvent utilisé pour le temps réel mais est moins fiable

UDP ne dispose que du mecanisme de controle d'erreur de base

Utilisé par :

- DNS
- IP telephony
- DHCP
- Computer games

### Quelles sont les différentes couches d’un réseau

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2af06295-79d6-48e9-b1b5-6e9968525d29/image.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2af06295-79d6-48e9-b1b5-6e9968525d29/image.png)

Le modèle OSI a segmenté la communication en **sept** couches :

1. **Application** (ou couche applicative) : *interface pour accéder aux services réseaux* 
2. **Présentation** : *formatage pour la presentation des données* *(format, cryptage, encodage, etc.).*
3. **Session** : établi une session entre les applications (ouvre, gère et clos la session)
4. **Transport**  : prepare le mail à l'envoi, divise les données en segments ou sequences (TCP utilisé)
5. **Réseau / Network** : se charge du routage et de l'adressage, utilise adresse IP source et du récepteur (protocole IP utilisé), liaison logique.
6. **Liaison de données / Data** : établi une liaison physique, elle fragmente les données en plusieurs trames, qui sont envoyées une par une dans un réseau local.
7. **Physique / Processing** : reçoit les trames et les convertit en une session de bits qui sont ensuite mis sur le media pour l'envoi. Se charge de la transmission de signaux électriques ou optiques entre les hôtes.

    *`All People Seem To Need Data Processing` (APSTNDP)*

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd675ab4-10f6-435e-9b4f-74705f55aea1/Screen_Shot_2020-12-03_at_3.26.16_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd675ab4-10f6-435e-9b4f-74705f55aea1/Screen_Shot_2020-12-03_at_3.26.16_PM.png)

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5560710e-1357-4ba1-ab04-21f6ef5fbb9f/Screen_Shot_2020-12-04_at_12.37.17_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5560710e-1357-4ba1-ab04-21f6ef5fbb9f/Screen_Shot_2020-12-04_at_12.37.17_PM.png)

Les données que vous transmettez sont tout simplement appelées unité de données (data unit : PDU = protocol data unit, précédé de l'initiale de la couche )

Dans la couche réseau du modèle OSI, ces données prennent le nom de paquets ; dans les couches liaison et physique, respectivement ceux de frame (trame) et bit.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2ac0c4a-c8dd-47ed-bf20-2c4a76fa4ad7/image.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2ac0c4a-c8dd-47ed-bf20-2c4a76fa4ad7/image.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b5837717-7d0f-46a3-b8a7-fc02852f5a05/image.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b5837717-7d0f-46a3-b8a7-fc02852f5a05/image.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/de12cda3-893b-45f4-8dea-568d9528076b/image.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/de12cda3-893b-45f4-8dea-568d9528076b/image.png)

Dans une couche C, le PDU est le SDU de la couche C + 1 plus son en-tête (couche C) : encapsulation.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd98bda5-2f3a-42a2-8778-81b97baa6cd9/image.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd98bda5-2f3a-42a2-8778-81b97baa6cd9/image.png)

Full-duplex/half-duplex = communication en simultané/chacun son tour.

1. Protocole de la couche Applicative (Application, Présentation, Session) : 

[Protocoles](https://www.notion.so/Protocoles-f658d8cc60074d199317fcb417c22252)

### Qu’est-ce que le modèle OSI

Le modèle OSI (Open Systems Interconnection : « interconnexion de systèmes ouverts ») est une façon standardisée de segmenter en plusieurs blocs le processus de communication entre deux entités. Chaque bloc résultant de cette segmentation est appelé couche

### A quoi sert un serveur DHCP et qu’est-ce que le protocole DHCP

Serveur DHCP (dynamic host configuration protocol) set a distribuer les adresses IP sur un réseau.

Utilise UDP

DHCP est aussi utilisé pour configurer le masque de sous réseau et le DNS.

### A quoi sert un serveur DNS et qu’est-ce que le protocole DNS

*Domain name system* 

Permet de traduire les noms de domaines en adresse IP

### Quelles sont les configurations minimales pour faire communiquer 2 appareils en utilisant IP

Ordinateur -> Passerelle(routeur) -> Internet -> Passerelle -> Serveur

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cb777906-23cf-45f5-a49f-25e697880c01/image.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cb777906-23cf-45f5-a49f-25e697880c01/image.png)

### Comment marche le routage IP

Sélection des chemins, dans un réseau, par lesquels on va faire acheminer les données, de l'expéditeur vers le ou les destinataire(s)

### Qu’est-ce qu’on appelle une passerelle par defaut et à quoi ca sert

Une passerelle est plus communément appelée modem-routeur ou box, relie un réseau local à Internet. Elle sert également de pare-feu, de proxy, et effectue la qualité de service. Une passerelle par défaut est une passerelle qui gère le routage au niveau IP.

Pour que 2 hôtes (machines connectées) communiquent :

- Ils doivent utiliser le même protocole ;
- **Ils doivent appartenir au même sous-réseau** ;
- Chaque hôte doit connaître l'adresse IP de l'autre.

**La passerelle permet la communication entre deux sous réseaux**

On parle aussi de passerelle par défaut, de passerelle applicative ou de passerelle logique. Tous ces termes sont synonymes.

Une passerelle est un autre ordinateur qui a plusieurs cartes réseau (en général, c'est un routeur). Cet ordinateur peut communiquer avec plusieurs sous-réseaux.

Un hôte communique avec la passerelle par défaut selon l'architecture client-serveur.

### Qu’est-ce qu’un port d’un point de vue IP et comment cela est utilisé pour se connecter à un autre appareil

- 0 à 1023 : Controlés et assignés par l'IANA, appelés Well Known Ports
- 1024 à 49156 : Ports enregistrés
- 49152 à 65535 : Ports dynamiques

Une adresse IP + un port = un socket : Chemin par lequel transitent des paquets
