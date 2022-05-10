# Commandes Linux pratiques

```sh
# Commande pour supprimer le cache (si error d'affichage d'une mauvaise page)
rm -rf .parcel-cache && rm -rf dist
```

```sh
parcel build src/index.html + paramètres
```

```sh
# pour installer la langue fr
wp language core install fr_FR
# commande ci-deessou dépréciée
wp language core activate fr_FR
# utiliser plutot celle-ci :
wp site switch-language instead
```


```sh
composer run build-assets
```

```sh
# permet à apache d'écrire dans le dossier uploads => à la racine du projet
sudo chown -R student:www-data wp-content/uploads
```
