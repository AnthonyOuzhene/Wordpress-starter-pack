# Plugins

## Pack de langue Fr

```sh
# pour installer la langue fr
wp language core install fr_FR
# /!\ ATTENTION : commande ci-dessous dépréciée
wp language core activate fr_FR
# utiliser plutot celle-ci :
wp site switch-language instead
```

## Query monitor

Barre d'outils en mode dev pour Wordpress (sensiblement pareil que `Profiler` pour Symfony)

https://fr.wordpress.org/plugins/query-monitor/

```sh
composer require wpackagist-plugin/query-monitor
wp plugin activate query-monitor
```

## classic editor

Editeur de Wordpress et son écran de rédaction

https://fr.wordpress.org/plugins/classic-editor/


```sh
composer require wpackagist-plugin/classic-editor
wp plugin activate classic-editor
```

## Fakerpress

Générateur de faux articles pour avoir de quoi travailler

https://fr.wordpress.org/plugins/fakerpress/

```sh
composer require wpackagist-plugin/fakerpress
wp plugin activate fakerpress
```

1. Dans le backoffice, on trouve "FakerPresss" dans la colonne de gauche.
2. On va dans "Articles", puis on choisit une quantité (un min et un max)
3. On enlève les Taxinomies dans "Taxonomy Field Rules"
4. On retire aussi "placehold.it" et "Lorem PIcsum" de "Meta Field Rules"
5. Puis on clique sur "Generate" et on laisse mouliner

## jwt-auth

```sh
composer require wpackagist-plugin/jwt-auth
wp plugin activate jwt-auth
```


# Création d'un plugin

1. créer un répertoire dans le dossier `wp-content/plugins`
2. créer dans ce répertoire un fichier PHP qui porte le même nom que le répertoire
3. Ce fichier doit contenier un commentaire avec au minum la ligne :
```sh
/**
 * Plugin Name: oProfile
 */
 ```
4. vérifier que ce dossier n'est pas ignoré par le .gitignore
5. Activer le plugin avec `wp plugin activate nomduplugin`
6. on peut vérifier que ça fonctionne en entrant un morceau de code dans ce fichier, par ex :

```sh
exit('plugin custom');
```
7. Penser à bien supprimer le code de l'étape 6
