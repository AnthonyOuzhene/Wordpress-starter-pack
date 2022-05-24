# Commandes Linux pratiques

```sh
# Commande pour supprimer le cache (si error d'affichage d'une mauvaise page)
rm -rf .parcel-cache && rm -rf dist
```

```sh
parcel build src/index.html + paramètres
```

## Commande à utiliser avec un composer run à la racine du projet

1. ### build-assets

installe les dépendances et fait un parcel build dans le thème pour installer dans un dossier `dist` la conversipn du `sass` en `css`

```sh
# dans scripts dans composer.jon
        "build-assets": [
            "cd wp-content/themes/oprofile && npm install",
            "cd wp-content/themes/oprofile && parcel build main.js"
        ],
```
2. ### reactivate-plugin

Désinstalle et réactive le plugin pour administrer les changements appliqués au plugin

```sh
"reactivate-plugin": "wp plugin deactivate oprofile && wp plugin activate oprofile"
```

3. ### upload-rights

"uploads-right": "sudo chown -R $USER:www-data wp-content/uploads",


```sh
# permet à apache d'écrire dans le dossier uploads => à la racine du projet
"uploads-right": "sudo chown -R $USER:www-data wp-content/uploads",
```

## Commande pour génerer directement du code applicable et modifiable (comme avec le maker de symfony)

1. ### post-type

```sh
#Commande pour générer automatiquement un post type grâce à WP-CLI
# https://developer.wordpress.org/cli/commands/scaffold/post-type/
# ex : wp scaffold post-type projectPostType --plugin=oprofile
wp scaffold post-type `nom du post type` --plugin=`nom du point d'entrée du plugin`
 
```