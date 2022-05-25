# Dépendances à installer

## Reset.css

```sh
# installe le reset css de Meyer
npm install reset-css
npm install --save reset.css
# pour installer dernière version de npm
npm install --global npm
```

## axios

Installation du composant

```sh
npm install --save axios
# OU
npm i -s axios
```

Importer la dépendance dans le composant courant
```sh
import axios from 'axios';
```

## Router

Permet d'intéragir avec url courante avec le composant

```sh
#Installation du composant
npm install vue-router@4
```

## Vuex

Vuex est un modèle de gestion d'état + une bibliothèque pour les applications Vue.js. Il sert de magasin centralisé pour tous les composants d'une application, avec des règles garantissant que l'état ne peut être muté que de manière prévisible.
Pour 2 composants Vue qui partagent la meme donnée => on utilise vuex

```sh
npm install vuex@next --save
```