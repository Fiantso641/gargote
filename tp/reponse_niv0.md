# Niveau 0

---

##  0-2-le schéma relationnel des 4 tables, en soulignant les clés primaires et en marquant les clés étrangères:

- categorie (<u>id</u>,libelle)
- plat (<u>id</u>,nom,prix,#id_categorie)
- commande (<u>id </u>,date_commande,numero_table)
- commande_ligne (<u>id</u>,#id_commande,#id_plat,quantite,prix_unitaire))


## Pourquoi commande_ligne contient-elle une colonne prix_unitaire, alors que le prix est déjà dans plat ? Donnez un exemple concret où les deux valeurs seraient différentes.

La colonne `prix_unitaire` dans la table `commande_ligne` est nécessaire pour enregistrer le prix du plat au moment de la commande.
Cela permet de conserver l'historique des prix, même si le prix du plat change dans la table `plat` après la commande.
Exemple concret : Supposons qu'un plat "Romazava" coûte 10 000 ariary au moment de la commande. Si le restaurant décide de changer le prix du "Romazava" à 12 000 ariary après que la commande a été passée, la colonne `prix_unitaire` dans `commande_ligne` conservera le prix original de 10 000 ariary pour cette commande spécifique, tandis que la table `plat` reflétera le nouveau prix de 12 000 ariary. Cela permet de calculer correctement 
le total de la commande et d'éviter toute confusion sur les prix facturés aux clients.

## Que se passe-t-il pour les lignes d’une commande quand on supprime la commande ? Quelle instruction en est responsable ?

Lorsque l'on supprime une commande, toutes les lignes associées à cette commande dans la table `commande_ligne` sont également supprimées automatiquement. Cela est rendu possible grâce à la contrainte de clé étrangère avec l'option `ON DELETE CASCADE` définie sur la colonne `id_commande` de la table `commande_ligne`. Cette instruction garantit que lorsque la commande parent est supprimée,
toutes les lignes enfants qui y sont liées sont également supprimées pour maintenir l'intégrité référentielle de la base de données.

## Repérez trois données absurdes que le schéma actuel accepte sans broncher (indice : essayez d’insérer à la main un prix négatif). Notez-les : vous les corrigerez au niveau 1 et 2. 
1. Insertion d'un plat avec un prix négatif 
2. Insertion d'une commande avec une date de commande future 
3. Insertion d'une commande_ligne avec une quantité négative 
4. Insertion d'une catégorie avec un libellé vide 

