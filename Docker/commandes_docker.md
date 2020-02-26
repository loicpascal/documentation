#Commandes Docker  

**Sommaire**

* [Commandes PROJET](#commandes-projet)
* [Commandes CMS-EOLAS](#commandes-cms-eolas)
* [Commandes DOCKER](#commandes-docker)
* [Commandes TOOLS](#commandes-tools)

###Afficher la liste des commandes disponibles dans le Makefile
```
make
```

##Commandes PROJET

###Lance l'environnement de développement (avec une mise à jour du CMS)
```
make dev-start
```

###Arrête l'environnement de développement
```
make dev-stop
```

###Ajoute les permissions nécessaires à www-data et lance l'environnement de développement
```
make project-install
```

###Arrête l'environnement docker et supprime tous les fichiers non versionnés (⚠)
```
make project-install
```

###Lance une réinitialisation complète du projet (⚠ les fichiers non versionnés seront supprimés)
```
make project-reinstall
```

<br>

##Commandes CMS-EOLAS

###Met à jour le CMS
```
make cms-update
```

###Met à jour les signatures des modules du CMS
```
make cms-update-signatures
```

###Remet à parser tous les paragraphes
```
make cms-paragraphes_parse
```

###Sauvegarde la base de données
```
make cms-db-dump
```

###Copies les données de src/www/uploads vers .docker/data/cms/www/uploads
```
make uploads-update-data-tree
```

###Permet d'ignorer les changements Git apportés au sein du dossier .docker/data/cms/www/uploads/
```
make uploads-untrack
```

###Permet de suivre les changements Git apportés au sein du dossier .docker/data/cms/www/uploads/
```
make uploads-track
```

<br>

##Commandes DOCKER

###Lancer les conteneurs Docker
```
make docker-up
```

###Arrête les conteneurs Docker
```
make docker-down
```

###Arrête et supprime les conteneurs de manière rapide et forcée
```
make docker-kill
```

###Met à jour les images docker utilisées
```
make docker-pull
```

<br>

##Commandes TOOLS

###Ajoute les permissions nécessaires à www-data au sein de l'hôte Docker
```
make acl
```
