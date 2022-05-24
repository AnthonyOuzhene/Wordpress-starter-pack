# Vue.js

https://vuejs.org/guide/essentials/event-handling.html

## Démarrage

On utilise parcel sur le fichier html dans le dossier sources.

```sh
index.html:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="app"></div>
    <script type="module" src="./index.js"></script>
</body>
</html>
```
```sh
index.js:
import { createApp } from "vue";
import App from "./App.vue";

const app = createApp(App);
app.mount("#app");
```

```sh
App.vue:
<template>
  <div>Hello {{ name }}!</div>
</template>

<script>
  export default {
    data() {
      return {
        name: "Vue",
      };
    },
  };
</script>
```

## Installation de Vue

```sh
# Installtion de vue dans le projet
npm install --save vue
```

## installation vue/cli en global

1. Lancer la commande suivante :

```sh
sudo npm install -g @vue/cli
```

2. Vérifier la version de Vue avec :

```sh
vue --version
```

## Créer un thème avec implémentation vue.js

```sh
vue create `nom-du-theme`
```

## Syntaxe de Vue.js

1. Boucles

`v-for`

2. Conditions

`v-if`,
`v-else,`
`v-elseif` 
=> permet de modifier la structure HTML (un élément est présent ou non dans le DOM) en fonction d'un booléen

`v-show` => 
L'élément sera affiché ou masqué via CSS selon la valeur d'un booléen

## Components

Pour pouvoir utiliser un composant externe dans la liste, il faut importer le fichier .vue dan ce composant externe

```sh
import `NomduComposant` from './components/`NomduComposant.vue`';
```