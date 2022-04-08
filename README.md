# plu-formel

Ce dépôt vise à documenter les principes de modélisation des règles d'urbanisme dans [Simplu3D](https://simplu3d.github.io/).

## Description

L'approche de formalisation des PLU présentée ici a été expérimentée dans le cadre du projet SimPLU3D. Elle résulte des constats suivants :

* De nombreuses informations concernant les restrictions de construction sont prisonnières des PDF (hauteur maximale, recul par rapport à la voirie, etc.)
* Les variantes de rédaction et la complexité des rédactions rendent l'extraction automatique difficile à partir des textes

Elle postule que **pour pouvoir vérifier automatiquement les règles d'urbanisme, il faut formaliser le contenu du règlement**. Qu'importe le format, pour chaque parcelle, il faut par exemple être en mesure de récupérer la hauteur maximale de construction.

## Mise en garde

Formaliser entièrement les documents d'urbanisme est une problématique complexe :

* Le contexte cartographique est complexe (références aux routes, etc.)
* La conditionnelle est complexe (les règles dépendent du type de construction, etc.)

**On se concentre ici sur la formalisation de règles "atomatiques" et on traitera plus tard la composition des règles avec des conditions**.

En outre, des travaux sont à suivre pour affiner la modélisation de ce registre de règles.

## Concepts

### Règle d'urbanisme

Une règle SimpLU3D sur une zone d'urbanisme peut être définie à l'aide des propriétés suivantes :

| Propriété  | Type         | Description                                                         | Exemple                                                                                                 |
| ---------- | ------------ | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `id`       | `string`     | L'identifiant de la règle d'urbanisme dans le registre              | "IAUIDF-001"                                                                                            |
| `title`    | `string`     | Nom de la règle pour présentation                                   | "Distance minimale à la voirie"                                                                         |
| `template` | `string`     | **Règle sous forme de phrase avec des paramètres**                  | `Les bâtiments ne doivent pas être construits à une distance inférieure à {{ B1_ART_6 }} de la voirie.` |
| `params`   | `RuleParams` | Valeurs nommées définissants les paramètres de la règle d'urbanisme | `B1_ART_6 de type numérique`                                                                            |

Face à chacune de ces règles, un outil tel SimPLU3D est capable de vérifier si un "bâtiment" respecte ou non la règle. Le modèle de phrase associé permet surtout de faire le lien avec le règlement sous sa forme textuelle.


### Registre de règles

Un registre de règles permet de recenser et décrire un ensemble de règles connues.

En outre, il permet d'obtenir une fiche descriptive associée à l'identifiant de règle, ce qui guide dans l'implémentation de moteur de vérification ou de simulation tel SimPLU3D.

Exemple : [Registre des règles SimPLU](registry/index.md) pour les règles IAUIDF/CartoPLU+ et les règles du démonstrateur Rennes Métropole.

**NB : Seule une approche collaborative permettra d'étendre et de compléter ce registre de règle qui se limite pour l'instant aux cas traités dans le cadre des expérimentations SimPLU3D.**

## Instanciation des règles d'urbanisme

Instancier les règles d'urbanisme revient à fournir la liste des règles et leurs paramètres correspondant s'appliquant sur les différentes zones d'un PLU.

Plusieurs approches et formats ont été expérimentés dans le temps avec SimPLU3D.

Il est à noter que la notion de registre de règle est compatible avec l'ensemble de ces travaux. Seule une approche où les règles sont formulées directement en [OCL](https://www.cs.montana.edu/courses/se422/currentLectures/OCL-2012.pdf) n'est pas représentée ici.

### Format XML avec éditeur de règle pour Terra-Magna

Le projet Terra-Magna correspond à une étude de faisabilité de l'approche SimPLU3D sur quelques communes (2010)

On notera les points clés suivant :

* Les règles sont instanciées sur les zones d'urbanisme par commune+libellé de zone
* Une interface de saisie permet de saisir les règles et d'exporter le résultat au format XML
* Les phrases auto-générées à partir de paramètre
* Le modèle de règle supporte de la conditionnelle avec par exemple des référence à des routes BDTOPO.

<!--TODO capture d'écran de l'interface -->

* Export XML :

<!--TODO extrait de l'XML correspondant -->




### Format CSV pour IAUIDF

Points clés :

* Approche industrielle appliquées sur toutes les communes de l'île de France
* Règles instanciées par commune et par zone d'urbanisme
* 11 règles unitaires (c.f. [règles CartoPLU+ développées par l'IAUIDF](registry/index.md))
* Saisie des règles par renseignement des paramètres dans un format tabulaire (CSV)
* Pas de conditionnelle (délicat avec format tabulaire)
* Approche reprise pour démonstrateur Rennes-Métropole et premiers tests SmartPLU :

  * [rennes.csv](sample/rennes.csv)
  * [SmartPLU-20180913.csv](sample/SmartPLU-20180913.csv)

### Format XML pour SmartPLU

Dans le cadre des travaux avec SmartPLU, il a été proposé de travailler avec un fichier XML annexé à chaque document d'urbanisme présent sur le GpU en renseignant les informations suivantes :

| Nom             | Type         | Description                                                                                                     |
| --------------- | ------------ | --------------------------------------------------------------------------------------------------------------- |
| `document.id`   | `string`     | Identifiant le document d'urbanisme sur le Géoportail de L'Urbanisme (ex : `69f0e42b13c577e63186146f9f1e65c5` ) |
| `document.name` | `string`     | Le nom du document (ex : `25392_PLU_20170602`)                                                                  |
| `zone.code`     | ̀`string`    | Libelle de la zone d'urbanisme (équivalent à `ZONE_URBA.LIBELLE` dans le standard CNIG, ex : `UAb`)             |
| `rule.id`       | `string`     | Identifiant de la règle (ex : "IAUIDF-001")                                                                     |
| `rule.citation` | `string`     | Extrait du texte du document d'urbanisme définissant les paramètres (produit par SmartPLU)                      |
| `rule.params`   | `RuleParams` | Liste des valeurs des paramètres nommés de la règle                                                             |

L'exemple [sample/69f0e42b13c577e63186146f9f1e65c5.xml](sample/69f0e42b13c577e63186146f9f1e65c5.xml) illustre le contenu du fichier XML stockant ces informations.

Le fichier XML obéit au schéma suivant : [plu-formel.xsd](plu-formel.xsd) (DRAFT)


## Voir aussi

* [Preuves de concepts et démonstrateurs](poc.md)
* [Principe d'instanciation des règles en CSV (ancien fonctionnement)](legacy-csv.md)
* [Relation possible entre ce registre de règle et d'autres projets](projects.md)
* [Documentation de SimPLU3D](https://simplu3d.github.io/simplu3D-tutorial/) : Documentation sur la bibliothèque SimPLU3D
