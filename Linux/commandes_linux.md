#Commandes Linux  

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
history 20							# Afficher les 20 dernières commandes
history | grep -i <search> | less	# Afficher les 10 dernières commandes filtrées sur un mot clé
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
ls -l 		# Afficher les détails pour chaque fichier
ls -a 		# Afficher les fichiers cachés
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
cat <filename>			# Affiche tout le fichier
tail <filename>			# Affiche les 10 dernières lignes d'un fichier
tail -20 <filename>		# Affiche les 20 dernières lignes d'un fichier
tail -f <filename>		# Affiche les 10 dernières lignes d'un fichier puis les lignes suivantes automatiquement lorsque le fichier est modifié
```

###Enregistrer la sortie d'une commande dans un fichier
```
cat filename > other_filename		# Ecrase le contenu
cat filename >> other_filename		# Ajoute le contenu à la fin du fichier
```

<br><br>

##Droits

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
```
chmod 755 <filename> 		# Pour un fichier
chmod -R 755 <filename> 	# Pour un répertoire
```

```
"4" pour le droit de lecture (read)
"2" pour le droit d'écriture (write)
"1" pour le droit d'exécution (execute)
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
i 			# Passer en mode édition/insertion
Escp 		# Passer en mode commande
```

###Enregistrer et quitter
```
:w 							# Enregistrer sans quitter
:w <chemin vers fichier> 	# Enregistrer sous
:x ou :wq 					# Enregistrer et quitter
:q 							# Quitter
:q! 						# Quitter en ignorant les modifications
```

###Se déplacer dans le fichier
```
:1 			# Aller à la première ligne
:10 		# Aller à la ligne 10
:$ 			# Aller à la fin du fichier
$ 			# Placer le curseur à la fin d'une ligne
```

###Copier / couper / coller
```
yy 			# Copier une ligne
dd 			# Couper ou supprimer une ligne
p 			# Coller
```

###Annuler / Refaire une action
```
u 			# Annuler
. 			# Refaire une action
```

###Rechercher
```
/test		# Rechercher le mot "test"
?test		# Rechercher le mot "test" vers le haut
n 			# Occurence suivante
? enter		# Occurence précédente
```