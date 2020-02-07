
# Commandes Git

## Configuration

### Aide en ligne de commande
```git
git help [nom_de_la_commande]
```

### Lister les configs globales
```git
git config --list
```

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