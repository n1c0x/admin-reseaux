<head><link rel="stylesheet" type="text/css" href="style.css"></head>

<!-- https://www.juniper.net/techpubs/en_US/junos15.1/topics/task/configuration/root-password.html -->

# Configuration de Routeur Juniper

## Introduction
Juniper est le deuxième constructeur mondial de matériel réseau. Il représente une part de marché d'environ 15% [1]. Juniper conçoit et vend du matériel réseau comme des routeurs, des switchs, des passerelles de sécurité (VPN, pare-feu) ainsi que du support pour ses produits [2].

## Connexion
Pour accéder à la console de l'équipement réseau, il faut tout d'abord se connecter au port série de celui-ci en utilisant un programme adapté comme PuTTY. Il faut ensuite utiliser les paramètres suivants:

* 9600 bauds
* 8 bits de données
* aucune parité
* 1 bit de stop
* pas de contrôle de flux

Ensuite seulement, l'équipement peut être mis en route. Lorsqu'il est démarré, un premier identifiant est demandé. Celui-ci est `root` et ne requiert pas de mot de passe.
A l'invite de commande, il suffit de taper la commande `cli` et d'appuyer sur la touche `Enter` pour accéder au mode opérationnel de ligne de commande (CLI operational mode). L'invite de commande passe alors de `root@#` à `cli`

## Configuration de base
Pour rentrer dans le mode de configuration de l'équipement, il faut taper la commande `configure`. 

### Mot de passe root
Un mot de passe root doit être configuré afin de protéger l'accès à l'équipement. Celui-ci doit respecter plusieurs conditions:

* Il doit être long de six caractères au minimum. La plupart des classes de caractères peut être utilisée: alphabétiques, numérique et caractères spéciaux.
* Il doit contenir au moins un changement de casse de caractère (majuscule et minuscule) ou de classe de caractère.

La configuration du mot de passe root s'effectue comme suit: 
	
	root@# set root-authentication plain-text-password
	New Password: taper le mot de passe
	Retype new password: confirmer le mot de passe

Il est également possible de n'autoriser qu'un accès root via le port console (aucun autre utilisateur ne sera autorisé à se connecter via le port console):

	root@# set services ssh root-login deny

### Hostname
Le hostname est une chaîne de caractères qui permet d'identifier l'équipement  de manière unique sur le réseau.

## Bibliographie
1: http://www.forbes.com/sites/greatspeculations/2015/09/10/how-can-juniper-curb-the-declines-in-its-router-market-share/#790ad1a07278
2: http://www.trefis.com/stock/jnpr/model/trefis?easyAccessToken=PROVIDER_b980e77d38293d7ed41f15fc5b26fb649f476b68