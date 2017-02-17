---
layout: post
title: Vérifier ses dépendences périmées avec Climb
tags: laravel-5 climb composer scheduler
image: climb.png
---

Jens Segers vient de sortir [Climb (en)](http://jenssegers.com/78/check-outdated-composer-packages-with-climb) un package à utiliser en complément de Composer pour détecter les dépendances dépassées ou celles à mettre à jour. Voici comment planifier son exécution pour recevoir régulièrement une liste des packages à mettre à jour.

<!--more-->
### 1. Installer le package de Climb
`composer require vinkla/climb`

### 2. Planifier l'exécution hebdomadaire

Dans votre fichier `app/Console/Kernel.php`, ajoutez ces lignes à la méthode `schedule()` pour recevoir chaque semaine la liste des packages à mettre à jour.

```php
$schedule->exec('vendor/bin/climb')
    ->sendOutputTo(storage_path('app/outDatedDependencies.log'))
    ->emailOutputTo('email@example.com')
    ->weekly();
```

Ps: Faites attention à bien renseigner le `'from'` de `config/mail.php` lorsque vous travaillez avec Mandrill, en effet ce dernier n'aime pas qu'il soit vide lorsque `emailOutputTo()` est appelé.
