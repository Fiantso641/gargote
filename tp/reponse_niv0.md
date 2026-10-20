# Niveau 0

---

##  0-2-le schéma relationnel des 4 tables, en soulignant les clés primaires et en marquant les clés étrangères:

- categorie (<u>id</u>,libelle)
- plat (<u>id</u>,nom,prix,#id_categorie)
- commande (<u>id </u>,date_commande,numero_table)
- commande_ligne (<u>id</u>,#id_commande,#id_plat,quantite,prix_unitaire))
