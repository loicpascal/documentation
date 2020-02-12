#Commandes Linux  

**Sommaire**

* [Commandes courantes](#commandes-courantes)
* [Crontab](#crontab)
* [Vim](#vim)

##Commandes courantes

###Nettoyer le terminal
```git
Ctrl + L (ou clear)
```

###Afficher l'aide d'une commande
```git
man <commande>
```

###Afficher le répertoire courant
```git
pwd
```

###Afficher le répertoire courant
```git
ls
ls -l 		Afficher les détails pour chaque fichier
ls -a 		Afficher les fichiers cachés
```

###Changer de répertoire
```git
cd <directory>
```

###Créer un répertoire
```git
mkdir <directory>
```

###Supprimer un répertoire
```git
rmdir <directory>
```

###Créer un fichier
```git
touch <filename>
```

###Copier un fichier ou un répertoire
```git
cp <old_name> <new_name>
```

###Renommer un fichier
```git
mv <old_name> <new_name>
```

###Renommer un fichier
```git
rm -f <filename|directory>
```

###Afficher le contenu d'un fichier
```git
cat <filename>
```

###Enregistrer la sortie d'une commande dans un fichier
```git
cat filename > other_filename		# Ecrase le contenu
cat filename >> other_filename		# Ajoute le contenu à la fin du fichier
```

<br><br>

##Crontab

###Afficher la crontab
```git
crontab -l
```

###Exporter la crontab dans un fichier
```git
crontab -l > mon_fichier
```

###Editer la crontab (avec vim)
```git
crontab -e
```

<br><br>

##Vim

###Changer de mode
```git
i 			Passer en mode édition/insertion
Escp 		Passer en mode commande
```

###Enregistrer et quitter
```git
:w 							Enregistrer sans quitter
:w <chemin vers fichier> 	Enregistrer sous
:x ou :wq 					Enregistrer et quitter
:q 							Quitter
:q! 						Quitter en ignorant les modifications
```

###Se déplacer dans le fichier
```git
:1 			Aller à la première ligne
:10 		Aller à la ligne 10
:$ 			Aller à la fin du fichier
$ 			Placer le curseur à la fin d'une ligne
```

###Copier / couper / coller
```git
yy 			Copier une ligne
dd 			Couper ou supprimer une ligne
p 			Coller
```

###Annuler / Refaire une action
```git
u 			Annuler
. 			Refaire une action
```

###Rechercher
```git
/test		Rechercher le mot "test"
?test		Rechercher le mot "test" vers le haut
n 			Occurence suivante
? enter		Occurence précédente
```