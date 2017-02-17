---
layout: post
title: Compiler automatiquement ses assets après npm install
---
Au plus on automatise les tâches récurrentes, au plus notre esprit est libre de se concentrer sur les choses importantes. 

Pour l'instant, après chaque `npm install`, je dois me souvenir de lancer la commande `gulp` pour recompiler les assets qui utilisent les nouveaux composants.  
<!--more-->
Cette manipulation obligatoire et récurrente occupe de la place dans votre mémoire pour rien.  
La commande `npm install` prend beaucoup de temps : on peut se préparer un café pendant qu'elle tourne et s'éviter d'être frustré de devoir encore lancer `gulp`.

Pour nous éviter cette peine il suffit simplement de se brancher à un point d'entrée (un _hook_) `postinstall` dans notre `package.json`

```JSON
{
  "scripts": {
    "postinstall": "gulp"
  }
}
```

De cette manière la commande `gulp` sera automatiquement appelée après chaque installation `npm`. Si vous avez besoin d'autres points d'entrée, il y a [plein d'autres _hooks_ disponibles](http://www.marcusoft.net/2015/08/pre-and-post-hooks-for-npm-scripting.html#hooks-out-the-box).

Happy hooking !
