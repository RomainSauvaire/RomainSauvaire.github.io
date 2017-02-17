---
layout: post
title: Optimiser ses metas Open graph et Twitter cards 
original: https://adactio.com/journal/9881
tags: [laravel-5, climb, composer, scheduler]
image: opengraph.png
---

Partager sur Twitter et sur Facebook requiert un certain nombre de métadonnées pour présenter correctement le lien que vous souhaitez partager.
<!--more-->

Voici ce que Facebook vous demande :

```HTML

<meta property="og:url" content="http://romainsauvaire.github.io/2015/11/24/optimiser-open-graph-and-twitter-cards-meta/">
<meta property="og:title" content="Optimiser ses metas Open graph et Twitter cards">
<meta property="og:description" content="Comment regrouper le tout pour épargner le poids de la page.">
<meta property="og:image" content=".../////.png">

```

Et voici le (presque) même code pour Twitter :

```HTML
<meta name="twitter:url" content="http://romainsauvaire.github.io/2015/11/24/optimiser-open-graph-and-twitter-cards-meta/">
<meta name="twitter:title" content="Optimiser ses metas Open graph et Twitter cards">
<meta name="twitter:description" content="Comment regrouper le tout pour épargner le poids de la page.">
<meta name="twitter:image" content=".../////.png">
```

Semblables mais différents dans le fait que Twitter utilise un attribut `property` alors que Facebook utilise un attribut `name` pour décrire la valeur qui suit.

## La solution : regroupez-les
Même si techniquement il n'[existe pas d'attribut](http://dev.w3.org/html5/spec-preview/the-meta-element.html) `property` rien n'empêche de l'utiliser pour satisfaire ces géants du web.

Ceci

```HTML
<meta property="og:title" content="Optimiser ses metas Open graph et Twitter cards">
<meta name="twitter:title" content="Optimiser ses metas Open graph et Twitter cards">
```

Est donc réécrit comme ça :
```HTML
<meta property="og:title" name="twitter:title" content="Optimiser ses metas Open graph et Twitter cards">
```

## La vraie solution : les standards
Je ne prêcherai jamais pour l'utilisation de balises/attributs propriétaires ou ciblants certains réseaux sociaux. Les standards web nous permettent déjà de spécifier un `<tilte>`, une `<meta name="description">` et les algorithmes de partage sont assez malins que pour les extraire lorsque les métadonnées ne sont pas spécifiées.
