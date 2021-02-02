
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

Cette carte provient du site **_map.geo.admin.ch_**. Elle représente la population résidante en Suisse dans les années 2000. Le site contenait déjà des données qui permettaient de représenter la population mais uniquement entre 1990 et 2017. Etant donné que je n'ai pas réussi à entrer mon jeux données sur le site et que mon sujet se focalise sur les années 1980 à 2018, j'ai décidé d'utiliser celui qui était déjà sur le site pour ce map. Les zones en rouges sont les zones qui contiennent plus de 120'000 habitants. On peut voir que la population est plus dense dans les régions du nord de la Suisse. Comme par exemple dans le canton de Zürich, la population est très dense car c'est une ville assez cosmopolite et elle est le centre économique et financier majeur du pays. La région de Berne, capitale du pays est également très dense à cette même époque.

<center><iframe src='https://map.geo.admin.ch/embed.html?topic=ech&lang=fr&bgLayer=ch.swisstopo.pixelkarte-farbe&layers=ch.swisstopo.zeitreihen,ch.bfs.gebaeude_wohnungs_register,ch.bav.haltestellen-oev,ch.swisstopo.swisstlm3d-wanderwege,ch.bfs.volkszaehlung-bevoelkerungsstatistik_einwohner&layers_opacity=1,1,1,0.8,1&layers_visibility=false,false,false,false,true&layers_timestamp=18641231,,,,2000&catalogNodes=688&E=2622720.54&N=1224537.07&zoom=1' width='600' height='400' frameborder='0' style='border:0'></iframe></center>

### Diagramme
<center>
<svg width="848" height="848" xmlns="http://www.w3.org/2000/svg"><g transform="translate(10,10)"><g><circle class="node node--root" transform="translate(414,414)" r="414.00000000000006" style="fill-opacity: 0; stroke: rgb(221, 221, 221); stroke-opacity: 1;"></circle><circle class="node node--leaf" transform="translate(244.97949055946438,436.46495918115136)" r="42.43388675067966" style="fill: rgb(191, 105, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(422.9822414474253,436.46495918115136)" r="131.1964707007054" style="fill: rgb(191, 116, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(248.89007460957077,562.6625014137994)" r="79.45183770293784" style="fill: rgb(191, 126, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(268.3858132769018,352.50476751673114)" r="40.35546444580588" style="fill: rgb(191, 137, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(350.07770854903265,571.3222017824315)" r="17.733278049817198" style="fill: rgb(191, 147, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(325.0756747140172,298.79721865409783)" r="33.36337846710559" style="fill: rgb(191, 158, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(404.33043570421927,626.1358981174885)" r="55.01695625467242" style="fill: rgb(191, 168, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(383.0919358424627,283.8474464829605)" r="22.175681452858722" style="fill: rgb(191, 179, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(214.42745918411805,381.16680293813994)" r="16.370556588865615" style="fill: rgb(191, 189, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(430.57818787482535,279.9853810329864)" r="21.09496953072132" style="fill: rgb(182, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(494.25788981748406,593.0153021385194)" r="36.443425919684806" style="fill: rgb(172, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(271.730031729158,291.8024618646449)" r="16.06649801136641" style="fill: rgb(161, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(171.8799081948412,472.5476767992789)" r="34.713726268778736" style="fill: rgb(151, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(324.7654583120675,634.4151043309262)" r="20.60521814268811" style="fill: rgb(140, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(493.10414082204596,278.7066914687104)" r="37.07166355982298" style="fill: rgb(130, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(351.6254131557813,232.57847572457516)" r="33.60713612852799" style="fill: rgb(119, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(617.5752355429063,321.823155310066)" r="90.28324797562395" style="fill: rgb(109, 191, 105); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(550.2076544772062,545.9632104207984)" r="32.28873248896386" style="fill: rgb(105, 191, 112); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(434.9324760362151,204.81053332266563)" r="49.83348399780904" style="fill: rgb(105, 191, 123); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(175.5827598704555,407.42343235832584)" r="26.14330865743736" style="fill: rgb(105, 191, 133); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(206.36488927845696,343.3003295397954)" r="17.972354972856078" style="fill: rgb(105, 191, 144); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(227.47919483868182,297.1151105576973)" r="24.129716356692096" style="fill: rgb(105, 191, 154); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(284.7403788621782,243.316761316885)" r="29.762027768031576" style="fill: rgb(105, 191, 165); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(578.848361372346,487.50072484883333)" r="28.439967081456174" style="fill: rgb(105, 191, 175); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(629.5005788500149,447.589286956698)" r="31.674614988831753" style="fill: rgb(105, 191, 185); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(527.820199767063,206.47548714884653)" r="38.69676672142818" style="fill: rgb(105, 185, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(184.7519806333257,311.08323054210996)" r="16.45034519696961" style="fill: rgb(105, 175, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(170.98560850023154,360.2472348190216)" r="16.88395418098744" style="fill: rgb(105, 165, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(470.75166772978736,635.4327478048352)" r="7.6793574522734005" style="fill: rgb(105, 154, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(222.85254432504095,241.00693006947904)" r="27.796503090832957" style="fill: rgb(105, 144, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(154.26697042721509,526.3511602099485)" r="17.526868238477412" style="fill: rgb(105, 133, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(288.0351157849544,656.5742161208249)" r="17.91929154294614" style="fill: rgb(105, 123, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(551.7429951972388,599.6537080493117)" r="17.051319622247252" style="fill: rgb(105, 112, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(340.70894227960775,682.2445437226331)" r="25.439151045365037" style="fill: rgb(109, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(613.6934761870368,536.721243194126)" r="27.4938701105546" style="fill: rgb(119, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(105.31409886990974,425.9675063326531)" r="42.15869090912743" style="fill: rgb(130, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(306.2975179042627,186.39957864569266)" r="26.72834185217173" style="fill: rgb(140, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(92.56477974217705,308.73322324951806)" r="71.39441021860803" style="fill: rgb(151, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(602.8306788804783,195.24620458268308)" r="32.77718954832568" style="fill: rgb(161, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(497.7613175874603,655.0804993211656)" r="21.34817912726831" style="fill: rgb(172, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(460.31915021017375,689.111987592112)" r="24.87644406603546" style="fill: rgb(182, 105, 191); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(369.469901254468,182.86867397535275)" r="14.836094500613402" style="fill: rgb(191, 105, 189); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(185.03555964996923,272.93667547694037)" r="17.32487047107203" style="fill: rgb(191, 105, 179); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(295.0974847013014,696.0968925894615)" r="17.857026207203536" style="fill: rgb(191, 105, 168); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(553.4327766695505,651.1398770078201)" r="30.090177839149693" style="fill: rgb(191, 105, 158); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(239.58511698460634,676.0208055756914)" r="29.915328200508295" style="fill: rgb(191, 105, 147); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(608.727144107496,604.1417387542581)" r="35.73689966213107" style="fill: rgb(191, 105, 137); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(725.5035562745904,516.0142574576516)" r="81.84509590070898" style="fill: rgb(191, 105, 126); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle><circle class="node node--leaf" transform="translate(144.49651097256407,567.8109268095282)" r="20.69620902837476" style="fill: rgb(191, 105, 116); fill-opacity: 1; stroke: rgb(221, 221, 221); stroke-opacity: 0;"></circle></g><g><text text-anchor="middle" transform="translate(414,414)" style="font-size: 11px; font-family: Arial, Helvetica;">Rest der Schweiz / Reste de la Suisse</text><text text-anchor="middle" transform="translate(244.97949055946438,436.46495918115136)" style="font-size: 11px; font-family: Arial, Helvetica;">Winterthur</text><text text-anchor="middle" transform="translate(422.9822414474253,436.46495918115136)" style="font-size: 11px; font-family: Arial, Helvetica;">Zürich</text><text text-anchor="middle" transform="translate(248.89007460957077,562.6625014137994)" style="font-size: 11px; font-family: Arial, Helvetica;">Bern</text><text text-anchor="middle" transform="translate(268.3858132769018,352.50476751673114)" style="font-size: 11px; font-family: Arial, Helvetica;">Biel/Bienne</text><text text-anchor="middle" transform="translate(350.07770854903265,571.3222017824315)" style="font-size: 11px; font-family: Arial, Helvetica;">Interlaken</text><text text-anchor="middle" transform="translate(325.0756747140172,298.79721865409783)" style="font-size: 11px; font-family: Arial, Helvetica;">Thun</text><text text-anchor="middle" transform="translate(404.33043570421927,626.1358981174885)" style="font-size: 11px; font-family: Arial, Helvetica;">Luzern</text><text text-anchor="middle" transform="translate(383.0919358424627,283.8474464829605)" style="font-size: 11px; font-family: Arial, Helvetica;">Altdorf (UR)</text><text text-anchor="middle" transform="translate(214.42745918411805,381.16680293813994)" style="font-size: 11px; font-family: Arial, Helvetica;">Lachen</text><text text-anchor="middle" transform="translate(430.57818787482535,279.9853810329864)" style="font-size: 11px; font-family: Arial, Helvetica;">Glarus</text><text text-anchor="middle" transform="translate(494.25788981748406,593.0153021385194)" style="font-size: 11px; font-family: Arial, Helvetica;">Zug</text><text text-anchor="middle" transform="translate(271.730031729158,291.8024618646449)" style="font-size: 11px; font-family: Arial, Helvetica;">Bulle</text><text text-anchor="middle" transform="translate(171.8799081948412,472.5476767992789)" style="font-size: 11px; font-family: Arial, Helvetica;">Fribourg</text><text text-anchor="middle" transform="translate(324.7654583120675,634.4151043309262)" style="font-size: 11px; font-family: Arial, Helvetica;">Grenchen</text><text text-anchor="middle" transform="translate(493.10414082204596,278.7066914687104)" style="font-size: 11px; font-family: Arial, Helvetica;">Olten – Zofingen</text><text text-anchor="middle" transform="translate(351.6254131557813,232.57847572457516)" style="font-size: 11px; font-family: Arial, Helvetica;">Solothurn</text><text text-anchor="middle" transform="translate(617.5752355429063,321.823155310066)" style="font-size: 11px; font-family: Arial, Helvetica;">Basel (CH)</text><text text-anchor="middle" transform="translate(550.2076544772062,545.9632104207984)" style="font-size: 11px; font-family: Arial, Helvetica;">Schaffhausen (CH)</text><text text-anchor="middle" transform="translate(434.9324760362151,204.81053332266563)" style="font-size: 11px; font-family: Arial, Helvetica;">St. Gallen</text><text text-anchor="middle" transform="translate(175.5827598704555,407.42343235832584)" style="font-size: 11px; font-family: Arial, Helvetica;">Rheintal (CH)</text><text text-anchor="middle" transform="translate(206.36488927845696,343.3003295397954)" style="font-size: 11px; font-family: Arial, Helvetica;">Buchs (SG) (CH)</text><text text-anchor="middle" transform="translate(227.47919483868182,297.1151105576973)" style="font-size: 11px; font-family: Arial, Helvetica;">Rapperswil-Jona – Rüti</text><text text-anchor="middle" transform="translate(284.7403788621782,243.316761316885)" style="font-size: 11px; font-family: Arial, Helvetica;">Wil (SG)</text><text text-anchor="middle" transform="translate(578.848361372346,487.50072484883333)" style="font-size: 11px; font-family: Arial, Helvetica;">Chur</text><text text-anchor="middle" transform="translate(629.5005788500149,447.589286956698)" style="font-size: 11px; font-family: Arial, Helvetica;">Aarau</text><text text-anchor="middle" transform="translate(527.820199767063,206.47548714884653)" style="font-size: 11px; font-family: Arial, Helvetica;">Baden – Brugg</text><text text-anchor="middle" transform="translate(184.7519806333257,311.08323054210996)" style="font-size: 11px; font-family: Arial, Helvetica;">Wohlen (AG)</text><text text-anchor="middle" transform="translate(170.98560850023154,360.2472348190216)" style="font-size: 11px; font-family: Arial, Helvetica;">Lenzburg</text><text text-anchor="middle" transform="translate(470.75166772978736,635.4327478048352)" style="font-size: 11px; font-family: Arial, Helvetica;">Stein (AG) (CH)</text><text text-anchor="middle" transform="translate(222.85254432504095,241.00693006947904)" style="font-size: 11px; font-family: Arial, Helvetica;">Arbon – Rorschach</text><text text-anchor="middle" transform="translate(154.26697042721509,526.3511602099485)" style="font-size: 11px; font-family: Arial, Helvetica;">Amriswil – Romanshorn</text><text text-anchor="middle" transform="translate(288.0351157849544,656.5742161208249)" style="font-size: 11px; font-family: Arial, Helvetica;">Frauenfeld</text><text text-anchor="middle" transform="translate(551.7429951972388,599.6537080493117)" style="font-size: 11px; font-family: Arial, Helvetica;">Kreuzlingen (CH)</text><text text-anchor="middle" transform="translate(340.70894227960775,682.2445437226331)" style="font-size: 11px; font-family: Arial, Helvetica;">Bellinzona</text><text text-anchor="middle" transform="translate(613.6934761870368,536.721243194126)" style="font-size: 11px; font-family: Arial, Helvetica;">Locarno (CH)</text><text text-anchor="middle" transform="translate(105.31409886990974,425.9675063326531)" style="font-size: 11px; font-family: Arial, Helvetica;">Lugano (CH)</text><text text-anchor="middle" transform="translate(306.2975179042627,186.39957864569266)" style="font-size: 11px; font-family: Arial, Helvetica;">Chiasso – Mendrisio (CH)</text><text text-anchor="middle" transform="translate(92.56477974217705,308.73322324951806)" style="font-size: 11px; font-family: Arial, Helvetica;">Lausanne</text><text text-anchor="middle" transform="translate(602.8306788804783,195.24620458268308)" style="font-size: 11px; font-family: Arial, Helvetica;">Vevey – Montreux</text><text text-anchor="middle" transform="translate(497.7613175874603,655.0804993211656)" style="font-size: 11px; font-family: Arial, Helvetica;">Yverdon-les-Bains</text><text text-anchor="middle" transform="translate(460.31915021017375,689.111987592112)" style="font-size: 11px; font-family: Arial, Helvetica;">Brig – Visp</text><text text-anchor="middle" transform="translate(369.469901254468,182.86867397535275)" style="font-size: 11px; font-family: Arial, Helvetica;">Martigny</text><text text-anchor="middle" transform="translate(185.03555964996923,272.93667547694037)" style="font-size: 11px; font-family: Arial, Helvetica;">Monthey</text><text text-anchor="middle" transform="translate(295.0974847013014,696.0968925894615)" style="font-size: 11px; font-family: Arial, Helvetica;">Sierre</text><text text-anchor="middle" transform="translate(553.4327766695505,651.1398770078201)" style="font-size: 11px; font-family: Arial, Helvetica;">Sion</text><text text-anchor="middle" transform="translate(239.58511698460634,676.0208055756914)" style="font-size: 11px; font-family: Arial, Helvetica;">La Chaux-de-Fonds – Le Locle (CH)</text><text text-anchor="middle" transform="translate(608.727144107496,604.1417387542581)" style="font-size: 11px; font-family: Arial, Helvetica;">Neuchâtel</text><text text-anchor="middle" transform="translate(725.5035562745904,516.0142574576516)" style="font-size: 11px; font-family: Arial, Helvetica;">Genève (CH)</text><text text-anchor="middle" transform="translate(144.49651097256407,567.8109268095282)" style="font-size: 11px; font-family: Arial, Helvetica;">Delémont (CH)</text></g></g></svg>
</center>
