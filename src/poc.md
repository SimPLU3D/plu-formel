# Preuves de concepts et démonstrateurs

## Démonstrateur SimPLU

### En entrée

* Embryon de registre de règle : https://demo-simplu3d.ign.fr/views/rule/view.html
* Instanciation des règles avec un CSV : https://demo-simplu3d.ign.fr/api/project/1/file/rules.csv
* Des données géographiques : https://demo-simplu3d.ign.fr/#/project/1/file

### En sortie

* Texte généré : https://demo-simplu3d.ign.fr/#/project/1/rule
* Une carte où l'on peut cliquer sur les parcelles pour voir si les règles sont respectées : https://demo-simplu3d.ign.fr/#/project/1/map
* Un globe où des projets de bâtiment sont proposés en fonction des règles d'urbanisme : https://demo-simplu3d.ign.fr/#/project/2/globe

### Limites

C'est la v0 d'un démonstrateur, limité à une zone d'un PLU, avec un ensemble de règles propre à Rennes Métropole, etc. Les idées pour la suite étaient les suivantes :

* Télécharger automatiquement les données du géoportail de d'urbanisme et les données du cadastre
* Partager les annotations sur les parcelles
* Finaliser une interface de saisie pour le CSV
* Optimiser/industrialiser le [coeur SimPLU](https://github.com/SimPLU3D/simplu3D-rules), unifier l'implémentation des règles, renforcer les tests, etc.
* Générer des bâtiments plus réaliste
* ...


## IAU IDF

Cette expérimentation à l'échelle de la région île de France s'appuie sur le même principe d'instanciation règles par fichier CSV que le démonstrateur simplu pour Rennes métropôle.

Les règles sont toutefois différentes. Voir [registry/IAUIDF-\*.md](registry/index.md)) pour les règles associées


