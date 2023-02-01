# Docker
## Workshop Docker

### Installation
Avant de commencer ce workshop vous devez d'abord **installer Docker** en suivant les indications sur le site officiel en [cliquant ici](https://docs.docker.com/engine/install/).

Et **Docker Compose** en [cliquant ici](https://docs.docker.com/compose/install/other/).

### Documentation
[Docker CLI](https://docs.docker.com/engine/reference/run/)         
[Docker Image](https://docs.docker.com/engine/reference/builder/)
[Docker Compose](https://docs.docker.com/compose/compose-file/compose-file-v3/)

### Exercie 1 - Lancer un conteneur
Pour ce premier exercice, vous devez **lancer un conteneur Docker avec la CLI** (command line interface).          
**Les caractérisques** que doit avoir le conteneur sont celles-ci :

  - La dernière version de l'**image nginx**
  - Un port forwarding du **port 80 du conteneur** vers -> le **port 8080 du host**
  - Un **nom "web"**

Pour tester votre exercice, ouvrez un **navigateur** puis rendez-vous sur **localhost:8080**.

### Exercice 2 - Monter un volume persistant
Pour ce deuxième exercice, vous devez aussi **lancer un conteneur Docker avec la CLI**.       
**Les caractéristiques** :

  - La dernière version de l'**image nginx**
  - Un port forwarding du **port 80 du conteneur** vers -> le **port 8080 du host**
  - Un **nom "web"**
  - Un volume monté d'un **dossier "src"** local contenant un **ficher "index.html"** personnalisé vers le répertoire **/usr/share/nginx/html/ du conteneur**

Pour tester cet exercice, vous pouvez donc créer votre conteneur, vous rendre sur **localhost:8080 de votre navigateur**, supprimer ce conteneur puis recommencer cet exercice. Vous devriez constater que l'affichage est le même.

### Exercice 3 - Monter un volume persistant 2
Pour ce troisième exercice, vous devez **créer un volume docker** puis lancer un conteneur avec la CLI avec les **même caractéristiques** que l'exercice 2 mais cette fois-ci, vous devez **monter le volume** que vous avez créer sur le répertoire **/usr/share/nginx/html/ du conteneur**.

### Exercice 4 - Variables d'environnement
Pour ce quatrième exercice, vous devez **lancer un conteneur Docker avec la CLI**.          
**Les caractéristiques** :

  - La dernière version de l'**image ubuntu**
  - Un **nom "testenv"**
  - Une variable d'environnement avec comme nom "**MYVARIABLE**" et comme valeur **"123456"**
  - En mode **interaction et détacher**

Pour tester cet exercice, vous pouvez **executer en interaction bash sur le conteneur** et taper la commande "**env**".
Celle-ci afficher toutes les variables d'environnement et vous deviez trouver celle que vous venez de créer.

### Exercice 5 - Variables d'environnement
Pour ce cinquième exercice, vous devez refaire l'exercice précedent mais cette fois avec **un fichier d'environnement (fichier.env)** ou vous avec juste à mettre le nom de la variable et sa valeur (Exemple : **MYVARIABLE="123456"**).

Pour tester, même chôse aussi que l'exercice précédent.

### Exercice 6 - Dockerfile
Dans cet exercice, il faudra créer sa propre image Docker en créer un **fichier "Dockerfile"** et avec les **caractéristiques** suivantes :

  - A partir de la dernière version de l'**image ubuntu**
  - Executer **apt-get update**
  - **Installer nginx**
  - Définir un **espace de travail** à **/var/www/html/**
  - Copier un fichier **index.html** que vous avez localement créer vers cet espace
  - **Exposer** le **port 80**
  - Définir un **entrypoint "nginx"**
  - Définir des **cmd "-g" et "daemon off;"**

Ensuite il faut que vous contruisiez cette image avec pour nom "test" et version "1.0".
Enfin créer un conteneur a partir de l'image que vous avez créer "test" en mode détacher et mapper les port 80 du conteneur vers 8080 du host.

Pour tester cet exercice, rendez vous sur un **navigateur** puis sur **localhost:8080**.

### Exercice 7 - Microservices
Dans cet exercice, il faut tout d'abord créer un network avec comme nom "my_network" (avec la CLI).
Ensuite il faudra créer un **conteneur** en mode détacher avec comme **image redislabs/redismod**,
comme **nom "redis"** et comme **réseau "my_network"**.
Après cette étape il faut créer un **Dockerfile** avec ces **caractéristiques**:
  
  - L'**image** de base **"node:14.17.3-alpine3.14"**
  - L'**espace de travail** situer sur **/usr/src/app**
  - **Copier package.json, package-lock.json et server.js** dans cet espace
  - **Executer "npm ci"**
  - Avoir comme **entrypoint** du conteneur **"npm"** et comme **argument "start"**

**Construisez cette image** avec comme **nom "web-images"** et enfin **créer un conteneur** en **mode détacher** avec comme **nom "web"**, comme **hostname "conteneur"**, comme **réseau "my_network"** et avec un **mapping des ports** **5000 du conteneur** vers le **80 de l'host**.

Testez votre exercice en executant sur un terminal de votre machine **"curl localhost"** ou en vous rendant sur un **navigateur a l'adresse localhost**.

### Exercice 8 - Docker-Compose
Cette fois-ci il vous faut créer un fichier docker-compose.yml avec 2 services et 1 réseau.                                    
Vous devez reprendre les caractéristiques du précédent exercice.

Testez cette fois-ci votre exercice avec la commande "docker-compose up -d" puis rendez-vous sur le localhost comme pour l'exercice précédent.

### Exercice 9 - Docker-compose 2
Pour ce dernier exercice vous devez donc avoir :                                         

**1 volume** qui doit avoir pour **nom "db_data"**

**1 réseau** qui doit avoir pour nom **"app_network"**

**2 services**                                     
Le **premier service** avec pour **nom "db"**
  
  - Se base sur la **dernière version** de l'**image mysql**
  - **Monter** sur un **volume** créer avec pour **nom "db_data"** sur le **chemin /var/lib/mysql/ du service**
  - Le conteneur doit **toujours redémarrer**
  - Doit avoir 4 **variable d'environnement** **MYSQL_ROOT_PASSWORD**, **MYSQL_DATABASE**, **MYSQL_USER** et **MYSQL_PASSWORD** qui ont toutes pour valeur **"wordpress"**
  - Doit avoir comme **réseau "app_network"**

Le **deuxième service** avec pour **nom "web"**

  - Se base sur la **dernière version** de l'**image de wordpress**
  - Un **mapping** de **port de 80 du conteneur** vers le **80 de l'host**
  - Le conteneur doit **toujours redémarrer**
  - **Dépend du service "db"**
  - Doit avoir comme **réseau "app_network"**
  - Doit avoir 4 **variables d'environnement** **WORDPRESS_DB_HOST** qui vaut **"db"**, **WORDPRESS_DB_USER**, **WORDPRESS_DB_PASSWORD**, **WORDPRESS_DB_NAME** qui ont toutes pour **valeur : "wordpress"**
 
 Pour tester -> **"docker-compose up -d"** puis rendez-vous sur localhost dans un navigateur pour créer votre site !
