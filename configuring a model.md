# Configuring a model

## Foodboost

Voor het foodbost project hebben we dus met machine learning gewerkt. Ik heb meerdere modellen bekeken waaronder multinominal naïve bayes en dicision forrest.
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
  2. Het schipsnummer van een container dat op een plek geplaatst wordt, moet lager zijn dan het aangegeven maximum containernummer voor die plek
  3. Het maximale containernummer voor een plek moet gelijk of lager zijn aan dat van de container eronder
  4. Het maximale containernummer voor een plek wordt naar 0 afgedwongen op het moment dat er een container geplaatst wordt, voorkomt dubbele containers. 
  5. Het maximale containernummer voor een plek wordt afgedwongen naar maximaal het hoogste schipnummer van de containers in de rij erachter. 
  6. Het maximale containernummer voor een plek wordt naar 0 afgedwongen, zodra er een container voor wordt gezet. Deze plek is dan niet meer te bereiken met de truk. 


