# Lexique

## SASS : préprocesseur CSS

Le navigateur ne comprend pas le sass mais le css. Le code devra être traduit en CSS.
La techno s'appelle SASS mais on fait des fichiers scss

##

Transforme du sass en css

## Assets

Comprend du JS, du CSS & sass

## Parcel

parletjs.org => Assets Bundler
Logiciel ou Code écrit est comme une dépendance

```sh
npm install --global parcel
```

```sh
# Il convertit le html et scss dans un dossier `dist` et Il lance automatiquement un serveur de dev (comme serveur php)
Parcel + nom du fichier
```

## npm

npmjs.com
équivalent de composer car il gère les dépendances

```sh
# installe le reset css de Meyer
npm install reset-css
npm install --save reset.css
# pour installer dernière version de npm
npm install --global npm
```

## node_modules

Code du module npm
équivalent du dossier vendor de composer

## Nesting

Mettre une propriété avec du css dans le parent qui a deja une propriété
ex : 

```sh
# Le caractère "&" permet de rappeler.carousel et donc de profiter du sass
.carousel {
    display: flex;
    
    &__items {
        width: 100%;
    }
}
```

## mixins

Morceau de sass qu'on va pouvoir injecter dans un autre fichier de sass.
Permet de définir les breakpoints pour le responsive par exemple.
C'est l'équivalent d'une fonction custom en php qu'on appelle dans un autre fichier.

```sh
# Plutot que de déclarer une nouvelle media query, on utilise une mixin (dans un dossier abstract)
@mixin medium {
    @media screen and (min-width: 600px) {
        // content va reprendre le contenu des accolades qu'on l'on pose avec le @include
        @content;
    }
```

```sh
# On fait un include dans notre sccs de notre choix
      @include medium {
        width: 50%;
      }
```

## mimification

pour plus de performance on réduit le fichier pour aller plus vite au chargement


## Taxonomy

type de classement que l'on peut faire pour ses article dans le backoffice de Wordpress
ex : classer par catégorie

## Custom post Type

Les Custom Post Types permettent de créer des types de contenu sur-mesure, associant ou non une taxonomie particulière, pour créer sa propre architecture.

## Capability

Capacités qui déterminent les droits auxquelles on a accès selon son rôle.

## Query_vars

Parametres d'url (avec $_GET)
On récupère ensuite les query_vars avec la fonction `get_query_var()`

# Vue.js

## Interpolation

Grâce à la syntaxe `{{ }}`, qui fonctionne comme un short echo tag de PHP, on peut faire un liaison entre une variable JS et une zone de texte en html.
On peut y mettre du JavaScript 
Le HTML peut aussi est être interprété suelement avec utklisation d'une directive

## Directive

Attribut HTML propre à Vue.js qui permet d'utiliser du HTML interprété.
Notre variable contiendra en string notre contenu
```sh
HTMLContent = "<strong>Bienvenue à vous</strong>"
```

```sh
<div>
v-html = `HTMLContent`
</div>
```

## modifiers

v-on::`nom-de-levenement`
@`nom de l'evenement`


## Props

Passer des données depuis l'extérieur gràce à un array
`props: ["today"]`

Pour fournir de la données à un composant enfant qui accepter certaines props, on utilise `v-bind` pour lier des données.
```sh
`v-bind:today=`nom de variable`
```

Syntaxe alternantive de `v-bin:today` => `:today="currentDay"`

