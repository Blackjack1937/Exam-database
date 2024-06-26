
---

## 1. Part1.sql:

Ce fichier contient les instructions SQL pour créer les tables de la base de données. Les tables incluent `ETUDIANTS`, `ENSEIGNANTS`, `SALLES`, `EPREUVES`, `INSCRIPTIONS`, `HORAIRES`, `OCCUPATIONS`, et `SURVEILLANCES`. Les attributs de chaque table et leurs contraintes correspondent aux descriptions fournies dans le fichier PDF.

## 2. Part2.sql:

Ce fichier se concentre sur la gestion d'une colonne dérivée, `Nb_Inscrits`, pour la table `EPREUVES`. Voici les étapes principales:
- **Ajout de la colonne `Nb_Inscrits`**: Une nouvelle colonne est ajoutée à la table `EPREUVES` pour stocker le nombre d'étudiants inscrits à une épreuve. Elle est initialisée à 0.
- **Mise à jour de `Nb_Inscrits`**: Le nombre d'inscrits pour chaque épreuve est calculé en fonction des inscriptions actuelles.
- **Triggers**: Deux déclencheurs sont définis pour gérer automatiquement les mises à jour de la colonne `Nb_Inscrits`:
  - Lorsqu'une nouvelle épreuve est créée, `Nb_Inscrits` est initialisé à 0.
  - Lorsqu'une inscription est ajoutée ou supprimée, la valeur de `Nb_Inscrits` pour l'épreuve concernée est mise à jour.

## 3. Part3.sql:

C1 : Contrainte sur les horaires des épreuves

    Description : Une épreuve ne peut pas se terminer après 20h00.
    SQL : Un déclencheur est créé pour vérifier que l'heure de fin de l'épreuve (déterminée en ajoutant la durée de l'épreuve à l'heure de début) ne dépasse pas 20h00.

C2 : Contraintes sur les inscriptions

    Description : Un étudiant ne peut pas avoir deux épreuves en même temps.
    SQL : Un déclencheur est créé pour vérifier qu'aucune des épreuves auxquelles un étudiant est inscrit ne se chevauche avec une nouvelle épreuve à laquelle il essaie de s'inscrire.

C4 : Contrainte sur la capacité des salles

    Description : La somme des places occupées par toutes les épreuves dans une salle ne doit pas dépasser la capacité de la salle.
    SQL : Un déclencheur est créé pour calculer le total des places occupées dans une salle après une insertion ou une mise à jour et vérifier si ce total dépasse la capacité de la salle.

C5 : Contrainte sur la surveillance des épreuves

    Description : Il ne peut y avoir de surveillance que si une épreuve est programmée dans la salle à l'heure donnée.
    SQL : Un déclencheur est créé pour vérifier si une épreuve est programmée dans une salle à l'heure de début de la surveillance.

---