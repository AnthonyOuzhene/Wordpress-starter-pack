# Registration

Le hook `register_form'` nous permet d'intervenir au moment ou le  champ email est affiché dans formulaire.

1. On affiche le formulaire et on ajoute nos hooks dans l'init

        add_action('register_form', [self::class, 'displayCustomFields']);
        add_filter('registration_errors', [self::class, 'validateCustomFields']);

2. On vérifie la validation du formulaire en vérifiant les errors
la variable $errors est disponible grace à la fonction add_filter();

la fonction de validation des données doit donc return $errors

https://codex.wordpress.org/Validating_Sanitizing_and_Escaping_User_Data

3. Si la validation c'est bien passée, il enregistre les données de l'utilisateur. 
Mais nous devons manuellement sauvegarder les meta (comme les roles par ex)