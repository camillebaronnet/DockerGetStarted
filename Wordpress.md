# Wordpress avec Docker

## Pré-requis

Dans tout les cas nous aurons besoin de [télécharger les images officielles][1] :

	docker pull mysql
	docker pull wordpress

## Deux méthodes pour notre stack

### 1. Manuellement, avec Docker Engine seul

Lancer les conteneurs :

	docker run --name db\_example\_com -e MYSQL\_ROOT\_PASSWORD=mypassword -d mysql
	docker run --name example\_com -p 80:80 -d wordpress

### 2. Avec Docker Compose

La même chose avec [Docker Compose][2], on créer un fichier **docker-compose.yml**. On en profite pour lier les données Wordpress et MySQL à l'extérieur du conteneur :

	app:
	  image: wordpress
	  ports:
	    - 80:80
	  links:
	    - db:mysql
	  volumes:
	    - ./html:/var/www/html
	    - ./log:/var/log
	
	db:
	  image: mysql
	  environment:
	    MYSQL_ROOT_PASSWORD: mysuperpassword
	  volumes:
	    - ./db:/var/lib/mysql

On démarre notre stack en background ( -d ) avec :

	docker-compose up -d

## Gestion des Vhosts

En créant un conteneur, le réseau de celui-ci est indépendant et séparé de la machine hôte, à ce compte la gestion des vhosts ne peux pas se faire au sein du conteneur.

Nous devons donc créer un conteneur ( pour les gouverner tous ) qui sera lié à chaque conteneur exposant son port 80.

La solution c’est le reverse proxy ( avec Nginx par exemple ). Vous pouvez utiliser le Docker Nginx officiel et écrire votre propre fichier de configuration, ou bien, utilisez l’image de [jwilder/nginx-proxy][3] qui créer une configuration dynamique et automatique pour Nginx.

[1]:	https://hub.docker.com/r/library/
[2]:	https://docs.docker.com/compose/compose-file/
[3]:	https://hub.docker.com/r/jwilder/nginx-proxy/