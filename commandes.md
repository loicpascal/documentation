
# Commandes Git

## Commencement

### Initialiser un nouveau dépôt
```git
git init
```

### Initialiser un nouveau dépôt
```git
git init
```

## Configuration

### Aide en ligne de commande
```git
git help [nom_de_la_commande]
```

### Lister les configs globales
```git
git config --list
```

<br/><br/>

## git commit

**Modifier le message du dernier commit**

```git
git commit --amend
```

**Annuler le dernier commit** (revient à revenir à l'avant-dernier commit)

```git
git reset HEAD^
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

**Annuler les modifications d'un fichier avant un commit**

```git
git checkout nom_fichier
```

<br/><br/>

## Gestion des branches

### Créer une nouvelle branche

**Créer une branche simple**
```git
git checkout <branch> <source_branch>
```

**Créer une branche et passer dessus**
```git
git checkout -b <branch> <source_branch>
```

### Pousser une nouvelle branche sur le serveur

```git
git push -u origin <branch>
```
`-u` est le raccourci pour `--set-upstream`

### Changer de branche

```git
git checkout <branch>
```

### Mettre à jour la branche

Se placer sur la branche avec `git checkout <branch>` puis executer la commande suivante.

```git
git pull
```

### Lister les branches

**Du dépôt local**
```git
git branch
```

**Du dépôt distant**

```git
git branch -r
```

### Supprimer toutes les branches de suivi fusionnées qui ont été supprimées sur le distant

```git
git branch-cleanup
```
Alias de `git fetch -p && LANG=en_US git branch -vv --merged | awk '/: gone]/{print $1}' | xargs -rn 1 git branch -d`

### Forcer la suppression de toutes les branches de suivi locales qui ont été supprimées sur le distant

```git
git branch-cleanup-force
```
Alias de `git fetch -p && LANG=en_US git branch -vv | awk '/: gone]/{print $1}' | xargs -rn 1 git branch -D`

<br/><br/>

## Exploration

### git log

**Affiche les logs des commit de la branche courante**

```git
git log
```

**Affiche les logs des commit de la branche courante pour un fichier donné**

```git
git log <nom_du_fichier>
```

### git blame

**Affiche quel commit et qui a modifié chaque ligne du fichier**

```git
git blame <nom_du_fichier>
```

### git show

**Voir le contenu exact d'un commit**

```git
git show <commit>
```

**Voir le contenu exact d'un commit pour un fichier donné**

```git
git show <commit> <nom_du_fichier>
```