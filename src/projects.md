
# Relation possible avec d'autres projets

## Standard CNIG et Géoportail de l'Urbanisme

Le Géoportail de l'Urbanisme pourrait exposer le registre des règles d'urbanisme (les données de ce registre gagnerait toutefois à être hébergée dans un dépôt GitHub pour permettre des contributions)

Le standard CNIG pourrait proposer des extensions pour l'instanciation de ces règles. Exemple : permettre l'ajout d'un fichier `reglement.json` avec une structure permettant d'instancier les règles générales et les règles s'appliquant sur chaque zone, etc.)

## SmartPLU

SmartPLU extrait les informations des textes des documents d'urbanisme présents sur le [Géoportail de l'urbanisme](https://www.geoportail-urbanisme.gouv.fr) à l'aide de technique d'IA.

SmartPLU a en outre vocation à fournir les paramètres des règles d'urbanisme dans une modélisation comptabible avec ce registre de règle.

Une première fourniture de données a été réalisée au format CSV : [sample/SmartPLU-20180913.csv](sample/SmartPLU-20180913.csv)

Des discussions sont en cours sur un format XML qui permettra la fourniture d'information plus riche (variantes d'une même règle trouvée sur la zone, citation des textes,...)


## APUR

L'APUR publie en opendata une table [PLU HAUTEUR](http://opendata.apur.org/datasets/plu-hauteur/data) conceptuellement proche de l'instanciation CSV des règles d'urbanisme proposée par SimPLU.

On y trouve en effet une colonne "Règlement hauteur" prenant par exemple pour valeur "de 16 à 24m".


## PLU Manager

[PLU Manager](https://www.plan-local-d-urbanisme.fr/outil-logiciel-plu-manager/) génère les textes de document d'urbanisme. La fonction "Duplication d'articles existants" n'est pas très loin d'une fonctionnalité de création d'article à partir d'un modèle de phrase fourni par un registre de règle.

## D'autres idées, d'autres références?

Si vous connaissez d'autres projets potentiellement concernés, n'hésitez pas à [faire une "issue" sur le projet github SimPLU3D/plu-formel](https://github.com/SimPLU3D/plu-formel/issues)
