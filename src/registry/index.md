# Registre des règles SimPLU

## Règles issues du modèle CartoPLU+ développé par l'IAUIDF

La première règle (IAUIDF-000) définit le nombre de bandes de constructibilité et leurs dimensions. S'il y en a deux, les règles de IAUIDF-001 à IAUIDF-008 sont définies pour les deux bandes.

| Identifiant                 | Titre                                                      | Paramètres           |
| --------------------------- | ---------------------------------------------------------- | -------------------- |
| [IAUIDF-000](IAUIDF-000.md) | Bandes de constructibilité                                 | B1_T_BANDE, B1_BANDE |
| [IAUIDF-001](IAUIDF-001.md) | Distance minimale à la voirie                              | B1_ART_6             |
| [IAUIDF-002](IAUIDF-002.md) | Distance et alignement par rapport aux limites séparatives | B1_ART_71, B1_ART_72 |
| [IAUIDF-003](IAUIDF-003.md) | Distance par rapport au fond de parcelle                   | B1_ART_73            |
| [IAUIDF-004](IAUIDF-004.md) | Contrainte de prospect par rapport aux limites séparatives | B1_ART_74            |
| [IAUIDF-005](IAUIDF-005.md) | Distance minimale entre bâtiments                          | B1_ART_8             |
| [IAUIDF-006](IAUIDF-006.md) | Coefficient d'emprise au sol maximum                       | B1_ART_9             |
| [IAUIDF-007](IAUIDF-007.md) | Hauteur maximale des constructions                         | B1_ART_10_m          |
| [IAUIDF-008](IAUIDF-008.md) | Part d'espace libre dans la parcelle                       | B1_ART_13            |
| [IAUIDF-009](IAUIDF-009.md) | Surface minimale d'une parcelle constructible              | B1_ART_5             |
| [IAUIDF-010](IAUIDF-010.md) | Coefficient d'occupation du sol                            | B1_ART_14            |

## Règles du démonstrateur Rennes Métropole

Les règles ci-dessous ont été proposée par Rennes Métropole dans le cadre d'un démonstrateur SimPLU visant à assister dans l'instruction des permis des construires.

Elles sont conservées pour trace et pour illustrer des formulations des contraintes mais ne sont pas maintenues.

| Identifiant                 | Titre                                                        | Paramètres                                                 |
| --------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| [RENNES-001](RENNES-001.md) | Bande inconstructible en fond de parcelle                    | bandIncons                                                 |
| [RENNES-002](RENNES-002.md) | Coefficient d'emprise au sol (cas 1)                         | empriseSol, empriseSurface, empLargeurMin                  |
| [RENNES-003](RENNES-003.md) | Coefficient d'emprise au sol (cas 2)                         | empriseSolAlt                                              |
| [RENNES-004](RENNES-004.md) | Règle de prospect                                            | largMaxProspect1, prospectVoirie1Hini, prospectVoirie2Hini |
| [RENNES-005](RENNES-005.md) | Développé de facade                                          | Aucun                                                      |
| [RENNES-006](RENNES-006.md) | Bande de constructibilité 1                                  | band1, alignement                                          |
| [RENNES-007](RENNES-007.md) | Recul des façades en distances latérales                     | reculLatMin, reculLatMax                                   |
| [RENNES-008](RENNES-008.md) | Ratio entre la hauteur du bâtiment et la hauteur des façades | hauteurMaxFacade                                           |
| [RENNES-009](RENNES-009.md) | Hauteur des façades en bande de constructibilité secondaire  | band2, hauteurMax2                                         |
| [RENNES-010](RENNES-010.md) | Distance de prospect en bande de constructibilité secondaire | band2, hIniProspectLat                                     |

## Remarque

* Certaines règles ci-dessus sont porteuses de conditions et ne sont donc pas "unitaire". Une règle unitaire serait du type [CORE-0001](CORE-0001.md)
* Il conviendrait d'ajouter un dossier "definitions" pour illustrer les notions de fonds de parcelles, de bandes de constructibilité, etc.
