# Instanciation des règles par fichier CSV (déprécié)

Tant que les noms des paramètres des règles d'urbanisme demeurent uniques, il est possible de mettre facilement à plat les informations en définissant des colonnes correspondant au nom des paramètres.

## Colonnes pour l'identification du document d'urbanisme

* **DOCUMENT_ID** : Identifiant du document d'urbanisme sur le GpU (ex : `https://www.geoportail-urbanisme.gouv.fr/document/by-id/69f0e42b13c577e63186146f9f1e65c5`).
* **DOCUMENT_NAME** : Nom de dossier du document d'urbanisme standardisé par le CNIG (ex : `25349_PLU_20010101`).

## Colonnes pour l'identification de la zone d'urbanisme

* **INSEE** : Code INSEE de la commune associé à la zone d'urbanisme (anciennement `ZONE_URBA.INSEE` qui a été migré dans les noms de fichier dans le standard CNIG 2017)
* **NOM_COM** : Nom de la commune associée à la zone d'urbanisme
* **LIBELLE** : Libellé de zone d'urbanisme (`ZONE_URBA.LIBELLE` dans les standards CNIG)

## Colonnes pour l'instanciation des règles

Pour instancier les règles sur les zones d'urbanisme, il suffit d'ajouter des colonnes correspondant aux paramètres de ces règles. Par exemple, on aura :

* Pour IAUIDF-000 : [B1_BANDE](registry/IAUIDF-000.md#B1_BANDE) et [B1_T_BANDE](registry/IAUIDF-000.md#B1_T_BANDE)

* Pour IAUIDF-001 : [B1_ART_6](registry/IAUIDF-001.md#B1_ART_6)

* Pour IAUIDF-002 : [B1_ART_71](registry/IAUIDF-002.md#B1_ART_71) et [B1_ART_72](registry/IAUIDF-002.md#B1_ART_72)

* Pour IAUIDF-003 : [B1_ART_73](registry/IAUIDF-003.md#B1_ART_73)

* Pour IAUIDF-004 : [B1_ART_74](registry/IAUIDF-004.md#B1_ART_74)

* Pour IAUIDF-005 : [B1_ART_8](registry/IAUIDF-005.md#B1_ART_8)

* Pour IAUIDF-006 : [B1_ART_9](registry/IAUIDF-006.md#B1_ART_9)

* Pour IAUIDF-007 : [B1_ART_10](registry/IAUIDF-007.md#B1_ART_10_m)

* Pour IAUIDF-008 : [B1_ART_13](registry/IAUIDF-008.md#B1_ART_13)

* Pour IAUIDF-009 : [B1_ART_5](registry/IAUIDF-009.md#B1_ART_5)

* Pour IAUIDF-010 : [B1_ART_14](registry/IAUIDF-010.md#B1_ART_14)

