# Installation Wordpress

## Démarche

Avantages avec Composer  :
- Se gère comme une dépendance,
- pas de souci de compatibilité. Composer va gérer les versions à installer,
- Versionning pour travail en équipe.

## installation de Composer

```sh
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
sudo mv composer.phar /usr/local/bin/composer
```

## Installation de Wordpress

```sh
composer require johnpbloch/wordpress
```
```sh
# Mettre "yes" pour faire confiance au code
Do you trust "johnpbloch/wordpress-core-installer" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?]
```

## Créer un BDD sur adminer

Créer une bdd sur adminer & utilisateur avec privilège

## Utiliser wp_cli

Démarche installation : [https://wp-cli.org/fr/]

documentation wpi-cli : [https://make.wordpress.org/cli/handbook/]

```sh
# Lister des commandes à rentrer dans terminal :
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
```

```sh
# vérifier que c'est bien installé avec la commande :
wp --info
```

### Installation de WP suite.

Au lieu d'utiliser le formulaire d'installation, on peut utiliser wp-cli :

- Ajouter un fichier wp-cli.yaml avec comme contenu :
```sh
path: wordpress
```

- Créer un fichier wp-config dans dossier wordpress

```sh
// Je définis l'URL vers la page d'accueil de mon site
define(
    'WP_HOME',
    rtrim ( 'http://localhost/Wordpress/wp-oSailing-AnthonyOuzhene/', '/' )
);

// Je définis l'URL vers le dossier source de WordPress
define(
    'WP_SITEURL',
    WP_HOME . '/wordpress'
);

// Je définis l'URL vers le dossier wp-content
define(
    'WP_CONTENT_URL',
    WP_HOME . '/wp-content'
);

// Je définis le path (chemin côté serveur) vers le dossier wp-content
define(
    'WP_CONTENT_DIR',
    __DIR__ . '/wp-content'
);
```

- Configurer les salts :

1. cliquer sur le lien en commentaire `https://api.wordpress.org/secret-key/1.1/salt/`
2. faire un copier/coller:

```sh
define('AUTH_KEY',         's+9gcf%+M{y;4%{NF)NJ}M3g2j+,C^=6vP~`60I~+Dk6CGUW1[vSE@,rl5H,%kCw');
define('SECURE_AUTH_KEY',  '/xF6V`b&7>v54d+L&zd4{KHv_B<Sr~rgR2r..%dlAdgZ2UL$DLb+A=*t/ehI^?Um');
define('LOGGED_IN_KEY',    'LZL,qU~?;QA`?kIifiN4Jnp,Z:}p1mWU#|Vl)(^!/?iN#20ZL>xe&58(nc]+Dv-0');
define('NONCE_KEY',        'ul.PgU<^K=^*8e7c[wau*1zK.*rmj0,v>U)&Z~q!Ci)HCZ}wpcl3c0!)i#Bao]}4');
define('AUTH_SALT',        ').nindU35UG9eL4l:+1-Fw-_]0xS-1er:4)yPVT(n]U|bUY`AZ8f=Ptdd~y]- /e');
define('SECURE_AUTH_SALT', 'bo{e tT+S6}np_r;sb`s2>c4+FT*,ktp2+,=R@,sTk@$;(to4|Am*LcS:Y^oxr;z');
define('LOGGED_IN_SALT',   '_V_Bt`$r)P3s6f#r&C<:7X>D-NQ-F^+;ZzYe+@BBe:ow|LZF`=S&{2a?ny8Q(t[4');
define('NONCE_SALT',       '<vUZ*)Hwb}>tx=9HTd~^ $R?:|t5{C >)+lewcJA;F|-WUKer+ vE-e5%mN/&WPc');
```

- Créer un fichier wp-config-sample à la racine

- Puis rentrer la commande suivante :

```sh
wp core install --url=example.com --title=Example --admin_user=supervisor --admin_password=strongpassword --admin_email=info@example.com
```

```sh
# exemple
'wp core install --url=http://localhost/Wordpress/wordpress-install --title="Wordpress2" --admin_user=wpadmin --admin_password=wpadminpass --admin_email=admin@bidon.zut'
```
Réponse attendue : ```Success: WordPress installed successfully.```




- Rajouter un .htaccess à la racine
```sh
RewriteEngine on
RewriteCond %{REQUEST_URI} !^wordpress/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php/$1
```

Rajouter un index.php à la racine
```sh
<?php
/**
 * Front to the WordPress application. This file doesn't do anything, but loads
 * wp-blog-header.php which does and tells WordPress to load the theme.
 *
 * @package WordPress
 */

/**
 * Tells WordPress to load the WordPress theme and output it.
 *
 * @var bool
 */
define( 'WP_USE_THEMES', true );

/** Loads the WordPress Environment and Template */
// CUSTOM : on modifie le chemin pour retrouver wp-blog-header.php
require __DIR__ . '/wordpress/wp-blog-header.php';
```

### Utiliser packagist

Nous permet d'utiliser des thèmes et plugins avec composer

https://wpackagist.org/

rajouter ceci au composer.json

```sh
    "repositories":[
        {
            "type":"composer",
            "url":"https://wpackagist.org",
            "only": [
                "wpackagist-plugin/*",
                "wpackagist-theme/*"
            ]
        }
    ],
```
 - PLUGINS

Et faire un composer require avec nom de dépendance
```sh
composer require wpackagist-plugin/wordpress-seo
# Puis activation :
wp plugin activate wordpress-seo
```

- THEME

Trouver sur Wordpress les noms de theme => récupérer le vrai nom dans url du theme.

```sh
composer require wpackagist-theme/twentyseventeen
# Puis activation:
wp theme activate twentyseventeen
```

### Remplir le gitignore

```sh
vendor
wordpress
wp-config.php

/wp-content/*
!/wp-content
/wp-content/themes/*
!/wp-content/themes
/wp-content/plugins/*
!/wp-content/plugins

!/wp-content/themes/custom
!/wp-content/plugin/custom
```