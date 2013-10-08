# Git
*Présentation pour l'APP ISEP 2013*

Sources:
Très inspiré de [cette présentation](http://blog.dbrgn.ch/2013/2/7/git-introduction-presentation-slides/) de [Danilo Bargen](http://blog.dbrgn.ch/about/)

+ ["Pro Git" Book](http://goo.gl/jX95vy)
+ [Git reference](http://goo.gl/eJODp8)
+ [Github git challenges](http://goo.gl/mJJUXn)
+ [Cheat sheet](http://goo.gl/942WZ8)
+ [Git Visual Cheat sheet](http://ndpsoftware.com/git-cheatsheet.html)

Réalisé avec [reveal.js](https://github.com/hakimel/reveal.js)

---

## Comment visualiser la présentation ?
+ Solution simple : [http://p-j.github.io/isep-git/](http://p-j.github.io/isep-git/)
  + Une fois sur la page, appuyé sur `S` pour voir les notes du présentateur 
   + `N` pour passer au slide suivant 
   + `P` pour revenir au précédent. 
   + Les fleches directionnelles peuvent également être utilisées, mais n'oubliez pas les slides verticaux !
+ Juste les sources (avec les notes du présentateur) : [sources](https://github.com/p-j/isep-git/blob/master/data/slides.md)
+ Cloner et regarder : 
  + `$ cd /chemin/vers/votre/dossier/www`
  + `$ git clone git@github.com:p-j/isep-git.git` (clone le dépôt de la présentation)
  + Naviguez vers [http://127.0.0.1/isep-git](http://127.0.0.1/isep-git)
+ Pour les curieux, la présentation peut être modifiée et réutilisée à l'aide des outils suivant :
  + [node](http://nodejs.org/)
  + [grunt](http://gruntjs.com/getting-started#installing-the-cli)
+ Une fois ces outils installés, la procédure suivante permet d'accéder à la présentation :
  + `$ git clone git@github.com:p-j/isep-git.git` (clone le dépôt de la présentation)
  + `$ cd isep-git` (aller dans le dossier que l'on vient de créer)
  + `$ npm install` (installer les dépendances)
  + `$ grunt serve` (assembler les fichiers et lancer le server local pour afficher la présentation)
  + Puis naviguez vers [http://localhost:8000](http://localhost:8000) pour voir la présentation

D'avantage d'information sur comment utiliser [reveal.js](https://github.com/hakimel/reveal.js) sont disponibles sur le dépôt officiel [hakimel/reveal.js](https://github.com/hakimel/reveal.js) (en anglais).
 
## License
MIT licensed

Copyright (C) 2013 Jérémie Parker, http://jeremie-parker.com
