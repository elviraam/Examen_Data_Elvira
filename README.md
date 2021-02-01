
## Population résidante dans les agglomérations, de 1980 à 2018

   ![alt tag](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Flag_of_Switzerland_%28Pantone%29.svg/200px-Flag_of_Switzerland_%28Pantone%29.svg.png)



### Thématique
J'ai décidé dans le cadre de mon cours de datavisualisation d'aborder un sujet qui touche mon pays la Suisse. En effet, la Suisse, appelée également _Confédération Suisse_ est un petit pays d'Europe centrale formé de 26 cantons et dont la capitale est Berne. J'ai donc choisi un sujet sur **la population suisse résidante dans les agglomérations de 1980 à 2018**. Pour mieux définir le sujet, selon wikipédia, _En Suisse comme ailleurs, la notion de ville évolue au cours du temps. Au xxe siècle, la ville, selon sa définition statistique, est une agglomération supérieure à 10 000 habitants, mais d’un point de vue historique, la notion est bien plus complexe et nullement liée à l'importance de la population._



### Jeu de données: Introduction

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
### Carte de la Suisse

Cette carte provient du site map.geo.admin.ch. Elle représente la population résidante en Suisse dans les années 2000. Le site contenait déjà des données qui permettaient de représenter la population mais uniquement entre 1990 et 2017. Etant donné que je n'ai pas réussi à entrer mon jeux données sur le site et que mon sujet se focalise sur les années 1980 à 2018, j'ai décidé d'utiliser celui qui était déjà sur le site pour ce map. Les zones en rouges sont les zones qui contiennent plus de 120'000 habitants. On peut voir que la population est plus dense dans les régions du nord de la Suisse. Comme par exemple dans le canton de Zürich, la population est très dense car c'est une ville assez cosmopolite et elle est le centre économique et financier majeur du pays. La région de Berne, capitale du pays est également très dense à cette même époque.

<center><iframe src='https://map.geo.admin.ch/embed.html?topic=ech&lang=fr&bgLayer=ch.swisstopo.pixelkarte-farbe&layers=ch.swisstopo.zeitreihen,ch.bfs.gebaeude_wohnungs_register,ch.bav.haltestellen-oev,ch.swisstopo.swisstlm3d-wanderwege,ch.bfs.volkszaehlung-bevoelkerungsstatistik_einwohner&layers_opacity=1,1,1,0.8,1&layers_visibility=false,false,false,false,true&layers_timestamp=18641231,,,,2000&catalogNodes=688&E=2622720.54&N=1224537.07&zoom=1' width='600' height='400' frameborder='0' style='border:0'></iframe></center>

### Population résidante dans les agglomérations en 1980
<center>
<iframe title="Population résidante dans les agglomérations en 1980" aria-label="Histogramme" id="datawrapper-chart-kl7zb" src="https://datawrapper.dwcdn.net/kl7zb/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="1264"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"])for(var e in a.data["datawrapper-height"]){var t=document.getElementById("datawrapper-chart-"+e)||document.querySelector("iframe[src*='"+e+"']");t&&(t.style.height=a.data["datawrapper-height"][e]+"px")}}))}();
</script>
</center>
