
## Population résidante dans les agglomérations, de 1980 à 2018
  
  ![alt tag](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Flag_of_Switzerland_%28Pantone%29.svg/200px-Flag_of_Switzerland_%28Pantone%29.svg.png)

# Table of contents 
1.[Introduction](#Introduction)
2.[Visualisations](#Visualisation)
3.[Augmentation](#Augmentation jeu de données)

# Introduction

### Thématique
<p style="text-justify">
  
J'ai décidé dans le cadre de mon cours de datavisualisation d'aborder un sujet qui touche mon pays la Suisse. En effet, la Suisse, appelée également _Confédération Suisse_ est un petit pays d'Europe centrale formé de 26 cantons et dont la capitale est Berne. J'ai donc choisi un sujet sur **la population suisse résidante dans les agglomérations de 1980 à 2018**. Pour mieux définir le sujet, selon wikipédia, _En Suisse comme ailleurs, la notion de ville évolue au cours du temps. Au xxe siècle, la ville, selon sa définition statistique, est une agglomération supérieure à 10 000 habitants, mais d’un point de vue historique, la notion est bien plus complexe et nullement liée à l'importance de la population._ 

</p>



### Jeu de données

Pour cette examen, j'ai utilisé un jeu de données que j'ai trouvé sur le site _opendata swiss_ .Ce jeu de donnée décris la population résidante dans les différantes agglomérations suisse de 1980 à 2018. J'ai décidé de nettoyer mon jeu de données grâce à Openrefine car je trouvais que certaines informations n'étaient pas utiles et certaines colonnes étaient mal nommées.

### Transformations du jeu de données
Voici donc les tranformations apportées à partir de Openrefine:
- J'ai décidé de supprimer deux colonnes qui étaient vides, j'ai renommée les deux colonnes sur la variation de la population _vpop_  afin que le nomage soit plus claire. J'ai également supprimer quelques lignes qui n'étaient pas utiles à mon jeu et qui apportait de l'incompréhension lorsque j'ajoutais mon jeu dans certain graphique.
```
[
  {
    "op": "core/column-move",
    "columnName": "pop2018",
    "index": 3,
    "description": "Move column pop2018 to position 3"
  },
  {
    "op": "core/column-move",
    "columnName": "pop2018",
    "index": 4,
    "description": "Move column pop2018 to position 4"
  },
  {
    "op": "core/column-move",
    "columnName": "pop1980",
    "index": 2,
    "description": "Move column pop1980 to position 2"
  },
  {
    "op": "core/column-removal",
    "columnName": "Column",
    "description": "Remove column Column"
  },
  {
    "op": "core/column-removal",
    "columnName": "Column2",
    "description": "Remove column Column2"
  },
  {
    "op": "core/column-rename",
    "oldColumnName": "vpop_0018",
    "newColumnName": "vpop_2000-2018",
    "description": "Rename column vpop_0018 to vpop_2000-2018"
  },
  {
    "op": "core/column-rename",
    "oldColumnName": "vpop_8099",
    "newColumnName": "vpop_1980-1999",
    "description": "Rename column vpop_8099 to vpop_1980-1999"
  },
  {
    "op": "core/row-removal",
    "engineConfig": {
      "facets": [
        {
          "type": "list",
          "name": "Lignes étoilées",
          "expression": "row.starred",
          "columnName": "",
          "invert": false,
          "omitBlank": false,
          "omitError": false,
          "selection": [
            {
              "v": {
                "v": true,
                "l": "true"
              }
            }
          ],
          "selectBlank": false,
          "selectError": false
        }
      ],
      "mode": "row-based"
    },
    "description": "Remove rows"
  },
  {
    "op": "core/column-rename",
    "oldColumnName": "geo_name",
    "newColumnName": "agglomérations",
    "description": "Rename column geo_name to agglomérations"
  },
  {
    "op": "core/row-removal",
    "engineConfig": {
      "facets": [
        {
          "type": "list",
          "name": "Lignes étoilées",
          "expression": "row.starred",
          "columnName": "",
          "invert": false,
          "omitBlank": false,
          "omitError": false,
          "selection": [
            {
              "v": {
                "v": true,
                "l": "true"
              }
            }
          ],
          "selectBlank": false,
          "selectError": false
        }
      ],
      "mode": "row-based"
    },
    "description": "Remove rows"
  }
]
```
# Visualisations 

### Circle Packing
J'ai utilisé RAWgraph pour ce grahique. Je pense que que le _circle Packing_ est le meilleur graph pour représenter la population résidante en Suisse dans les années 1980. On constate que la population à cette époque est beaucoup plus concentrée dans la ville de Zürich qui est à la fois un canton dans la partie alémanique de la Suisse et que le reste de la population est concentré dans d'autres villes. Ce qui est très visible également, c'est que les plus gros cercles, sont des villes alémaniques , **Zürich, Bâle, Berne** puis **Genève et Lausanne** viennent juste après. Il faut savoir que lorsque l'on parle de population, cela concerne les étrangers de nationalité suisse, ceux qui ne sont pas de nationalité suisse et les suisses d'origine. 

<svg width="645" height="645" xmlns="http://www.w3.org/2000/svg"><g transform="translate(10,10)"><g><circle class="node node--root" transform="translate(312.5,312.5)" r="312.5" style="fill-opacity: 0; stroke: rgb(221, 221, 221); stroke-opacity: 1;"></circle><circle class="node node--leaf" transform="translate(242.04349144599112,296.0229661719081)" r="113.27967516499376" style="fill: rgb(191, 105, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(389.25890233451923,296.0229661719081)" r="28.743817109202237" style="fill: rgb(191, 115, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(410.4416783375464,416.98770634610685)" r="88.86971352284822" style="fill: rgb(191, 126, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(390.3144196393269,208.2745846858465)" r="53.81899389375839" style="fill: rgb(191, 136, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(313.4648250791308,168.90558195103588)" r="27.335937813157745" style="fill: rgb(191, 146, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(304.5632083204737,410.55371184972984)" r="12.012147367160795" style="fill: rgb(191, 156, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(259.8500221226279,156.08004081837385)" r="22.599646703073205" style="fill: rgb(191, 167, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(266.7745623574023,449.78571872544364)" r="37.2673221706224" style="fill: rgb(191, 177, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(217.91960827271623,164.7278750705893)" r="15.021337444246486" style="fill: rgb(191, 187, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(220.0115458789332,423.69660727140854)" r="11.089068680673284" style="fill: rgb(184, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(429.8565405737305,269.99443385193064)" r="14.28928605286282" style="fill: rgb(174, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(318.68889586265897,492.3695900843622)" r="24.68600568274369" style="fill: rgb(163, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(193.9319888749818,416.0976164200818)" r="10.883105833256737" style="fill: rgb(153, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(451.8441771867692,306.9425193035509)" r="23.51434373455558" style="fill: rgb(143, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(185.72073211006267,176.1679623425464)" r="13.957538824301933" style="fill: rgb(132, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(153.36988516521023,408.9526512048458)" r="25.111560568520428" style="fill: rgb(122, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(356.27996039906094,133.9178991310621)" r="22.7647629857286" style="fill: rgb(112, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(105.47782145007997,179.3358778011641)" r="61.15596205182695" style="fill: rgb(105, 191, 108); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(292.5389160593228,118.69185340979271)" r="21.871704253814748" style="fill: rgb(105, 191, 119); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(106.49048284393973,365.2953787486444)" r="33.75614773078586" style="fill: rgb(105, 191, 129); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(224.53669746976058,127.3874695586205)" r="17.70892416935545" style="fill: rgb(105, 191, 139); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(199.8035539935235,443.72979622132044)" r="12.174093016665793" style="fill: rgb(105, 191, 150); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(213.44300865680734,474.558270733266)" r="16.34495934649621" style="fill: rgb(105, 191, 160); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(106.73851614158315,265.83473976714356)" r="20.160167933464077" style="fill: rgb(105, 191, 170); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(93.7026817425826,308.5046190155508)" r="19.2646319952771" style="fill: rgb(105, 191, 180); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(180.67714244567276,134.00891709060352)" r="21.45571405213766" style="fill: rgb(105, 191, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(161.6869123195944,464.85317346419885)" r="26.212371067808903" style="fill: rgb(105, 180, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(449.2653240878619,246.30586854466944)" r="11.143115795711651" style="fill: rgb(105, 170, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(328.7838782033989,105.70771508662594)" r="11.436833347599965" style="fill: rgb(105, 160, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(260.5752580691709,123.09461299230338)" r="5.20183426564856" style="fill: rgb(105, 150, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(251.31079870005738,95.37954068669657)" r="18.828763101826397" style="fill: rgb(105, 139, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(466.0895312227143,268.9465718442296)" r="11.872329727981167" style="fill: rgb(105, 129, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(396.2257731273336,137.37151811306165)" r="12.13814897191025" style="fill: rgb(105, 119, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(112.02973669253518,415.4889230493212)" r="11.550203156550966" style="fill: rgb(105, 108, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(487.14123833373463,336.3438144719198)" r="17.23194270083288" style="fill: rgb(112, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(64.22658200560736,277.08689763230717)" r="18.623765923805824" style="fill: rgb(122, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(477.81715394048774,211.66306045474502)" r="28.557405268465924" style="fill: rgb(132, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(287.4931397699139,73.80573194195884)" r="18.1052132778941" style="fill: rgb(143, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(188.66595557187424,539.9174306820141)" r="48.36106298724002" style="fill: rgb(153, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(39.43170348174482,238.31971840559333)" r="22.202574731517807" style="fill: rgb(163, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(245.52053497154645,502.5887292264708)" r="14.460804876396585" style="fill: rgb(174, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(60.722624020017065,333.3765127604591)" r="16.85077689825266" style="fill: rgb(184, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(201.52200812510515,103.80655610774014)" r="10.049656526776738" style="fill: rgb(191, 105, 187); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(278.38385808662065,502.72241921585845)" r="11.735500714016885" style="fill: rgb(191, 105, 177); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(125.22367263975042,441.13177180268286)" r="12.0959717508288" style="fill: rgb(191, 105, 167); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(214.45597718258782,70.61343029963572)" r="20.38244984895323" style="fill: rgb(191, 105, 156); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(145.77136016188868,102.6674331015181)" r="20.26401040303945" style="fill: rgb(191, 105, 146); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(506.7517796576215,261.8803041706093)" r="24.207419743885563" style="fill: rgb(191, 105, 136); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(564.0859821426156,324.41450038614494)" r="55.44013636265397" style="fill: rgb(191, 105, 126); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(426.65115424315456,144.92606243005756)" r="14.019174125167687" style="fill: rgb(191, 105, 115); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle></g><g><text text-anchor="middle" transform="translate(312.5,312.5)" style="font-size: 11px; font-family: Arial, Helvetica;"></text><text text-anchor="middle" transform="translate(242.04349144599112,296.0229661719081)" style="font-size: 11px; font-family: Arial, Helvetica;">Rest der Schweiz / Reste de la Suisse</text><text text-anchor="middle" transform="translate(389.25890233451923,296.0229661719081)" style="font-size: 11px; font-family: Arial, Helvetica;">Winterthur</text><text text-anchor="middle" transform="translate(410.4416783375464,416.98770634610685)" style="font-size: 11px; font-family: Arial, Helvetica;">Zürich</text><text text-anchor="middle" transform="translate(390.3144196393269,208.2745846858465)" style="font-size: 11px; font-family: Arial, Helvetica;">Bern</text><text text-anchor="middle" transform="translate(313.4648250791308,168.90558195103588)" style="font-size: 11px; font-family: Arial, Helvetica;">Biel/Bienne</text><text text-anchor="middle" transform="translate(304.5632083204737,410.55371184972984)" style="font-size: 11px; font-family: Arial, Helvetica;">Interlaken</text><text text-anchor="middle" transform="translate(259.8500221226279,156.08004081837385)" style="font-size: 11px; font-family: Arial, Helvetica;">Thun</text><text text-anchor="middle" transform="translate(266.7745623574023,449.78571872544364)" style="font-size: 11px; font-family: Arial, Helvetica;">Luzern</text><text text-anchor="middle" transform="translate(217.91960827271623,164.7278750705893)" style="font-size: 11px; font-family: Arial, Helvetica;">Altdorf (UR)</text><text text-anchor="middle" transform="translate(220.0115458789332,423.69660727140854)" style="font-size: 11px; font-family: Arial, Helvetica;">Lachen</text><text text-anchor="middle" transform="translate(429.8565405737305,269.99443385193064)" style="font-size: 11px; font-family: Arial, Helvetica;">Glarus</text><text text-anchor="middle" transform="translate(318.68889586265897,492.3695900843622)" style="font-size: 11px; font-family: Arial, Helvetica;">Zug</text><text text-anchor="middle" transform="translate(193.9319888749818,416.0976164200818)" style="font-size: 11px; font-family: Arial, Helvetica;">Bulle</text><text text-anchor="middle" transform="translate(451.8441771867692,306.9425193035509)" style="font-size: 11px; font-family: Arial, Helvetica;">Fribourg</text><text text-anchor="middle" transform="translate(185.72073211006267,176.1679623425464)" style="font-size: 11px; font-family: Arial, Helvetica;">Grenchen</text><text text-anchor="middle" transform="translate(153.36988516521023,408.9526512048458)" style="font-size: 11px; font-family: Arial, Helvetica;">Olten – Zofingen</text><text text-anchor="middle" transform="translate(356.27996039906094,133.9178991310621)" style="font-size: 11px; font-family: Arial, Helvetica;">Solothurn</text><text text-anchor="middle" transform="translate(105.47782145007997,179.3358778011641)" style="font-size: 11px; font-family: Arial, Helvetica;">Basel (CH)</text><text text-anchor="middle" transform="translate(292.5389160593228,118.69185340979271)" style="font-size: 11px; font-family: Arial, Helvetica;">Schaffhausen (CH)</text><text text-anchor="middle" transform="translate(106.49048284393973,365.2953787486444)" style="font-size: 11px; font-family: Arial, Helvetica;">St. Gallen</text><text text-anchor="middle" transform="translate(224.53669746976058,127.3874695586205)" style="font-size: 11px; font-family: Arial, Helvetica;">Rheintal (CH)</text><text text-anchor="middle" transform="translate(199.8035539935235,443.72979622132044)" style="font-size: 11px; font-family: Arial, Helvetica;">Buchs (SG) (CH)</text><text text-anchor="middle" transform="translate(213.44300865680734,474.558270733266)" style="font-size: 11px; font-family: Arial, Helvetica;">Rapperswil-Jona – Rüti</text><text text-anchor="middle" transform="translate(106.73851614158315,265.83473976714356)" style="font-size: 11px; font-family: Arial, Helvetica;">Wil (SG)</text><text text-anchor="middle" transform="translate(93.7026817425826,308.5046190155508)" style="font-size: 11px; font-family: Arial, Helvetica;">Chur</text><text text-anchor="middle" transform="translate(180.67714244567276,134.00891709060352)" style="font-size: 11px; font-family: Arial, Helvetica;">Aarau</text><text text-anchor="middle" transform="translate(161.6869123195944,464.85317346419885)" style="font-size: 11px; font-family: Arial, Helvetica;">Baden – Brugg</text><text text-anchor="middle" transform="translate(449.2653240878619,246.30586854466944)" style="font-size: 11px; font-family: Arial, Helvetica;">Wohlen (AG)</text><text text-anchor="middle" transform="translate(328.7838782033989,105.70771508662594)" style="font-size: 11px; font-family: Arial, Helvetica;">Lenzburg</text><text text-anchor="middle" transform="translate(260.5752580691709,123.09461299230338)" style="font-size: 11px; font-family: Arial, Helvetica;">Stein (AG) (CH)</text><text text-anchor="middle" transform="translate(251.31079870005738,95.37954068669657)" style="font-size: 11px; font-family: Arial, Helvetica;">Arbon – Rorschach</text><text text-anchor="middle" transform="translate(466.0895312227143,268.9465718442296)" style="font-size: 11px; font-family: Arial, Helvetica;">Amriswil – Romanshorn</text><text text-anchor="middle" transform="translate(396.2257731273336,137.37151811306165)" style="font-size: 11px; font-family: Arial, Helvetica;">Frauenfeld</text><text text-anchor="middle" transform="translate(112.02973669253518,415.4889230493212)" style="font-size: 11px; font-family: Arial, Helvetica;">Kreuzlingen (CH)</text><text text-anchor="middle" transform="translate(487.14123833373463,336.3438144719198)" style="font-size: 11px; font-family: Arial, Helvetica;">Bellinzona</text><text text-anchor="middle" transform="translate(64.22658200560736,277.08689763230717)" style="font-size: 11px; font-family: Arial, Helvetica;">Locarno (CH)</text><text text-anchor="middle" transform="translate(477.81715394048774,211.66306045474502)" style="font-size: 11px; font-family: Arial, Helvetica;">Lugano (CH)</text><text text-anchor="middle" transform="translate(287.4931397699139,73.80573194195884)" style="font-size: 11px; font-family: Arial, Helvetica;">Chiasso – Mendrisio (CH)</text><text text-anchor="middle" transform="translate(188.66595557187424,539.9174306820141)" style="font-size: 11px; font-family: Arial, Helvetica;">Lausanne</text><text text-anchor="middle" transform="translate(39.43170348174482,238.31971840559333)" style="font-size: 11px; font-family: Arial, Helvetica;">Vevey – Montreux</text><text text-anchor="middle" transform="translate(245.52053497154645,502.5887292264708)" style="font-size: 11px; font-family: Arial, Helvetica;">Yverdon-les-Bains</text><text text-anchor="middle" transform="translate(60.722624020017065,333.3765127604591)" style="font-size: 11px; font-family: Arial, Helvetica;">Brig – Visp</text><text text-anchor="middle" transform="translate(201.52200812510515,103.80655610774014)" style="font-size: 11px; font-family: Arial, Helvetica;">Martigny</text><text text-anchor="middle" transform="translate(278.38385808662065,502.72241921585845)" style="font-size: 11px; font-family: Arial, Helvetica;">Monthey</text><text text-anchor="middle" transform="translate(125.22367263975042,441.13177180268286)" style="font-size: 11px; font-family: Arial, Helvetica;">Sierre</text><text text-anchor="middle" transform="translate(214.45597718258782,70.61343029963572)" style="font-size: 11px; font-family: Arial, Helvetica;">Sion</text><text text-anchor="middle" transform="translate(145.77136016188868,102.6674331015181)" style="font-size: 11px; font-family: Arial, Helvetica;">La Chaux-de-Fonds – Le Locle (CH)</text><text text-anchor="middle" transform="translate(506.7517796576215,261.8803041706093)" style="font-size: 11px; font-family: Arial, Helvetica;">Neuchâtel</text><text text-anchor="middle" transform="translate(564.0859821426156,324.41450038614494)" style="font-size: 11px; font-family: Arial, Helvetica;">Genève (CH)</text><text text-anchor="middle" transform="translate(426.65115424315456,144.92606243005756)" style="font-size: 11px; font-family: Arial, Helvetica;">Delémont (CH)</text></g></g></svg> 

### Carte de la Suisse

Cette carte provient du site **_map.geo.admin.ch_**. Elle représente la population résidante en Suisse dans les années 2000. Le site contenait déjà des données qui permettaient de représenter la population mais uniquement entre 1990 et 2017. Etant donné que je n'ai pas réussi à entrer mon jeux données sur le site et que mon sujet se focalise sur les années 1980 à 2018, j'ai décidé d'utiliser celui qui était déjà sur le site pour ce map. Les zones en rouges sont les zones qui contiennent plus de 120'000 habitants. On peut voir que la population est plus dense dans les régions du nord de la Suisse comme vu antérieurement pour les années 1980. Comme par exemple dans le canton de Zürich, la population est très dense car c'est une ville assez cosmopolite et elle est le centre économique et financier majeur du pays. La région de Berne, capitale du pays est également très dense à cette même époque. On peut donc constater que de 1980 à 2000 la densité de la population n'a pas tellement changé.

<center><iframe src='https://map.geo.admin.ch/embed.html?topic=ech&lang=fr&bgLayer=ch.swisstopo.pixelkarte-farbe&layers=ch.swisstopo.zeitreihen,ch.bfs.gebaeude_wohnungs_register,ch.bav.haltestellen-oev,ch.swisstopo.swisstlm3d-wanderwege,ch.bfs.volkszaehlung-bevoelkerungsstatistik_einwohner&layers_opacity=1,1,1,0.8,1&layers_visibility=false,false,false,false,true&layers_timestamp=18641231,,,,2000&catalogNodes=688&E=2622720.54&N=1224537.07&zoom=1' width='600' height='400' frameborder='0' style='border:0'></iframe></center>

### Diagramme en barre
Pour ce graphique, j'ai choisi un diagramme en barre afin de montrer la variation de la population résidante en agglomération entre 2000-2018. Pour mieux comprendre le terme de variation, selon le site de l'[Insee](https://www.insee.fr/fr/metadonnees/definition/c1020) _L'accroissement total (ou variation totale) de population est la variation de l'effectif d'une population au cours de l'année, qu'il s'agisse d'une augmentation ou d'une diminution. C'est la somme de l'accroissement naturel, du solde migratoire, et parfois d'un ajustement destiné à rétablir la cohérence entre les différences sources statistiques._ Ainsi sur ce diagramme, on constate que certaine ville ont obtenu une augmentation de sa population comme la ville de Bulle avec 56,4%. Selon le site de la RTS (radio télévision suisse), cela s'explique par le fait que Bulle est devenu un important pôle économique.

<iframe title="Variation de la population résidante dans les agglomérations entre 2000-2018" aria-label="Histogramme" id="datawrapper-chart-kl7zb" src="https://datawrapper.dwcdn.net/kl7zb/2/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="1289"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"])for(var e in a.data["datawrapper-height"]){var t=document.getElementById("datawrapper-chart-"+e)||document.querySelector("iframe[src*='"+e+"']");t&&(t.style.height=a.data["datawrapper-height"][e]+"px")}}))}();
</script>

# Augmentation jeu de données
j'ai décidé d'ajouter des municipalités et villes dans ma colonne _agglomérations_ afin d'enrichir mon jeu de données grâce à wikidata. Il faut savoir qu'en Suisse certains cantons sont également des villes comme par exemple Zürich qui est une ville qui fait parti du canton de Zürich, idem pour Berne et autres.
```
[
  {
    "op": "core/recon",
    "engineConfig": {
      "facets": [],
      "mode": "record-based"
    },
    "columnName": "agglomérations",
    "config": {
      "mode": "standard-service",
      "service": "https://wdreconcile.toolforge.org/en/api",
      "identifierSpace": "http://www.wikidata.org/entity/",
      "schemaSpace": "http://www.wikidata.org/prop/direct/",
      "type": {
        "id": "Q54935504",
        "name": "city of Switzerland"
      },
      "autoMatch": false,
      "columnDetails": [
        {
          "column": "geo_nr",
          "propertyName": "coordinate location",
          "propertyID": "P625"
        }
      ],
      "limit": 0
    },
    "description": "Reconcile cells in column agglomérations to type Q54935504"
  },
  {
    "op": "core/recon-judge-similar-cells",
    "engineConfig": {
      "facets": [],
      "mode": "record-based"
    },
    "columnName": "agglomérations",
    "similarValue": "Olten – Zofingen",
    "judgment": "new",
    "shareNewTopics": true,
    "description": "Mark to create one single new item for all cells containing \"Olten – Zofingen\" in column agglomérations"
  },
  {
    "op": "core/recon-judge-similar-cells",
    "engineConfig": {
      "facets": [],
```
