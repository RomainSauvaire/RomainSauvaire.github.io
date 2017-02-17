---
title: Nettoyer ses données de formulaire avant validation
tags: laravel 5.4 form validation
image: dust.jpg
original: http://larabrain.com/tips/sanitizing-form-data-before-validating-in-a-laravel-5-form-request
---

Quand on travaille avec les [form request](https://laravel.com/docs/5.4/validation#form-request-validation), il arrive parfois d'avoir besoin de standardiser les données *avant* qu'elles ne passent dans le validateur.

<!--more-->

Par exemple si vous avez demandé un numéro de téléphone avec seulement des chiffres `0612345678` tout en laissant le champ libre à l'utilisateur pour la saisie. Si votre utilisateur saisit `06.12.34.56.78`, il ne respecte pas votre formatage mais cela n'empêche que l'entrée est parfaitement valide. Pourquoi combpliquer la vie de notre utilisateur en lui refusant cette entrée ?

La classe `Request` inclut la méthode `all()` qui récupère toutes les données de la requête et cette dernière permet de surcharger les valeurs que l'on désire comme ceci :

```PHP

class RegistrationRequest extends Request
{
	public function all()
	{
		$input = parent::all();
		    
		// On retire tout ce qui n'est pas un chiffre
		$input['phone'] = preg_replace("/[^0-9]/", '', $input['phone']);
		
		$this->replace($attributes);
		
		return parent::all();
	}

}
```

Il n'y a rien d'autre à faire : lors de la validation de vos données, Laravel va appeler votre méthode `all()` qui retournera les informations déjà filtrées.