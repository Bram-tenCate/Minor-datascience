# Configuring a model

## Foodboost

Voor het foodboost project hebben we dus met machine learning gewerkt. Ik heb meerdere modellen bekeken waaronder multinominal naïve bayes en dicision forrest.
Ik ben op een dcision forrest gekozen omdat we Ilias al gewerkt had met een dicision tree, vervolgens had Tony in week drie gevraagd waarom je dit boven een dicision forrest zou kiezen. 
Hier hadden we niet echt een antwoord op. Het bestaat uit meerdere dicision tree's, dus zou uiteindelijk beter moeten werken. 
Op naïve bayes ben ik gekomen door op google te zoeken naar andere modellen die als y-variabelen een discrete variabele voorspellen. 




## Containerproject

Ik heb twee lineair programmeer modellen in elkaar gezet tijdens het container project. 
Om het opstellen van de constraints een beetje makkelijker te maken heb ik ervoor gekozen om containers maar vanaf 1 kant te gaan plaatsen. 
Dit levert in de reële situatie een beetje tijdswinst op, aangezien de truck die containers rondrijd nooit naar de achterkant hoeft te rijden. 

**model 1**

Het eerste model zit als volgt in elkaar.

![model 1](https://github.com/Bram-tenCate/Minor-datascience/blob/main/model1.png)

definities constraints:

  1.	Geen zwevende containers (er moet dus een container onder de geplaatste container staan.
  2.	Container moet op een lege positie komen
  3.	Containers worden pas geplaatst op een y locatie als de y locatie erachter tot de max gevuld is. (dus stel container i wordt geplaatst op (x,y) locatie   (1,2), mag dat pas als (1,1) tot de max hoogte gevuld is)
  4.	Containers mogen alleen op plekken gezet worden als de containers erachter voor schepen bestemd zijn die op een later schip weggaan
  5.	Alle containers moeten op een plek geplaatst worden.
  6.	Als een container op plek x,y,z geplaatst wordt is deze daarna niet meer leeg
  7.	De containers die onder de container staan moeten voor latere schepen bestemd zijn. (als er op een bepaalde (x,y,z) locatie een container voor schip 4 staat. Mag één z hoger de container maximaal voor schip 1,2,3, én 4 bestemd zijn 

Ik heb er bij dit model dus voor gekozen om containers altijd tot de maximale hoogte te stapelen. 
Een voordeel hiervan is dat er meer plekken overzijn bij het aankomen van nieuwe schepen waar er containers gestapeld kunnen worden. 
Het nadeel hiervan is dat het voordeliger kan zijn voor de doelfunctie om dit niet te doen.

**model 2**

Het tweede model zit als volgt in elkaar. 

![model 2](https://github.com/Bram-tenCate/Minor-datascience/blob/main/model2.png)

definities constraints:

  1. overgenomen uit model 1, alle containers moeten geplaatst worden
  2. Het schipsnummer van een container dat op een plek geplaatst wordt, moet lager zijn dan het aangegeven maximum containernummer voor die plek. ook om C aan E te koppelen. 
  4. Het maximale containernummer voor een plek moet gelijk of lager zijn aan dat van de container eronder
  5. Het maximale containernummer voor een plek wordt naar 0 afgedwongen op het moment dat er een container geplaatst wordt, voorkomt dubbele containers. 
  6. Het maximale containernummer voor een plek wordt afgedwongen naar maximaal het hoogste schipnummer van de containers in de rij erachter. 
  7. Het maximale containernummer voor een plek wordt naar 0 afgedwongen, zodra er een container voor wordt gezet. Deze plek is dan niet meer te bereiken met de truk. 

Er zitten hier nog een paar rare dingen in. Ten eerste zou restrictie 1 moeten afdwingen dat er eop elke plek precies 1 container staat. 
Tijdens het testen van het model plaatste het model alsnog meerdere containers op 1 plek, waardoor restrictie 4 bedacht is.
Ik kom er tijdens het schrijven van dit portofolio achter dat er nog een paar andere kinken inzitten, ik heb geen tijd meer om dit recht te trekken. 
Ik zal hier verder de diepte over ingaan bij het kopje "Evaluating a model". 

**beginstap 

Om bij beide modellen iets minder variabelen en restricties te krijgen heb ik besloten om een beginstap uit te voeren. 
Tijdens een presentatie merkte Jeroen Vuurens namelijk op dat als er genoeg containers zijn om een compleet rijtje te vullen, dat je dat vooraf zou kunnen oden.
Dit heb ik erin verwerkt. In de beginstap pakt hij altijd de eerste n benodigde containers om een rijtje mee te kunnen vullen. Deze vult hij van rechts naar links op de kade. 
Over de uitvoering hiervan kan nog beter na worden gedacht. Hierover meer in het kopje "evaluation".

**verschillen modellen**

Ik ben begonnnen met model 2 te maken omdat ik dacht dat model 1 compacter kon. En dat het mogelijk zou moeten zijn om het aangeven van een niet lege startpositie op de kade makkelijker moest kunnen. De gedachtengang was dat als ik van LD in plaats van een binaire parameter, een integer parameter maak,
dan kan van de binaire variabele E ook een integer variabele gemaakt worden. Wat scheelt op het aantal Variabele, en daarmee ook op het aantal restricties.
(zelfde aantal restricties die over minder variabelen geloopt worden staat gelijk aan minder variabelen). Daarvoor heb ik wel de definitie van E moeten 
veranderenen. Waar die in model 1 aangaf of een plek nog leeg was, is dat in model 2 het maximale schipsnummer voor een bepaalde plek geworden. 

Verder heb ik bij model 2 geen restricties ingebouwd dat een rij tot de maximale hoogte gevuld moet worden, of dat er geen "gaten" in de kade mogen komen. De gedachten erachter was dat als het optimaler is om dit niet te doen; waarom zou je het dan forceren? Een nadeel hiervan wel is wel dat als er een extra schip binnenkomt, en deze oplossing als startoplossing zou mee worden gegeven. De kans op geen oplossing voor dat schip een heel stuk groter is. 
