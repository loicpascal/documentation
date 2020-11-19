#Commandes Linux  
[Doc Ubuntu - Commandes de base](https://doc.ubuntu-fr.org/tutoriel/console_commandes_de_base "Doc Ubuntu - Commandes de base")

**Sommaire**

* [Commandes courantes](#commandes-courantes)
* [Droits](#droits)
* [Crontab](#crontab)
* [Vim](#vim)

##Commandes courantes

###Nettoyer le terminal
```
Ctrl + L (ou clear)
```

###Afficher l'aide d'une commande
```
man <commande>
```

###Afficher l'historique des commandes lancées
```
history
history 20                          # Affiche les 20 dernières commandes
history | grep -i <search> | less   # Affiche les 10 dernières commandes filtrées sur un mot clé
```

###Recherche dans l'historique
```
Ctrl + R
```

###Afficher le répertoire courant
```
pwd
```

###Afficher le répertoire courant
```
ls
ls -l       # Affiche les détails pour chaque fichier
ls -a       # Affiche les fichiers cachés
```

###Afficher la hiérarchie du répertoire courant
```
tree        # Affiche les sous-répertoires et les fichiers qui s'y trouvent
tree -d     # Affiche les répertoires uniquement
```

```
Avec l'option -l, le premier caractère indique :
- : fichier classique
d : répertoire
l : lien symbolique
```

###Changer de répertoire
```
cd <directory>
```

###Créer un répertoire
```
mkdir <directory>
```

###Supprimer un répertoire
```
rmdir <directory>
```

###Créer un fichier
```
touch <filename>
```

###Copier un fichier ou un répertoire
```
cp <old_name> <new_name>
```

###Renommer un fichier
```
mv <old_name> <new_name>
```

###Supprimer un fichier
```
rm -f <filename|directory>
```
`-f` force la suppression

###Afficher le contenu d'un fichier
```
cat <filename>          # Affiche tout le fichier
tail <filename>         # Affiche les 10 dernières lignes d'un fichier
tail -20 <filename>     # Affiche les 20 dernières lignes d'un fichier
tail -f <filename>      # Affiche les 10 dernières lignes d'un fichier puis les lignes suivantes automatiquement lorsque le fichier est modifié
```

###Enregistrer la sortie d'une commande dans un fichier
```
cat filename > other_filename       # Ecrase le contenu
cat filename >> other_filename      # Ajoute le contenu à la fin du fichier
```

###Localiser un fichier
```
locate <filename>
```

<br><br>

##Droits
[Doc Ubuntu - Droits](https://doc.ubuntu-fr.org/droits "Doc Ubuntu - Droits")
[Doc Ubuntu - Permissions](https://doc.ubuntu-fr.org/permissions "Doc Ubuntu - Permissions")

###Visualiser les droits des fichiers d'un répertoire
```
ls -l <directory>
```

***Exemple***
```
drwxrwx---+ 2 loic.pascal utilisateurs du domaine 4096 févr. 26 16:16
-rwxrwxr--+ 1 loic.pascal utilisateurs du domaine 1160 févr. 26 15:56 participationBO.js
```

Le `d` en début de ligne signifie qu'il s'agit d'un répertoire.  
Le `l` en début de ligne signifie qu'il s'agit d'un lien.  

```
1er groupe  : -rwx------ Propriétaire
2ème groupe : ----rwx--- Groupe
3ème groupe : -------rwx Public (autres utilisateurs)

r = read (lire)
w = write (écrire)
x = execute (executer) 
```

###Modifier les droits d'un fichier
***Avec chmod en gérant chaque droit séparément***

1. À qui s'applique le changement :

* u (user, utilisateur) représente la catégorie "propriétaire"
* g (group, groupe) représente la catégorie "groupe propriétaire"
* o (others, autres) représente la catégorie "reste du monde"
* a (all, tous) représente l'ensemble des trois catégories

2. La modification que l'on veut faire :

* '+' : ajouter
* '-' : supprimer
* '=' : affectation

3. Le droit que l'on veut modifier

* r : read ⇒ lecture
* w : write ⇒ écriture
* x : execute ⇒ exécution
* X : eXecute ⇒ exécution, concerne uniquement les répertoires

```
chmod o-w <filename>        # Supprime le droit d'écriture pour les autres
chmod a+x <filename>        # Ajoute le droit d'éxecution à tout le monde
chmod a+rx,g-w <filename>   # Ajoute le droit de lecture et d'éxecution à tout le monde et supprime le droit d'écriture au groupe
```

***Avec chmod en octal***
```
chmod 755 <filename>        # Pour un fichier
chmod -R 755 <directory>    # Pour un répertoire
```

```
"4" pour le droit de lecture (read)
"2" pour le droit d'écriture (write)
"1" pour le droit d'exécution (execute)

Donc :

0 : - - - (aucun droit)
1 : - - x (exécution)
2 : - w - (écriture)
3 : - w x (écriture et exécution)
4 : r - - (lecture seule)
5 : r - x (lecture et exécution)
6 : r w - (lecture et écriture)
7 : r w x (lecture, écriture et exécution)
```

###Modifier le propriétaire et le groupe d'un fichier
Il faut être root pour pouvoir faire ce changement.
```
sudo chown <user> <file|directory>		 		 # Modifie l'utilisateur uniquement
sudo chgrp <group> <file|directory>		 		 # Modifie le groupe uniquement
sudo chown <user>:<group> <file|directory>		 # Modifie l'utilisateur et le groupe
sudo chown -R <user>:<group> <directory>         # Récursif
```

###Lister les groupes de l'utilisateur connecté
Le premier groupe de la liste de résultats est le groupe principal de l'utilisateur
```
groups
```

###Lister les groupes d'un utilisateur
```
groups <username>
```

###Lister les membres d'un groupe
```
getent group <groupname>
```

###Lister tous les groupes
```
less /etc/group
```

<br><br>

##Crontab

###Afficher la crontab
```
crontab -l
```

###Exporter la crontab dans un fichier
```
crontab -l > mon_fichier
```

###Editer la crontab (avec vim)
```
crontab -e
```

<br><br>

##Vim

###Changer de mode
```
i           # Passer en mode édition/insertion
Escp        # Passer en mode commande
```

###Enregistrer et quitter
```
:w                          # Enregistrer sans quitter
:w <chemin vers fichier>    # Enregistrer sous
:x ou :wq                   # Enregistrer et quitter
:q                          # Quitter
:q!                         # Quitter en ignorant les modifications
```

###Se déplacer dans le fichier
```
:1          # Aller à la première ligne
:10         # Aller à la ligne 10
:$          # Aller à la fin du fichier
$           # Placer le curseur à la fin d'une ligne
```

###Copier / couper / coller
```
yy          # Copier une ligne
dd          # Couper ou supprimer une ligne
p           # Coller
```

###Annuler / Refaire une action
```
u           # Annuler
.           # Refaire une action
```

###Rechercher
```
/test       # Rechercher le mot "test"
?test       # Rechercher le mot "test" vers le haut
n           # Occurence suivante
? enter     # Occurence précédente
```