# Custom roles

## Capabilities

Pour créer des capabilities custom pour un CPT

A partir du moment ou on ajouter une clé `capabiliites` dans `register_post_type` => on exige pour ce CPT d'avoir la caps associée pour chaque action

Par ex :
CPT customer qui déclare une cap custom `edit_customers` correspondant à l'action de la cap apr défaut `edit_posts`.
Seuls utilisateurs ayant le roles avec cette cap pourront réaliser cette action sur le CPT customer
=> Le role d'admin ne possède pas cette cap !

Il faudra ajouter les caps nécessaires pour le rôle `administrator`