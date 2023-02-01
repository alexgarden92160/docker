# Docker
## Workshop Docker

### Installation
Avant de commencer ce workshop vous devez d'abord **installer Docker** en suivant les indications sur le site officiel en [cliquant ici](https://docs.docker.com/engine/install/).

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

Pour tester cet exercice, vous pouvez **executer en interaction bash sur le conteneur** et taper la commande "**env**".
Celle-ci afficher toutes les variables d'environnement et vous deviez trouver celle que vous venez de créer.

### Exercice 5 - Variables d'environnement
Pour ce cinquième exercice, vous devez refaire l'exercice précedent mais cette fois avec **un fichier d'environnement (fichier.env)** ou vous avec juste à mettre le nom de la variable et sa valeur (Exemple : **MYVARIABLE="123456"**).

Pour tester, même chôse aussi que l'exercice précédent.

### Exercice 6 - Dockerfile
Dans cet exercice, il faudra créer sa propre image Docker en créer un **fichier "Dockerfile"** et avec les **caractéristiques** suivantes :

  - A partir de la dernière version de l'**image ubuntu**
  - Executer apt-get update
  - Installer git

Ensuite il faut que vous contruisiez cette image avec pour nom "test" et version "1.0".
Enfin créer un conteneur a partir de l'image que vous avez créer "test".

Pour tester cet exercice, **executer en interaction bash sur le conteneur et tester une commande git**.
