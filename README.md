# Docker Get Started

Ce dépôt contient le détail de ma présentation, les slides et les sources utilisées pour les démonstrations.

URL vers les slides : [http://bunkrapp.com/present/zd6wmq/?utm_medium=share][8]

## Installation de Docker avec Debian 8 Jessie

Ajout de la clef GPG :

	apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

Ajout du dépôt dans sources.list :

	echo "deb https://apt.dockerproject.org/repo debian-jessie main" > /etc/apt/sources.list.d/docker.list

On update la liste des paquets et on installe docker

	apt-get update
	apt-get install docker-engine

## Déploiement d’une stack Wordpress
Le détail de cette stack ici : [Wordpress.md][1]

## L’univers autour de Docker

- [Dockerfile][2] : C’est un fichier qui contient les instructions pour compiler une image Docker
- [Docker Compose][3] : Outil pour lancer de multiples conteneurs, basé sur un simple fichier YAML
- [Docker Registry][4] : Créez votre propre dépôt privé pour vos images Docker
- [Docker Machine][5] : Création d’hôtes Docker en local ou dans le cloud ou vos propres serveurs
- [Docker Cloud][6] (ex: Tutum) : Les avantages de Docker Compose / Machine dans une interface moderne performante et entièrement monitorée ( avantage : Officiel )
- [Rancher/RancherOS][7] : Similaire à Docker Cloud, projet très prometteur ( avantage : Open Source )

[1]:	Wordpress.md
[2]:	https://docs.docker.com/v1.8/reference/builder/
[3]:	https://docs.docker.com/compose/
[4]:	https://docs.docker.com/registry/
[5]:	https://docs.docker.com/machine/
[6]:	https://cloud.docker.com/
[7]:	http://rancher.com/
[8]:	http://bunkrapp.com/present/zd6wmq/?utm_medium=share