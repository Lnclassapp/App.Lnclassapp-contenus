# Référentiel d'import

Les deux fichiers livrés à l'écran **Imports** de l'application (ADR-0034, ADR-0066), dans cet ordre :

1. `drenas-2026.json` : les 41 DRENA (`lnclass.drenas` v1). À importer en premier.
2. `etablissements-2026.json` : 3 851 écoles (`lnclass.schools` v1), chacune rattachée à une DRENA du premier fichier.

Ils ne contiennent que le nom, le type, le statut et la DRENA de chaque école : ni contact, ni adresse, ni donnée de personne. Ils vivaient dans `db/seeds/data/imports/` de l'application.

Contrôle de cohérence (schéma, 41 slugs, 3 851 écoles, DRENA citées = DRENA livrées) : depuis l'application, `CONTENUS_DIR=<clone de ce dépôt> bin/rails test test/db/import_data_files_test.rb`.
