# IAUIDF-008 - Part d'espace libre dans la parcelle

## Modèle de phrase

> La part d'espace libre dans la parcelle représente au minimum {{B1_ART_13}} fois l'aire de la parcelle.

## Paramètres

### B1_ART_13

Part minimale d'espaces libres de toute construction exprimée par rapport à la surface totale de la parcelle.

Ratio compris entre 0 et 1.

Remarque : Si valeur exprimée en %, convertir en ratio. Ex : 5%= 5/100 = 0,05 ; 85%= 85/100 = 0.85

## Explications

![Image montrant la contrainte de hauteur maximale d'un bâtiment](img/IAUIDF/IAUIDF-008.png)

## Implémentation

La vérification du ratio s'effectue dans la classe PredicateIAUIDF. Seule la valeur de la première bande est prise en compte.
