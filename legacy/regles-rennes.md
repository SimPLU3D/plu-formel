<h1>{{rule.nomZone}}</h1>

<div class="well">

    <p>
        Une bande de <b>{{rule.bandIncons}}</b> m (par rapport au fond de la parcelle) est inconstructible.
    </p>

    <hr />

    <p>
        Le coefficient d'emprise au sol peut atteindre un ratio de <b>{{rule.empriseSol}}</b> de la superficie du terrain pour les terrains cumulant les caractéristiques suivantes :

        <ul>
            <li>superficie supérieure ou égale à <b>{{rule.empriseSurface}}</b> m²</li>
            <li>largeur de façade supérieure ou égale à <b>{{rule.empLargeurMin}}</b> mètres</li>
        </ul>
    </p>

    <hr />

    <p>
    Pour les terrains dont l'une des caractéristiques en matière de superficie et de largeur de façade ne répond pas aux critères fixés ci-dessus, le coefficient d'emprise au sol, y compris les constructions annexes, est limité à <b>{{rule.empriseSolAlt}}</b> de la superficie du terrain.
    </p>

    <hr />

    <p>
    Si la largeur de la rue est inférieure à <b>{{rule.largMaxProspect1}}</b>, le gabarit 3D de bâtiment doit se trouver sous un prospect mesuré à partir de l'autre côté de la voirie défini par un angle de <b>{{rule.prospectVoirie1Hini}}</b> et une hauteur initiale de <b>{{rule.prospectVoirie1Hini}}</b>. Dans le cas contraire, le gabarit 3D doit se trouver sous un prospect défini par un angle de <b>{{rule.prospectVoirie2Hini}}</b> et une hauteur initiale de <b>{{rule.prospectVoirie2Hini}}</b>.
    </p>

    <p>
    Les contraintes sont relatives à la voie ou la marge de recul.
    <p>

    <hr />

    <p>
        Le développé de façade doit être supérieur à 50% de la superficie du plan vertical lorsque la façade est implantée sur l'alignement ou la marge de recul.
        Le gabarit 3D respecte la règle des 45° (cf. coupes précédentes). Si la hauteur de la façade est sous le plan incliné des 45°, le plan des 45° est décalé d'autant (cf. tirets rouges sur la coupe précédente pour une hauteur de façade égale à Y).
        La hauteur maximale est inférieure à la hauteur de la façade + 6 m
    </p>

    <hr />

    <p>
        Dans la bande de constructibilité maximale définie par une profondeur de <b>{{rule.band1}}</b> m, les bâtiments doivent s'aligner sur une ligne à une distance de <b>{{rule.alignement}}</b> de la voirie.
    </p>

    <hr />

    <p>
        En distance latéral, les façades du bâtiment doivent vérifier un recul compris entre <b>{{rule.reculLatMin}}</b> et <b>{{rule.reculLatMax}}</b> m.
    </p>

    <hr />

    <p>
        La hauteur maximale du bâtiment est inférieure à la hauteur de la façade + <b>{{rule.hauteurMaxFacade}}</b> m.
    </p>

    <hr />

    <p>
        Dans la bande de constructibilité secondaire (définie par une profondeur de <b>{{rule.band2}}</b> m par rapport à la bande de constructibilité principale), la hauteur maximale des façades est fixée à <b>{{rule.hauteurMax2}}</b> m.
    </p>

    <hr />

    <p>
        Dans la bande de constructibilité secondaire (définie par une profondeur de <b>{{rule.band2}}</b> m par rapport à la bande de constructibilité principale), les bâtiments doivent se trouver sous une contrainte de prospect observée à partir des limites latérales définie par la pente <b>{{rule.slopeProspectLat}}</b> et la hauteur initiale <b>{{rule.hIniProspectLat}}</b>.
    </p>
</div>
