# Notes pour discussion SG6

## Niveau 1 : Texte structuré permettant de récupérer la règle textuelle pour une zone données

Point clés :

* Structuration du texte dans un format XML avec réutilisation de balise HTML :

```xml
<plu:Titre id="idelem3x1138" intitule="2. constRuctions, activités, usages et affectations des sols autoRisés sous conditions" niveau="3" idZone="UG" idPrescription="nonConcerne" inseeCommune="15079">
    <plu:Contenu id="idelem16777218x61" idZone="UG" idPrescription="nonConcerne">
        <h3>2. constRuctions, activités, usages et affectations des sols autoRisés sous conditions</h3>
        <div>Sont autorisées, à condition de ne pas excéder une emprise au sol de 300 m² : </div>
        <ul>
            <li>les constructions destinées à la vente directe des produits de la ferme ; </li>
            <li>les commerces et activités de services. </li>
        </ul>
    </plu:Contenu>
</plu:Titre>
```

* Identification des zones d'urbanisme concernée par le texte réglementaire (`idZone`)


## Niveau 2 : Texte structuré permettant d'évaluer les règles sur les zones

Approche possible : étendre le niveau 1 en injectant les identifiants des règles et leurs paramètres dans le document XML en s'inspirant des [microdata HTML5](https://www.tutorialspoint.com/html5/html5_microdata.htm) :

```xml
<!-- ATTENTION : A ALIGNER SUR TRAVAUX SmartPLU pour ruleId et ruleParam -->
<p ruleId="https://github.com/SimPLU3D/plu-formel/blob/master/src/registry/IAUIDF-004.md">
La part d'espace libre dans la parcelle représente au minimum <span ruleParam="B1_ART_74">2</span> fois l'aire de la parcelle.
</p>
```

...où :

* La règle est identifiée par une URL correspondant à une fiche décrivant précisément la contraintes (ruleId par exemple)
* Le texte de la règle est généré à partir d'un modèle "La part d'espace libre dans la parcelle représente au minimum {{ B1_ART_74 }} fois l'aire de la parcelle." dans lequel les valeurs sont injectées.
* On retrouve les même "données" que dans les premiers XML et CSV de SimPLU3D et SmartPLU, mais avec une meilleure articulation avec le texte du règlement d'urbanisme (cohérence à priori assurée).


Remarque :

* Pour chaque règle, les outils tels SimPLU3D devront implémenter un code mettant en oeuvre le contrôle correspondant. Il y a donc un intérêt à construire un **thésaurus de règle**, par exemple via **un dépôt GITHUB ouvert aux contributions** (but : premier recensement pour voir si une homogénéisation de la formulation des contraintes morphologiques est possible)
* Ces modèles peuvent être utilisés pour guider dans la rédaction des documents d'urbanisme (intéressant pour des outils tel [plu-manager](https://www.plan-local-d-urbanisme.fr/outil-logiciel-plu-manager/))
* Ce principe d'encodage d'information s'applique aux contraintes non morphologique
* Ce principe d'encodage d'information dans des attributs HTML pourrait s'appliquer à bien d'autres cas (décrets de fusion de communes,...)


## Niveau 3 : Gérer la conditionnelle

Il faut être conscient que le niveau 2 ne suffira pas. Il sera nécessaire de gérer de la conditionnelle pour être précis dans l'évaluation des règles :

> TODO screenshot conditionnelle de l'éditeur de règle de MBrasebin.

Il faut peut-être dès le niveau 2 s'assurer que cette conditionnelle pourra être ajoutée au modèle. Par exemple :

```xml
<div ruleCondition="<condition-a-formaliser>">
    <p ruleId="https://github.com/SimPLU3D/plu-formel/blob/master/src/registry/IAUIDF-004.md">
    La part d'espace libre dans la parcelle représente au minimum <span ruleParam="B1_ART_74">2</span> fois l'aire de la parcelle.
    </p>
<div>
```

Toutefois, pour standardiser la description des conditions, il faudra une maturité sur les référentiels en jeu dans les conditions ("à moins de 500 mètres de la D14,..." : quelle D14?).


