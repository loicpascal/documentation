[MarkdownPreview](https://facelessuser.github.io/MarkdownPreview/usage/ "MarkdownPreview")  
[Markdown](https://fr.wikipedia.org/wiki/Markdown#Quelques_exemples "Markdown")

#Commandes Git  

**Sommaire**

* [Gérer un dépôt](#gerer-un-depot)
    * [Aide en ligne de commande](#aide-en-ligne-de-commande)
    * [Initialiser un nouveau dépôt](#initialiser-un-nouveau-depot)
    * [Cloner un dépôt](#cloner-un-depot)
    * [Configurer un dépôt](#configurer-un-depot)
* [Enregistrer des changements](#enregistrer-des-changements)
    * [git add](#git-add)
    * [git commit](#git-commit)
    * [git diff](#git-diff)
    * [git stash](#git-stash)
    * [.gitignore](#gitignore)
* [Inspecter un dépôt](#inspecter-un-depot)
    * [git status](#git-status)
    * [git log](#git-log)
    * [git blame](#git-blame)
    * [git show](#git-show)
* [Annuler des changements](#annuler-des-changements)
    * [git reset](#git-reset)
    * [git checkout](#git-checkout)
    * [git revert](#git-revert)
* [Réécrire l'historique](#reecrire-lhistorique)
    * [git commit](#git-commit_1)
    * [git cherry-pick](#git-cherry-pick)
* [Gestion des branches](#gestion-des-branches)
    * [Créer une nouvelle branche](#creer-une-nouvelle-branche)
    * [Pousser une nouvelle branche sur le serveur](#pousser-une-nouvelle-branche-sur-le-serveur)
    * [Changer de branche](#changer-de-branche)
    * [Mettre à jour la branche](#mettre-a-jour-la-branche)
    * [Lister les branches](#lister-les-branches)
    * [Supprimer une branche](#supprimer-une-branche)
    * [Trouver la branche qui contient un commit spécifique](#trouver-la-branche-qui-contient-un-commit-specifique)
    * [Merger une branche A dans une branche B](#merger-une-branche-a-dans-une-branche-b)
* [Commandes EOLAS](#commandes-eolas)
    * [Supprimer toutes les branches de suivi fusionnées qui ont été supprimées sur le distant](#supprimer-toutes-les-branches-de-suivi-fusionnees-qui-ont-ete-supprimees-sur-le-distant)
    * [Forcer la suppression de toutes les branches de suivi locales qui ont été supprimées sur le distant](#forcer-la-suppression-de-toutes-les-branches-de-suivi-locales-qui-ont-ete-supprimees-sur-le-distant)
* [Cas pratiques](#cas-pratiques)
    * [Livrer des commits de la branche master quand la branche production a des commits d'avance](#livrer-des-commits-de-la-branche-master-quand-la-branche-production-a-des-commits-davance)


##Gérer un dépôt

###Aide en ligne de commande
```git
git help [nom_de_la_commande]
```

###Initialiser un nouveau dépôt
```git
git init
```

###Cloner un dépôt
```git
git clone <repo_url>
```

###Configurer un dépôt

**Configurer son mail**
```git
git config --global user.email "your_email@example.com"
```
**Configurer son éditeur de texte**
```git
git config --global core.editor "vim"
```
**Configurer ses alias**
```git
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```
**Lister les config globales**
```git
git config --list
```

<br/><br/>

##Enregistrer des changements

###git add

**Ajouter un fichier à l'index**
```git
git add <file>
```

**Ajouter un répertoire à l'index**
```git
git add <directory>
```

**Ajouter tous les fichiers à l'index**
```git
git add .
```

<br/>

###git commit

**Faire un commit avec un message**
```git
git commit -m "commit message"
```

**Ajouter tous les fichiers déjà trackés et fais un commit avec un message**
```git
git commit -am "commit message"
```

**Modifier le message du dernier commit**
```git
git commit --amend
```

<br/>

###git diff

**Voir les différences entre le contenu du répertoire de travail et celui de l'index**
```git
git diff
```

**Voir les différences entre le contenu de l'index et celui du dernier commit**
```git
git diff --cached
```

**Voir les différences entre deux commits**
```git
git diff <commit_1> <commit_2>
```

<br/>

###git stash

**Mettre les changements de côté**
```git
git stash
git stash -u                            # Inclue les fichiers untracked
git stash save "WIP <message>"          # Avec un message
```

**Lister les stashs enregistrés**
```git
git stash list
```

**Réintégrer le dernier stash dans le répertoire de travail et dans l'index**
```git
git stash apply
git stash pop                           # Et supprime le stash
git stash apply|pop stash@{0}           # Un stash en particulier
```

**Visualiser le contenu d'un stash**
```git
git stash show stash@{0}
```

**Supprimer les stashs**
```git
git stash clear
git stash drop stash@{0}                # Un stash en particulier
```

<br/>

###.gitignore

[.gitignore](https://www.atlassian.com/fr/git/tutorials/saving-changes/gitignore ".gitignore")

<br/><br/>

##Inspecter un dépôt

###git status

**Afficher l'état des fichiers**
```git
git status
```

<br/>

###git log

**Afficher la liste des commits**
```git
git logs                                # Tous les commits
git logs -3                             # Les 3 derniers commits
git logs --oneline                      # Chaque commit sur une seule ligne
git logs --stat                         # Pour chaque commit quels fichiers ont été modifiés
git logs -p                             # Les différences pour chaque fichier
git log --author="<pattern>"            # Pour une personne en particulier
git log --grep="<pattern>"              # Selon leur message
git log <file>                          # Pour un fichier en particulier
git log --graph --decorate --oneline    # Sous forme de graph
```

<br/>

###git blame

**Afficher qui a modifié quoi**
```git
git blame <fichier>
git blame -L 1,5 README.md              # Restreindre sur un ensemble de lignes
```

<br/>

###git show

**Voir le contenu exact d'un commit**

```git
git show <commit>
```

**Voir le contenu exact d'un commit pour un fichier donné**

```git
git show <commit> <nom_du_fichier>
```

<br/><br/>

##Annuler des changements

###git reset

**Annuler le dernier commit**
```git
git reset HEAD^                         # Revient à revenir à l'avant-dernier commit

OU

git reset HEAD~1
```

**Revenir à l'avant-avant-dernier commit**
```git
git reset HEAD^^

OU

git reset HEAD~2
```

**Revenir à un commit précis**
```git
git reset d6d9892
```

Avec un `reset HEAD`, seuls les commit sont supprimés. Les modifications elles, restent en place.

**Annuler tous les changements du dernier commit**
```git
git reset --hard HEAD^
```

**Annuler tous les changements sur le dépôt local**
```git
git reset --hard
```

**Remettre l'état d'une branche locale dans le même état que sur le dépôt distant (forcer)**
```git
git reset --hard origin/<branch>
```
Attention, supprime les changements locaux et les commits non pushed

###git checkout

**Annuler les modifications d'un fichier avant un commit**
```git
git checkout <nom_fichier>
```

###git revert

**Annuler un commit en créant un nouveau commit contenant les changements inverses**
```git
git revert <commit>
```

**Annuler un commit en appliquant les changements inverses sans créer de commit**
```git
git revert -n <commit>
```

<br/><br/>

##Réécrire l'historique

###git commit

**Changer le dernier commit**
```git
git commit --amend -m "mon nouveau message"
```

###git cherry-pick

**Appliquer un commit à la branche courante**
```git
git cherry-pick <commit>
```

L'option `-edit` permet de saisir un message pour le commit  
L'option `--no-commit` applique seulement les modifications sans créer un nouveau commit

<br/><br/>

##Gestion des branches

###Créer une nouvelle branche

**Créer une branche simple**
```git
git checkout <branch> <source_branch>
```

**Créer une branche et passer dessus**
```git
git checkout -b <branch> <source_branch>
```

###Pousser une nouvelle branche sur le serveur

```git
git push -u origin <branch>
```
`-u` est le raccourci pour `--set-upstream`

###Changer de branche

```git
git checkout <branch>
```

###Mettre à jour la branche

Se placer sur la branche avec `git checkout <branch>` puis executer la commande suivante.

```git
git pull
```

###Lister les branches

**Du dépôt local**
```git
git branch
```

**Du dépôt distant**

```git
git branch -r
```

###Supprimer une branche

```git
git branch -D <branch>
```

###Trouver la branche qui contient un commit spécifique

```git
git branch -a --contains <commits>
```

###Merger une branche A dans une branche B

```git
git co <branch-B>           # Se rendre sur la branche cible
git pull                    # S'assurer que la branche cible est à jour
git merge <branch-A>        # Merger la branche A dans la branche B
```

<br/><br/>

##Commandes EOLAS

###Supprimer toutes les branches de suivi fusionnées qui ont été supprimées sur le distant

```git
git branch-cleanup
```
Alias de `git fetch -p && LANG=en_US git branch -vv --merged | awk '/: gone]/{print $1}' | xargs -rn 1 git branch -d`

###Forcer la suppression de toutes les branches de suivi locales qui ont été supprimées sur le distant

```git
git branch-cleanup-force
```
Alias de `git fetch -p && LANG=en_US git branch -vv | awk '/: gone]/{print $1}' | xargs -rn 1 git branch -D`

###Rebaser une branche fille depuis sa branche mère

```git
git co <branch-mere>
git pull
git co <branch-fille>
git update-from origin <branch-mere>
git push --force origin <branch-fille>
```

Si `git update-from origin <branch-mere>` ne fonctionne pas, utiliser la commande `git pull --rebase origin <branch-mere>`


<br/><br/>

##Cas pratiques

###Livrer des commits de la branche master quand la branche production a des commits d'avance

Parfois, une merge request de la master vers la production peut poser problème si la production a des commits d'avance (il nous est alors demander de rebaser).  
Parfois aussi, un cherry-pick du commit qu'on vient de merger sur la master vers la production est aussi bloqué.  
Il faut alors traiter le problème en local.  

* Créer une branche depuis la branche de production
* Faire un cherry-pick du commit sur cette nouvelle branche
* Puis sur le dépôt, faire une MR classique de cette branche vers la branche production

```git
git co -b <branch-fille> <branch-mere>
git cherry-pick <commit>
git push
```