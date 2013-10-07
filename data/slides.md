# Comprendre
![git](http://git-scm.com/images/logos/downloads/Git-Logo-2Color.png "git")



## Concepts de base
+ Décentralisé
+ Rapide
+ Flexible

Note:
Inspiré par BitKeeper et créé en 2005 pour le remplacer après que la gratuité de ce dernier soit révoqué.



## Décentralisé
![schema decentralisé](http://git-scm.com/figures/18333fig0103-tn.png "schema VCS décentralisé")

(git, mercurial, bazaar, bitkeeper, darcs)


### Avantages
+ Chaque `clone` est un `fork`
+ Chaque `clone` est un backup
+ Possibilité de versionner hors ligne
+ **Très** rapide

---

### Inconvénients
+ Pas très performant pour les gros fichiers binaires

Note:
Chaque clone est un backup : a condition de maintenir a jour toutes les branches.



## Objectif de git
+ Rapidité
+ Simplicité
+ Prise en charge de milliers de branches parallèles
+ Architecture distribuée
+ Capable de gerer efficacement de gros projet *(ex:Le noyau Linux)*
+ Garantir l'intégrité

Note:
+ Git est rapide car presque toutes les opérations sont locale.
+ Git gère l'intégrité en utilisant des somme de contrôle (checksum ou hash) qui servent ensuite de référence.



## Les trois états
![schema 3 states](http://git-scm.com/figures/18333fig0106-tn.png "schema 3 states")

Note:
Cette notion est primordiale pour la compréhension de la suite.
Git gère trois états dans lesquels les fichiers peuvent résider : validé, modifié et indexé. 

+ Validé signifie que les données sont stockées en sécurité dans votre base de données locale. 
+ Modifié signifie que vous avez modifié le fichier mais qu'il n'a pas encore été validé en base. 
+ Indexé signifie que vous avez marqué un fichier modifié dans sa version actuelle pour qu'il fasse partie du prochain instantané du projet.

Ceci nous mène aux trois sections principales d'un projet Git : le répertoire Git, le répertoire de travail et la zone d'index.



## Le dossier git
![git directory](images/git-directory.png "git directory")

Note:
Le répertoire Git est l'endroit où Git stocke les méta-données et la base de données des objets de votre projet. C'est la partie la plus importante de Git, et c'est ce qui est copié lorsque vous clonez un dépôt depuis un autre ordinateur.

Le répertoire de travail est une extraction unique d'une version du projet. Ces fichiers sont extraits depuis la base de données compressée dans le répertoire Git et placés sur le disque pour pouvoir être utilisés ou modifiés.

La zone d'index est un simple fichier, généralement situé dans le répertoire Git, qui stocke les informations concernant ce qui fera partie du prochain instantané.



## Utilisation standard

![schema file lifecycle](http://git-scm.com/figures/18333fig0201-tn.png "schema file lifecycle")

1. Modifier des fichiers dans l'espace de travail
2. Indexer les fichiers modifiés
3. Valider les changements

Note:
L'utilisation standard de Git se passe comme suit :

+ vous modifiez des fichiers dans votre répertoire de travail ;
+ vous indexez les fichiers modifiés, ce qui ajoute des instantanés de ces fichiers dans la zone d'index ;
+ vous validez, ce qui a pour effet de basculer les instantanés des fichiers de l'index dans la base de données du répertoire Git.

Si une version particulière d'un fichier est dans le répertoire Git, il est considéré comme **validé**. 

S'il est modifié mais a été ajouté dans la zone d'index, il est **indexé**. 

S'il a été modifié depuis le dernier instantané mais n'a pas été indexé, il est **modifié**.



## Installer git

![one does not simply install git on windows](http://i.qkme.me/35nf3j.jpg "one does not simply install git on windows")


### Officiel
http://git-scm.com/downloads

Note:
Binaire, installeur et source pour Windows, OS X, Linux, Solaris


### Windows
http://msysgit.github.io/


### LINUX
+ Debian: `aptitude install git`
+ Ubuntu: `sudo apt-get install git`
+ ArchLinux: `pacman -S git`


### OS X
Avec [Homebrew](http://brew.sh/)
`brew install git`


![Y U NO GUI](http://cdn.meme.li/i/jqjn1.jpg "command line all Y U NO GUI")


### Interface graphique ?
http://git-scm.com/downloads/guis



## Configuration


### Identité
```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```


### Couleur
```
$ git config --global color.ui true
```


![bravo](http://i.imgur.com/v06N8.gif "bravo")



## Commandes de base


### L'aide dans git
```
$ git --help
$ git add --help
$ git <sub-command> --help
```

### Créer un dépôt local
`$ git init`


### Cloner un dépôt existant
```
$ git clone https://github.com/p-j/isep-git.git
```


### Créer un instantané 
#### Changements spécifiques:
```
$ git add *.html
$ git add README.md
$ git commit -m 'First commit'
```
#### Tous les changements:
```
$ git commit -am 'First commit'
```


# To be continued...


### Enlever un fichier
#### De l'index
```
$ git rm --cached file.html
```
#### De l'index et du disque dur
```
$ git rm file.html
```


### Déplacer des fichiers
Bien que git ne se préocuppe que du contenu, il y a une commade pour déplacer des fichiers.
```
$ git mv file1 file2
```
Qui est l'équivalent de 
```
$ mv file1 file2
$ git rm file1
$ git add file2
```


### Connaitre le status du dépôt
```
$ git status
```


### Voir l'historique du dépôt
#### Complet
```
$ git log
```
#### Filtrer par date
```
$ git log --since=2.weeks
$ git log --since="2 years 1 day 3 minutes ago"
```
#### Format court avec graphique
```
$ git log --pretty=oneline --decorate --graph
```


### Voir les différences
#### Les fichiers modifiés
```
$ git diff
```
##### Les fichiers indexés
```
$ git  diff --cached
```

#### Par rapport a une version spécifique
```
$ git diff 7be56a
git diff HEAD^
```


### Voir les commits
#### Le dernier commit
```
$ git show
```
#### Un commit spécifique
```
$ git show 7be56a
git show HEAD^
```


### Revenir en arrière
#### Modifier le dernier commit
```
$ git commit --amend
```
#### Désindexer un fichier
```
$ git reset HEAD file.html
```
#### Annuler les modifications d'un fichier modifier
```
$ git checkout -- file.html
```
#### Annuler un commit 
```
$ git revert 7be56a
```


### Créer des tags
#### Tags léger
```
$ git tag v0.1.0
```
#### Tags annotés
```
$ git tag -a v0.1.0 -m 'Version 0.1.0'
```

Note:
Un tag est simplement un commit avec un nom un peu plus sympa qu'un hash. On s'en sert pour marquer des versions stable ou des points important dans le développement qui serviront de références.



## .gitignore
```
$ cat .gitignore 
.DS_Store
.svn
log/*.log
tmp/**
node_modules/
```
+ Les lignes vides ou démarrant par un `#` sont ignorées
+ Il est possible d'utiliser des jokers standards
+ Terminer un modèle par un slash `/` pour spécifier un dossier
+ Inverser un modèle avec un point d'exclamation `!`



## Remotes
+ Autre clones du même dépôt
+ Peut être local (un autre `checkout`) ou distant (collègue, serveur central)
+ On peut configurer une valeur par défaut pour `push` et `pull`

```
$ git remote -v
origin  git@github.com:p-j/isep-fsnp.git (fetch)
origin  git@github.com:p-j/isep-fsnp.git (push)
```


### Push to remote
#### Sans valeur par défaut
```
$ git push <remote> <rbranch>
```
#### Configurer une valeur par défaut
```
$ git push -u <remote> <rbranch>
```
#### Puis
```
$ git push 
```


### Pull from remote
#### FETCH & MERGE
```
$ git pull  [<remote> <rbranch>]
```
Equivalent de
```
$ git fetch <remote>
$ git merge <rbranch>
```



## Branches
Les branches sont des "pointeurs" vers des commits.
![schema branch 1](http://git-scm.com/figures/18333fig0308-tn.png "schema branch 1")


### Branches divergentes
![schema branches divergentes](http://git-scm.com/figures/18333fig0309-tn.png "schema branches divergentes")


### Fusionner des branches
![schema fusion de branches](http://git-scm.com/figures/18333fig0317-tn.png "schema fusion branches")


### Conflits lors de la fusion
+ Il y a plusieurs stratégie de fusion automatique
(fast-forward, 3 way, etc...) 
+ Si ça ne fonctionne pas, il faut le faire à la main
```
$ git merge iss53
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```
+ Ensuite, il faut le marquer comme résolue et finaliser le commit
```
$ git add index.html
$ git commit
```


### En général ça marche sans problème
![branch merged successful](http://memecrunch.com/meme/2KBX/git-branch-success/image.png "branch merged successful")


### Gestion des branches


#### Créer une branche
```
$ git branch iss53
```
```
$ git checkout -b iss53 master
```
#### Changer de branche
```
$ git checkout iss53
```
#### Supprimer une branche
```
$ git branch -d iss53
```


#### Voire toutes les branches
```
$ git branch
  iss53
* master
  testing
```
#### Voire le dernier commit sur chaque branches
```
$ git branch -v
  iss53 93b412c fix javascript issue
* master 7a98805 Merge branch 'iss53'
  testing 782fd34 add scott to the author list in the readmes
```


#### Lister les branches fusionnées
```
$ git branch --merged
  iss53
* master
```
#### Lister les branches non fusionnées
```
$ git branch --no-merged
  testing
```



## Stashing
```
$ git stash
$ git stash pop
$ git stash list
$ git stash apply
$ git stash drop
$ git stash clear
```

Note: 
Utilisez git stash quand vous voulez enregistrer l'état actuel du répertoire de travail et de l'index, et revenir à un répertoire de travail propre. La commande enregistre vos modifications locales à part et mets à jour le répertoire de travail pour correspondre à la HEAD.

Les modifications mise de côté par cette commande peuvent être listés avec `git stash list`, inspecté avec `git stash show`, et restauré (potentiellement par dessus ​​un autre commit) avec `git stash apply`. `git stash` sans aucun argument équivaut à `git stash save`. Une `stash` est par défaut répertorié comme «WIP sur branchname ...», mais vous pouvez donner un message plus explicite via la ligne de commande lorsque vous en créez un.



## Workflow courrant
![schema common workflow](http://git-scm.com/figures/18333fig0319-tn.png "schema common workflow")


## Master comme branche stable
+ On ne commit dans master que du code stable
+ On commit le code instable dans une branche de développement
+ On déploie des patchs sur master
+ On merge les patchs dans la branche de développement


## Master comme branche de développement
+ On commit le code instable dans master
+ On créer des tags pour marquer les étapes stables
+ On créer une branche à partir d'un tag pour les patchs
+ On merge les patchs dans master



## Et maintenant ?


![git all the things](http://memecrunch.com/meme/1BZ/git/image.png "git all the things")



## Resources

Très inspiré de [cette présentation](http://blog.dbrgn.ch/2013/2/7/git-introduction-presentation-slides/) de [Danilo Bargen](http://blog.dbrgn.ch/about/)

+ ["Pro Git" Book](http://goo.gl/jX95vy)
+ [Git reference](http://goo.gl/eJODp8)
+ [Github git challenges](http://goo.gl/mJJUXn)
+ [Cheat sheet](http://goo.gl/942WZ8)
+ [Git Visual Cheat sheet](http://ndpsoftware.com/git-cheatsheet.html)
