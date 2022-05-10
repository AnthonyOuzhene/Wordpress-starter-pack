# Theme 

## Configurer la page d'accueil sur une page statique

Si le contenu de la page d'accueil n'est pas géré par défaut dans WP, on doit configurer une page statique

1. Créer une page statique => ici "accueil"
2. Dans Réglages/Lecture, choisir "page statique" pour l'accueil et choisir "Accueil" (la page créée en 1)
3. Valider

## Fichiers de template

Dans notre thème, on trouve des fichiers PHP qui sont des templates. Le template de base est index.php.

Pour fonctionner correctement, un fichier de template doit utiliser <?php wp_head(); ?> entre les balises `<head></head>` et `<?php wp_footer(); ?>` juste avant la fermeture de </body>. => sinon pas de barre d'admin (entre autres soucis)

## Boucle principale

Lorsqu'on utilise la boucle principale (`the_loop`), on utilise des fonctions pour récupérer le contenu d'un post. Par ex. `the_title()`. 

Pour savoir de quel post on récupère le contenu avec les fonctions the_ou get_the , WP a besoin de "charger" le contenu d'un post dans le contexte => the_post()

## Image mise en avant de l'article

1. On creer un fichier functions.php

```sh
<?php

# on déclare que notre thème supporte la fonctionnalité "image mise en avant" (thumbnails ou Featured Image) pour pouvoir définir une image mise en avant sur nos articles
add_theme_support( 'post-thumbnails' );
```
2. dans le backoffice : ajouter une image dans et mettre à jour