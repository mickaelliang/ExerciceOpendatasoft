# Les fromages français

<p align="center"><img src="https://www.chaumartinvesoul.fr/images/cremerie/cremerie-fromages2.jpg"></p>

<br/>

## Présentation du nombre de fromages différents produits selon leur département
<center>
Voici ci-dessous le nombre de fromages différents produits en fonction de chaque département. Pour l'Ain et l'Aveyron, nous pouvons constater qu'il y a 13 fromages produits dans ces départements. Cependant, nous pouvons voir que dans l'Eure-et-Loir ou encore dans le Bas-Rhin, il y a très peu de fromages produits : seulement 1 fromage pour chacun de ces départements.

<iframe src="https://data.opendatasoft.com/explore/embed/dataset/fromagescsv-fromagescsv@public/analyze/?disjunctive.fromage&dataChart=eyJxdWVyaWVzIjpbeyJjb25maWciOnsiZGF0YXNldCI6ImZyb21hZ2VzY3N2LWZyb21hZ2VzY3N2QHB1YmxpYyIsIm9wdGlvbnMiOnsiZGlzanVuY3RpdmUuZnJvbWFnZSI6dHJ1ZX19LCJjaGFydHMiOlt7ImFsaWduTW9udGgiOnRydWUsInR5cGUiOiJzcGxpbmUiLCJmdW5jIjoiQ09VTlQiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiIjMTQyRTdCIiwicG9zaXRpb24iOiJjZW50ZXIifV0sInhBeGlzIjoiZGVwYXJ0ZW1lbnQiLCJtYXhwb2ludHMiOjUwLCJzb3J0IjoiIiwic2VyaWVzQnJlYWtkb3duVGltZXNjYWxlIjoiIn1dLCJ0aW1lc2NhbGUiOiIiLCJkaXNwbGF5TGVnZW5kIjp0cnVlLCJhbGlnbk1vbnRoIjp0cnVlfQ%3D%3D&location=5,46.66619,2.91208&basemap=jawg.streets&static=false&datasetcard=false" width="600" height="450" frameborder="0"></iframe>
</center>

<br/>

## Présentation du type de lait utilisé en fonction du département
<center>
Voici ci-dessous un graphique représentant 4 types de laits différents utilisés pour produire du fromage : le lait de brebis, le lait de chèvre, le lait de vache ainsi que le lait de vaches (ce dernier étant différencié de l'avant-dernier car il est constitué à partir de plusieurs vaches et non d'une seule). A l'aide de cette visualisation, nous pouvons constater que les fromages français sont majoritairement produits avec du lait de vache. Nous comptons ainsi dans tout le territoire français 243 fromages issus du lait de vache. Le département utilisant le plus le lait de vache est la Savoie, avec 23 fromages produits à partir de ce type de lait.
Le recours au lait de chèvre est également plesbiscité puisqu'il arrive en seconde position en permettant de produire 61 fromages.

<iframe src="https://data.opendatasoft.com/chart/embed/?dataChart=eyJxdWVyaWVzIjpbeyJjb25maWciOnsiZGF0YXNldCI6ImZyb21hZ2VzY3N2LWZyb21hZ2VzY3N2QHB1YmxpYyIsIm9wdGlvbnMiOnsiZGlzanVuY3RpdmUuZnJvbWFnZSI6dHJ1ZSwidGltZXpvbmUiOiJFdXJvcGUvQmVybGluIn19LCJjaGFydHMiOlt7ImFsaWduTW9udGgiOnRydWUsInR5cGUiOiJiYXIiLCJmdW5jIjoiQ09VTlQiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiJyYW5nZS1TZXQzIiwiY3VtdWxhdGl2ZSI6ZmFsc2UsImRpc3BsYXlWYWx1ZXMiOmZhbHNlLCJkaXNwbGF5U3RhY2tWYWx1ZXMiOnRydWV9XSwieEF4aXMiOiJsYWl0IiwibWF4cG9pbnRzIjoyMDAsInNvcnQiOiIiLCJzZXJpZXNCcmVha2Rvd24iOiJkZXBhcnRlbWVudCIsInN0YWNrZWQiOiJub3JtYWwifV0sInRpbWVzY2FsZSI6IiIsImRpc3BsYXlMZWdlbmQiOnRydWUsImFsaWduTW9udGgiOnRydWV9&static=false&datasetcard=true" width="600" height="450" frameborder="0"></iframe>
</center>

<br/>

## Requêtes SPARQL avec Wikidata
  
````sparql

#Peintures de Claude Monet
#defaultView:ImageGrid
SELECT distinct ?peinture
WHERE
{
  ?peinture wdt:P31 wd:Q3305213 .
  ?peinture wdt:P170 wd:Q296 .
}

#Peintures de Claude Monet avec les labels et images associées
#defaultView:ImageGrid
SELECT ?peinture ?peintureLabel ?pic
WHERE
{
  ?peinture wdt:P31 wd:Q3305213 .
  ?peinture wdt:P170 wd:Q296 .
  ?peinture wdt:P18 ?pic .

SERVICE wikibase:label 
{ bd:serviceParam wikibase:language "fr"
}
}

#Peintures de Claude Monet avec les collections et lieux de conservation en option
#defaultView:ImageGrid
SELECT ?peinture ?peintureLabel ?lieux ?lieuxLabel
WHERE
{
  ?peinture wdt:P31 wd:Q3305213 .
  ?peinture wdt:P170 wd:Q296 .

OPTIONAL 
{ 
  #en option 
  ?peinture wdt:P195 ?lieux .
  
SERVICE wikibase:label 
{ 
  bd:serviceParam wikibase:language "fr"
}
}
}

````

