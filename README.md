
## Population résidante dans les agglomérations, de 1980 à 2018
  
  ![alt tag](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Flag_of_Switzerland_%28Pantone%29.svg/200px-Flag_of_Switzerland_%28Pantone%29.svg.png)

 
# Introduction

### Thématique
<p class="text-justify">
  
J'ai décidé dans le cadre de mon cours de datavisualisation d'aborder un sujet qui touche mon pays la Suisse. En effet, la Suisse, appelée également _Confédération Suisse_ est un petit pays d'Europe centrale formé de 26 cantons et dont la capitale est Berne. J'ai donc choisi un sujet sur **la population suisse résidante dans les agglomérations de 1980 à 2018**. Pour mieux définir le sujet, selon wikipédia, _En Suisse comme ailleurs, la notion de ville évolue au cours du temps. Au xxe siècle, la ville, selon sa définition statistique, est une agglomération supérieure à 10 000 habitants, mais d’un point de vue historique, la notion est bien plus complexe et nullement liée à l'importance de la population._ 

</p>



### Jeu de données

Pour cette examen, j'ai utilisé un jeu de données que j'ai trouvé sur le site _opendata swiss_ .Ce jeu de donnée décris la population résidante dans les différantes agglomérations suisse de 1980 à 2018. J'ai décidé de nettoyer mon jeu de données grâce à Openrefine car je trouvais que certaines informations n'étaient pas utiles et certaines colonnes étaient mal nommées.

### transformations du jeu de données
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

<svg width="848" height="848" xmlns="http://www.w3.org/2000/svg"><g transform="translate(10,10)"><g><circle class="node node--root" transform="translate(414,414)" r="414.00000000000006" style="fill-opacity: 0; stroke: rgb(221, 221, 221); stroke-opacity: 1;"></circle><circle class="node node--leaf" transform="translate(407.90606708007715,363.8745889967922)" r="162.52082649661367" style="fill: rgb(191, 105, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(616.3507333191051,363.8745889967922)" r="41.23836784004702" style="fill: rgb(191, 115, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(648.3180650465048,534.32687352435)" r="127.50018281049833" style="fill: rgb(191, 126, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(619.058950985863,240.767147694445)" r="77.21338674471029" style="fill: rgb(191, 136, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(511.40413395791205,185.2707018161425)" r="39.21850234813635" style="fill: rgb(191, 146, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(499.24861366967536,524.1076684571292)" r="17.233666280086403" style="fill: rgb(191, 156, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(437.43581279501547,166.4410197391136)" r="32.42340918938253" style="fill: rgb(191, 167, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(449.3548329883209,580.6202273307282)" r="53.46692592173677" style="fill: rgb(191, 177, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(379.7758482578105,177.2252524887374)" r="21.55091081403353" style="fill: rgb(191, 187, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(384.178562377384,545.4464527464794)" r="15.909337702776721" style="fill: rgb(184, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(672.3764622466128,328.190838151031)" r="20.500646527943527" style="fill: rgb(174, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(519.9269345344933,642.0592285867906)" r="35.416680358732265" style="fill: rgb(163, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(348.98350272738423,536.9391331788952)" r="15.61384557551754" style="fill: rgb(153, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(320.0955831972755,183.1344142917799)" r="33.735712718978576" style="fill: rgb(143, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(678.7590275620262,385.19157312477535)" r="20.024693240691008" style="fill: rgb(132, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(292.92459954838756,531.4547919019196)" r="36.02721823020279" style="fill: rgb(122, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(570.7479079705604,136.89297481107081)" r="32.66029929951144" style="fill: rgb(112, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(198.83919422987535,217.96889243109266)" r="87.73963628852188" style="fill: rgb(105, 191, 108); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(483.18679335985524,115.47590318272069)" r="31.379039947299702" style="fill: rgb(105, 191, 119); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(223.4625439799954,475.5857367440582)" r="48.42949117358029" style="fill: rgb(105, 191, 129); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(356.31944250993695,582.0526464571802)" r="25.406755344041628" style="fill: rgb(105, 191, 139); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(384.8584040066894,620.0962184675019)" r="17.46600752547529" style="fill: rgb(105, 191, 150); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(390.13147000090265,128.6301176676622)" r="23.44989335621795" style="fill: rgb(105, 191, 160); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(213.43286886713264,338.43679132038983)" r="28.923521806404445" style="fill: rgb(105, 191, 170); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(719.4196214352895,352.2200600983191)" r="27.638708439667816" style="fill: rgb(105, 191, 180); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(190.28984587083994,398.5253048321817)" r="30.78222439947454" style="fill: rgb(105, 191, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(327.8758489571038,107.50583632380767)" r="37.60653624907894" style="fill: rgb(105, 180, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(310.36253508444486,585.4062466814604)" r="15.986878371859673" style="fill: rgb(105, 170, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(699.77055791831,296.89136924396405)" r="16.408270993439174" style="fill: rgb(105, 160, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(522.0774534014205,135.02484162283497)" r="7.4630016630985265" style="fill: rgb(105, 150, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(426.71878263700694,87.36570312374653)" r="27.01337320009729" style="fill: rgb(105, 139, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(533.1775995612206,97.57973923391233)" r="17.033071793518697" style="fill: rgb(105, 129, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(717.9841541888659,401.9379612665787)" r="17.414439087864626" style="fill: rgb(105, 119, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(624.3783790685321,142.4411530900602)" r="16.570921133666392" style="fill: rgb(105, 108, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(231.15295929635099,553.0422940945475)" r="24.72243644592555" style="fill: rgb(112, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(259.307175350143,115.30923491613612)" r="26.71926650573353" style="fill: rgb(122, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(761.6670713715284,292.32577421140246)" r="40.97092527913665" style="fill: rgb(132, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(726.3925660234468,229.98148679935804)" r="25.975305998494875" style="fill: rgb(143, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(99.65311765845024,345.81245036895274)" r="69.38296667511875" style="fill: rgb(153, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(416.00048868629887,664.21802472442)" r="31.853735371887637" style="fill: rgb(163, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(269.02978615272553,588.0789675388413)" r="20.74672227736489" style="fill: rgb(174, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(326.3626905123626,627.3029308559421)" r="24.1755829951423" style="fill: rgb(184, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(363.3936729558706,649.7036495807013)" r="14.418107064307394" style="fill: rgb(191, 105, 187); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(161.86616352035838,442.4326044379246)" r="16.836765047354373" style="fill: rgb(191, 105, 177); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(469.6049834785495,669.788318013497)" r="17.353927996007208" style="fill: rgb(191, 105, 167); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(375.5879571187668,54.20733633000117)" r="29.242426681157397" style="fill: rgb(191, 105, 156); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(764.736360454232,422.7429410424764)" r="29.07250320095963" style="fill: rgb(191, 105, 146); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(477.79108958070583,44.88725168552514)" r="34.730059548603776" style="fill: rgb(191, 105, 136); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(185.86487027821448,652.1304636301626)" r="79.53921804260132" style="fill: rgb(191, 105, 126); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(665.0996748797997,149.73585830049257)" r="20.113120577929394" style="fill: rgb(191, 105, 115); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle></g><g><text text-anchor="middle" transform="translate(414,414)" style="font-size: 11px; font-family: Arial, Helvetica;"></text><text text-anchor="middle" transform="translate(407.90606708007715,363.8745889967922)" style="font-size: 11px; font-family: Arial, Helvetica;">Rest der Schweiz / Reste de la Suisse</text><text text-anchor="middle" transform="translate(616.3507333191051,363.8745889967922)" style="font-size: 11px; font-family: Arial, Helvetica;">Winterthur</text><text text-anchor="middle" transform="translate(648.3180650465048,534.32687352435)" style="font-size: 11px; font-family: Arial, Helvetica;">Zürich</text><text text-anchor="middle" transform="translate(619.058950985863,240.767147694445)" style="font-size: 11px; font-family: Arial, Helvetica;">Bern</text><text text-anchor="middle" transform="translate(511.40413395791205,185.2707018161425)" style="font-size: 11px; font-family: Arial, Helvetica;">Biel/Bienne</text><text text-anchor="middle" transform="translate(499.24861366967536,524.1076684571292)" style="font-size: 11px; font-family: Arial, Helvetica;">Interlaken</text><text text-anchor="middle" transform="translate(437.43581279501547,166.4410197391136)" style="font-size: 11px; font-family: Arial, Helvetica;">Thun</text><text text-anchor="middle" transform="translate(449.3548329883209,580.6202273307282)" style="font-size: 11px; font-family: Arial, Helvetica;">Luzern</text><text text-anchor="middle" transform="translate(379.7758482578105,177.2252524887374)" style="font-size: 11px; font-family: Arial, Helvetica;">Altdorf (UR)</text><text text-anchor="middle" transform="translate(384.178562377384,545.4464527464794)" style="font-size: 11px; font-family: Arial, Helvetica;">Lachen</text><text text-anchor="middle" transform="translate(672.3764622466128,328.190838151031)" style="font-size: 11px; font-family: Arial, Helvetica;">Glarus</text><text text-anchor="middle" transform="translate(519.9269345344933,642.0592285867906)" style="font-size: 11px; font-family: Arial, Helvetica;">Zug</text><text text-anchor="middle" transform="translate(348.98350272738423,536.9391331788952)" style="font-size: 11px; font-family: Arial, Helvetica;">Bulle</text><text text-anchor="middle" transform="translate(320.0955831972755,183.1344142917799)" style="font-size: 11px; font-family: Arial, Helvetica;">Fribourg</text><text text-anchor="middle" transform="translate(678.7590275620262,385.19157312477535)" style="font-size: 11px; font-family: Arial, Helvetica;">Grenchen</text><text text-anchor="middle" transform="translate(292.92459954838756,531.4547919019196)" style="font-size: 11px; font-family: Arial, Helvetica;">Olten – Zofingen</text><text text-anchor="middle" transform="translate(570.7479079705604,136.89297481107081)" style="font-size: 11px; font-family: Arial, Helvetica;">Solothurn</text><text text-anchor="middle" transform="translate(198.83919422987535,217.96889243109266)" style="font-size: 11px; font-family: Arial, Helvetica;">Basel (CH)</text><text text-anchor="middle" transform="translate(483.18679335985524,115.47590318272069)" style="font-size: 11px; font-family: Arial, Helvetica;">Schaffhausen (CH)</text><text text-anchor="middle" transform="translate(223.4625439799954,475.5857367440582)" style="font-size: 11px; font-family: Arial, Helvetica;">St. Gallen</text><text text-anchor="middle" transform="translate(356.31944250993695,582.0526464571802)" style="font-size: 11px; font-family: Arial, Helvetica;">Rheintal (CH)</text><text text-anchor="middle" transform="translate(384.8584040066894,620.0962184675019)" style="font-size: 11px; font-family: Arial, Helvetica;">Buchs (SG) (CH)</text><text text-anchor="middle" transform="translate(390.13147000090265,128.6301176676622)" style="font-size: 11px; font-family: Arial, Helvetica;">Rapperswil-Jona – Rüti</text><text text-anchor="middle" transform="translate(213.43286886713264,338.43679132038983)" style="font-size: 11px; font-family: Arial, Helvetica;">Wil (SG)</text><text text-anchor="middle" transform="translate(719.4196214352895,352.2200600983191)" style="font-size: 11px; font-family: Arial, Helvetica;">Chur</text><text text-anchor="middle" transform="translate(190.28984587083994,398.5253048321817)" style="font-size: 11px; font-family: Arial, Helvetica;">Aarau</text><text text-anchor="middle" transform="translate(327.8758489571038,107.50583632380767)" style="font-size: 11px; font-family: Arial, Helvetica;">Baden – Brugg</text><text text-anchor="middle" transform="translate(310.36253508444486,585.4062466814604)" style="font-size: 11px; font-family: Arial, Helvetica;">Wohlen (AG)</text><text text-anchor="middle" transform="translate(699.77055791831,296.89136924396405)" style="font-size: 11px; font-family: Arial, Helvetica;">Lenzburg</text><text text-anchor="middle" transform="translate(522.0774534014205,135.02484162283497)" style="font-size: 11px; font-family: Arial, Helvetica;">Stein (AG) (CH)</text><text text-anchor="middle" transform="translate(426.71878263700694,87.36570312374653)" style="font-size: 11px; font-family: Arial, Helvetica;">Arbon – Rorschach</text><text text-anchor="middle" transform="translate(533.1775995612206,97.57973923391233)" style="font-size: 11px; font-family: Arial, Helvetica;">Amriswil – Romanshorn</text><text text-anchor="middle" transform="translate(717.9841541888659,401.9379612665787)" style="font-size: 11px; font-family: Arial, Helvetica;">Frauenfeld</text><text text-anchor="middle" transform="translate(624.3783790685321,142.4411530900602)" style="font-size: 11px; font-family: Arial, Helvetica;">Kreuzlingen (CH)</text><text text-anchor="middle" transform="translate(231.15295929635099,553.0422940945475)" style="font-size: 11px; font-family: Arial, Helvetica;">Bellinzona</text><text text-anchor="middle" transform="translate(259.307175350143,115.30923491613612)" style="font-size: 11px; font-family: Arial, Helvetica;">Locarno (CH)</text><text text-anchor="middle" transform="translate(761.6670713715284,292.32577421140246)" style="font-size: 11px; font-family: Arial, Helvetica;">Lugano (CH)</text><text text-anchor="middle" transform="translate(726.3925660234468,229.98148679935804)" style="font-size: 11px; font-family: Arial, Helvetica;">Chiasso – Mendrisio (CH)</text><text text-anchor="middle" transform="translate(99.65311765845024,345.81245036895274)" style="font-size: 11px; font-family: Arial, Helvetica;">Lausanne</text><text text-anchor="middle" transform="translate(416.00048868629887,664.21802472442)" style="font-size: 11px; font-family: Arial, Helvetica;">Vevey – Montreux</text><text text-anchor="middle" transform="translate(269.02978615272553,588.0789675388413)" style="font-size: 11px; font-family: Arial, Helvetica;">Yverdon-les-Bains</text><text text-anchor="middle" transform="translate(326.3626905123626,627.3029308559421)" style="font-size: 11px; font-family: Arial, Helvetica;">Brig – Visp</text><text text-anchor="middle" transform="translate(363.3936729558706,649.7036495807013)" style="font-size: 11px; font-family: Arial, Helvetica;">Martigny</text><text text-anchor="middle" transform="translate(161.86616352035838,442.4326044379246)" style="font-size: 11px; font-family: Arial, Helvetica;">Monthey</text><text text-anchor="middle" transform="translate(469.6049834785495,669.788318013497)" style="font-size: 11px; font-family: Arial, Helvetica;">Sierre</text><text text-anchor="middle" transform="translate(375.5879571187668,54.20733633000117)" style="font-size: 11px; font-family: Arial, Helvetica;">Sion</text><text text-anchor="middle" transform="translate(764.736360454232,422.7429410424764)" style="font-size: 11px; font-family: Arial, Helvetica;">La Chaux-de-Fonds – Le Locle (CH)</text><text text-anchor="middle" transform="translate(477.79108958070583,44.88725168552514)" style="font-size: 11px; font-family: Arial, Helvetica;">Neuchâtel</text><text text-anchor="middle" transform="translate(185.86487027821448,652.1304636301626)" style="font-size: 11px; font-family: Arial, Helvetica;">Genève (CH)</text><text text-anchor="middle" transform="translate(665.0996748797997,149.73585830049257)" style="font-size: 11px; font-family: Arial, Helvetica;">Delémont (CH)</text></g></g></svg>

### Carte de la Suisse

Cette carte provient du site **_map.geo.admin.ch_**. Elle représente la population résidante en Suisse dans les années 2000. Le site contenait déjà des données qui permettaient de représenter la population mais uniquement entre 1990 et 2017. Etant donné que je n'ai pas réussi à entrer mon jeux données sur le site et que mon sujet se focalise sur les années 1980 à 2018, j'ai décidé d'utiliser celui qui était déjà sur le site pour ce map. Les zones en rouges sont les zones qui contiennent plus de 120'000 habitants. On peut voir que la population est plus dense dans les régions du nord de la Suisse comme vu antérieurement pour les années 1980. Comme par exemple dans le canton de Zürich, la population est très dense car c'est une ville assez cosmopolite et elle est le centre économique et financier majeur du pays. La région de Berne, capitale du pays est également très dense à cette même époque. On peut donc constater que de 1980 à 2000 la densité de la population n'a pas tellement changé.

<center><iframe src='https://map.geo.admin.ch/embed.html?topic=ech&lang=fr&bgLayer=ch.swisstopo.pixelkarte-farbe&layers=ch.swisstopo.zeitreihen,ch.bfs.gebaeude_wohnungs_register,ch.bav.haltestellen-oev,ch.swisstopo.swisstlm3d-wanderwege,ch.bfs.volkszaehlung-bevoelkerungsstatistik_einwohner&layers_opacity=1,1,1,0.8,1&layers_visibility=false,false,false,false,true&layers_timestamp=18641231,,,,2000&catalogNodes=688&E=2622720.54&N=1224537.07&zoom=1' width='600' height='400' frameborder='0' style='border:0'></iframe></center>

### Diagramme en barre
Pour ce graphique, j'ai choisi un diagramme en barre afin de montrer la variation de la population résidante en agglomération entre 2000-2018. Pour mieux comprendre le terme de variation, selon le site de l'[Insee](https://www.insee.fr/fr/metadonnees/definition/c1020) _L'accroissement total (ou variation totale) de population est la variation de l'effectif d'une population au cours de l'année, qu'il s'agisse d'une augmentation ou d'une diminution. C'est la somme de l'accroissement naturel, du solde migratoire, et parfois d'un ajustement destiné à rétablir la cohérence entre les différences sources statistiques._ Ainsi sur diagramme, on constate que certaine ville ont obtenu une augmentation de sa population comme la ville de Bulle avec 56,4%
<iframe title="Variation de la population résidante dans les agglomérations entre 2000-2018" aria-label="Histogramme" id="datawrapper-chart-kl7zb" src="https://datawrapper.dwcdn.net/kl7zb/2/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="1289"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"])for(var e in a.data["datawrapper-height"]){var t=document.getElementById("datawrapper-chart-"+e)||document.querySelector("iframe[src*='"+e+"']");t&&(t.style.height=a.data["datawrapper-height"][e]+"px")}}))}();
</script>
