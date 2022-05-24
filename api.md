# API

dans notre ORM (Insomnia ou ThunderClient), faire une recherche avec 
{{ _.base_url }}/wp/v2/recipes

pour éviter une 404, il faut ajouter dans les CAPS le class mère de postType `'show_in_rest' => true,`
pour faire apparaitre, les terms de taxo dans l'éditor Guttenberg, ajouter `'show_in_rest' => true,` dans la class mere des taxonomy

# installation du plugin token coté back

```sh
composer require wpackagist-plugin/jwt-auth
wp plugin activate jwt-auth
```