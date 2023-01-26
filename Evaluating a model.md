# Evaluating a model and visualizing the outcome

## Foodboost

Voor foodboost heb ik het multinomial naïve bayes gevisualiseerd en gevalueerd door er een confusion matrix bij te maken. 
En deze te vergelijken met die van andere modellen die groepsgenoten hebben gemaakt. 
We kregen hele goede resultaten voor alles, we dachten dat dit door overfitting kon komen, omdat hij keek naar een paar ingredienten die alleen in een bepaalde keuken voorkwamen.
Hierdoor heb ik het minimum voorkomen van een ingredient van 5 naar 40 verplaatst, zodat elk ingredient in minstens 40 recepten voor moest komen.
Alsnog bleven alle modellen met een precision, recall en accuracy van boven de 95% presteren. Uiteindelijk hebben we hierdoor voor de k-nereast neighbors gekozen. 

De volgende code voor de confusionmatrix is geschreven door Milan, ik heb hem passend gemaakt voor naive bayes

![confusion matrix](https://github.com/Bram-tenCate/Minor-datascience/blob/main/conusion%20matrix.png)

## Containerproject

Voor het foodboost project heb ik mijn model gevalideerd op twee manieren.
De eerste is door alle outputs te printen in python, vervolgens alles mee te tekenen op papier. 
Dit heb ik op het begin veel gebruikt omdat er vaak een kleine redenatiefout ergens in een restrictie of in de beginstap zat. 
Zo heb ik een aantal fouten eruit gekregen die doormiddel van plotten in python niet te vinden waren. 
Bijvoorbeeld fouten met indices, of modellen die meerdere containers op één plek gooien, heb ik er zo weten uit te halen. 

De tweede manier is om een visualisatie te maken van de output, hier ga ik zo verder op in. 

**model 1**

Het uiteindelijke model 1 werkt op grote velden, toch zijn er nog een paar kleie nadelen. 
De eerste is dat het met op een groot veld met veel containers (meer dan enkele honderden) een paar keer een uur of 8 heeft geduurd voordat er een oplossing uit komt.
Het zit hem in de stap "cutting planes", hoewel het model al via de "root relaxation" methode aangegeven had een feasible oplossing gevonden te hebben (binnen ongeveer 40 seconden).
Bleef het model doorgaan op andere nodes om te kijken naar een betere oplossing. In dit geval zou het beter zijn om alleen de feasible oplossing terug te geven, 
8 uur rekentijd vind ikt te lang voor het toepassen van dit model. Helaas is het mij niet gelukt om deze stap eruit te halen.

Hieronder heb ik een voorbeeld gegeven van een model, hoe deze output eruit ziet. 

![optimize output](https://github.com/Bram-tenCate/Minor-datascience/blob/main/optimizer%20output.png)

Als ik vervolgens het wegschrijven van de resultaten run. Heb ik een ander stuk code wat door milan geschreven is om de resultaten te weergeven. 
Hij heeft dit zo geschreven dat dit altijd voor een vaste disctionary containers op een 4*3*3 veld werkt.
Ik heb het omgezet dat de grootte van het veld kan variëren, en dat de oplossing mijn huiduge oplossing is inplaats van een vaste dictionary.
Helaas blijft dit stuk code hangen in de laatste regel code bij het runnen, waardoor je daarna je kernel af moet sluiten, maar je kan de resultaten zien. 

![vizualisatie code](https://github.com/Bram-tenCate/Minor-datascience/blob/main/vizualisatie%20code.png)

Na runnen levert het de volgende resultaten.
van 20 runs komt er een in 11 runs op een 8*4*4 veld een geldige oplossing uit. 
In de andere 9 gevallen had hij op zijn minst 1, en maximaal 4 containers op een rare plek geplaatst. 
Ik heb alle restricties doorlopen en met de hand uitgeschreven. Uit logisch redenderen volgt dat uit het model restrictie 4 en/of 7 overtreden, 
zoals hieronder in de 2e afbeelding container 98 overtreed dat hij op containers staan die eerder wegmoeten (7), en ook nog eens ervoor staat (4). 
Ik heb deze restricties volledig met de hand uitgewerkt op de momenten in de loop dat de restricties het plaatsen tegen moeten gaan. 
De restricties zouden op dat moment ook inderdaad een false moeten teruggeven waardoor deze oplossing als ongeldig gezien zou moeten worden. 
Het model geeft het alsnog terug als feasible oplossing. Mijn theorie is dat het iets met een relexatie te maken zou moeten hebben. 
Dit zou alsnog raar zijn omdat er wel gewoon feasible oplossingen bestaan, en de solver dus helemaal niet zou moeten denken aan relexaties. 

![geldige uitkomst](https://github.com/Bram-tenCate/Minor-datascience/blob/main/seed%2013.png)

![ongeldige uitkomst](https://github.com/Bram-tenCate/Minor-datascience/blob/main/9%20bij%204%20bij%204.png)

**model 2**
Ik heb hetzelfde ook gedaan voor model 2. 
Uiteindelijk kan dit model niet op minder restricties draaien dan model 1. 
De library ziet de minimalisatie functie in de resrtictie namelijk als meerdere restricties. 
Anders gezegd betekent dit dat als je vraagt naar E[i] <= min(C[j], over i= 1 t/m 5), dat hij 5 restricties reserveert in het geheugen. 
Namelijk E[i]<=C[1], E[i] <= C[2], enzovoorts.

Daarnaast zoals ik in het kopje "trainen van het model" al aangaf zou restrictie 1 (elke container moet op 1 plek komen, en elke plek mag 1 container hebben)
moeten dekken dat er op elke plek maximaal 1 container staat. Karin de Smidt was het hiermee eens. Alsnog gaf het model zonder resstrictie 4 deze output:

zonder restrictie 4

![foutieve uitkomst](https://github.com/Bram-tenCate/Minor-datascience/blob/main/model%202%20foutief.png)

met restrictie 4

![goede uitkomst](https://github.com/Bram-tenCate/Minor-datascience/blob/main/model%202%20goed.png)

Nu kom ik er zojuist achter dat er toch nog iets fout gaat in dit model. 
Container 15 zou in de tweede foto namelijk door de doelfunctie op het vlak linksonder geplaatst moeten worden. 
Na het opnieuw doornemen van de restricties zit er mogelijk een fout in de zesde restricite,
die zou moeten voorkomen dat er containers containers op een lager y-coordinaat containers blokkeren. 
Hij zou het bovenstaande wel moeten toestaan. 
Zodra er op de y-as een gat valt, werkt de restrictie alleen niet meer om het maximale schipsnummer goed te kunnnen bepalen. 
Waardoor er alsnog een container de achterstaande containers zou kunnen blokkeren. 
Dit zou niet dan een uurtje moeten kosten om om te zetten zodat het wel werkt. 
Voor mijn eigen gezondheid doe ik het alleen nu niet.

**conclusie vergelijking modellen**

Toen ik bijna een volledige studiedag gestopt had in het proberen te begrijpen van hoe ik model 2 in guirobi kon krijgen, heb ik maar besloten dat het beter zou zijn om aan model 1 door te werken.
Ik ben ervan overtuigd dat er nog een manier gevonden kan worden om model 2 zo te krijgen dat het met minder restricties dan model 1 goed zou werken. 
Voor mij was het het niet waard om een duurdere solver-package te kopen, dus heb ik model 2 maar gelaten voor wat het is. 

Behalve het volledig opstapelen zouden ze op een lege kade hetzelfde moeten werken. Of het volledig opstapelen een voordeel of een nadeel is, 
is wat mij betreft nog onbepaald. 
Model 2 werkt op een volle kade iets makkelijker omdat er alleen de waardes voor de variabele E ingevoerd moeten worden. 
Model 1 vereist op een deels gevdulde kade alle informatie van de eerdere containers (de tijdsvolgorde waarop ze zijn gekomen en het schipsnummer).

De stappen die ik met meer tijd nog graag aan de modellen zou willen maken zijn: 
  1. het ten eerste werkend krijgen van één van de modellen, op een kade van realisttische grootte. 
  2. een optimalisatieslag maken in de beginstap. Ik kan mij namelijk goed voorstellen dat het helemaal niet optimaal is om voor de rijtjes altijd maar de containers te pakken die als eerste binnenkomen. Het lijkt mij een leuke uitdaging om te kijken welke containers je hier het beste voor kan gebruiken.
 
