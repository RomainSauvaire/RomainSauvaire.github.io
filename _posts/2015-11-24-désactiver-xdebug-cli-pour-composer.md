---
layout: post
title: Désactiver XDebug pour améliorer la vitesse de Composer
tags: [laravel-5, climb, composer, scheduler]
image: composer.png
---

Composer pourrait être jusqu'à trois fois plus rapide [en désactivant XDebug](https://getcomposer.org/doc/articles/troubleshooting.md#xdebug-impact-on-composer) pour le mode console et recommande ce changement depuis sa dernière mise à jour.
<!--more-->

>You are running composer with xdebug enabled. This has a major impact on runtime performance.

Il est possible que vous ne voyiez pas encore ce warning, si c'est le cas, n'hésitez pas à mettre Composer à jour en lançant `composer self-update`.

## Désactiver XDebug pour le mode <abbr title="Command Line Interface">CLI</abbr>

```BASH
sudo php5dismod -s cli xdebug
sudo service php5-fpm restart
```

## Désactiver XDebug pour tous les services
Désactiver totalement XDebug sur votre serveur de production peut être une excellente démarche afin de s'assurer qu'en cas d'erreur, le visiteur ne se retrouve pas avec plus d'informations qu'il le devrait voir. 

```BASH
sudo php5dismod xdebug
sudo service php5-fpm restart
```

## Bonus : Réactiver XDebug

```BASH
sudo php5enmod xdebug
sudo service php5-fpm restart
```
