---
title: Stocker ses ressources dans /storage
tags: salut les musclés
original: http://taylorotwell.com/spark-storage/
---
# Stocker ses ressources dans /storage

Cela rend les choses plus faciles lorsqu'on doit passer vers S3 ou utiliser Envoyer

Changer le disque utilisé de `local` vers `public`

`php artisan storage:link`

[Voir](https://laravel.com/docs/5.3/filesystem#the-public-disk)
puis récupérer en préfixant de `storage`

Générer les liens : https://laravel.com/docs/5.3/filesystem#file-urls


```
$path = $request->file('panorama')->store('panoramas');
{{ asset('storage/' . $panorama->picture) }}
```

![My helpful screenshot]({{ site.url }}/images/posts/composer.png)