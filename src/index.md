# Registre de règles SimPLU3D

> ATTENTION : https://mborne.github.io/plu-formel/ a vocation sur le long terme à être remplacé par https://www.geoportail-urbanisme.gouv.fr/schemas/plu-formel/1.0

## Description

L'approche de formalisation des PLU présentée ici a été expérimentée dans le cadre du projet SimPLU3D. Elle résulte des constats suivants :

* De nombreuses informations concernant les restrictions de construction sont prisonnières des PDF (hauteur maximale, recul par rapport à la voirie, etc.)
* Les variantes de rédaction et la complexité des rédactions rendent l'extraction automatique difficile à partir des textes

Elle postule que **pour pouvoir vérifier automatiquement les règles d'urbanisme, il faut formaliser le contenu du règlement**. Qu'importe le format, pour chaque parcelle, il faut par exemple être en mesure de récupérer la hauteur maximale de construction.

## Mise en garde

Formaliser entièrement les documents d'urbanisme est une problématique complexe :

* Le contexte cartographique est complexe (références aux routes, etc.)
* La conditionnelle est complexe (les règles dépendent du type de construction, etc.)

**On se concentre d'abord sur la formalisation de règles "primitives" et on traitera plus tard la composition des règles**.

En outre, des travaux sont en cours pour affiner la modélisation de ce registre de règle avec l'équipe SmartPLU. Ces travaux portent en particulier sur :

* L'utilisation du format XML pour la modélisation des règles d'urbanisme (production des schémas XSD associés)
* La gestion du lien entre les règles dans un tel format et les documents d'urbanisme présents sur le GpU


## Concepts

### Règle d'urbanisme

Une règle sur une zone d'urbanisme est définie à l'aide des propriétés suivantes :

| Propriété  | Type         | Description                                                         | Exemple                                                                                                 |
| ---------- | ------------ | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `id`       | `string`     | Identifiant la règle d'urbanisme dans le registre                   | "IAUIDF-001"                                                                                            |
| `title`    | `string`     | Nom de la règle pour présentation                                   | "Distance minimale à la voirie"                                                                         |
| `template` | `string`     | Règle sous forme de phrase avec des paramètres                      | `Les bâtiments ne doivent pas être construits à une distance inférieure à {{ B1_ART_6 }} de la voirie.` |
| `params`   | `RuleParams` | Valeurs nommées définissants les paramètres de la règle d'urbanisme | `B1_ART_6 de type numérique`                                                                            |

Remarque : 

* On choisit un identifiant sous la forme `{AuteurDuModeleDePhrase}-{NumeroDeLaPhrase}` pour permettre une première étape d'identification des différentes formulations textuelles
* Il convient toutefois de limiter au maximum le nombre de formulation car il faudra préparer des données (calcul des fonds de parcelle, des bandes, etc.) et écrire des codes pour chaque règle dans les outils qui les interprèteront

### Registre de règles

Un registre de règles de recenser et décrire un ensemble de règles connues.

En outre, il permet d'obtenir une fiche descriptive associée à l'identifiant de règle. Par exemple :

https://mborne.github.io/plu-formel/registry/IAUIDF-001



### Exemple de registre

Voir [Registre des règles SimPLU](registry/index.md) pour les règles IAUIDF/CartoPLU+ et les règles du démonstrateur Rennes Métropole.


## Instanciation des règles d'urbanisme

### Principe

Instancier les règles d'urbanisme revient à fournir la liste des règles et leurs paramètres s'appliquant sur les différentes zones d'un PLU. 

On propose dans un premier temps d'annexer ces informations aux zones d'un document d'urbanisme en reprenant ces informations :

| Nom             | Type         | Description                                                                                                     |
| --------------- | ------------ | --------------------------------------------------------------------------------------------------------------- |
| `document.id`   | `string`     | Identifiant le document d'urbanisme sur le Géoportail de L'Urbanisme (ex : `69f0e42b13c577e63186146f9f1e65c5` ) |
| `document.name` | `string`     | Le nom du document (ex : `25392_PLU_20170602`)                                                                  |
| `zone.code`     | ̀`string`     | Libelle de la zone d'urbanisme (équivalent à `ZONE_URBA.LIBELLE` dans le standard CNIG, ex : `UAb`)             |
| `rule.id`       | `string`     | Identifiant de la règle (ex : "IAUIDF-001")                                                                     |
| `rule.citation` | `string`     | Extrait du texte du document d'urbanisme définissant les paramètres (produit par SmartPLU)                      |
| `rule.params`   | `RuleParams` | Liste des valeurs des paramètres nommés de la règle                                                             |

### Format XML

Il est proposé de travailler avec un fichier XML par document d'urbanisme présent sur le GpU (ex : `69f0e42b13c577e63186146f9f1e65c5.xml`)

L'exemple suivant illustre le contenu du fichier XML : [sample/69f0e42b13c577e63186146f9f1e65c5.xml](sample/69f0e42b13c577e63186146f9f1e65c5.xml)

Le fichier XML obéit au schéma suivant : [plu-formel.xsd](plu-formel.xsd) (DRAFT)

Nous remarquerons que :

* Pour exploiter ces données, un outil tel SimPLU devra 
  * Récupérer la géométrie des zones à l'aide d'une jointure attributaire entre `ZONE_URBA.LIBELLE` et `zone.code`
  * Récupérer ensuite les parcelles concernées à l'aide d'une jointure spatiale entre `ZONE_URBA.geometry` et `parcelle.geometry`

* Nous choisissons de dire "une zone est porteuse de règles" et de ne pas fusionner zone/rules en `<rules codeZone="U">...</rules>` pour
  * Que le modèle de règle soit au maximum indépendant du concept de zone d'urbanisme et ainsi ne pas se priver de la possibilité d'instancier à terme des règles sur d'autres éléments
  * Qu'il soit plus naturel d'étendre `ZONE_URBA` avec les règles (ex : [ZONE_URBA.json](sample/69f0e42b13c577e63186146f9f1e65c5/ZONE_URBA.geojson) avec une propriété `rules`
  * Stocker ces informations dans un `LIB_REGLES` au niveau des `ZONE_URBA` serait possible sans les limitations des SIG et leurs formats

* La suppression du support du format CSV permettra de supprimer la contrainte d'unicité du nom des paramètres dans l'ensemble des règles

## Resources

* [Preuves de concepts et démonstrateurs](poc.md)
* [Principe d'instanciation des règles en CSV (ancien fonctionnement)](legacy-csv.md)
* [Relation possible entre ce registre de règle et d'autres projets](projects.md)
