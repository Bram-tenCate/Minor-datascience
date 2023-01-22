## Foodboost

Om het model te kunnen trainen moest ik eerst de data op orde krijgen.
Dit heb ik gedaan door eerst even in de data te kijken.
Daar kwam het volgende uit 
![training a model](https://github.com/Bram-tenCate/Minor-datascience/blob/main/training%20a%20model.png)

Als je de keukens gaat voorspellen die iemand lekker vind, is het niet handig als de keukens nog tussen de data staan. Dus die heb ik eruit gehaald. 
Daarnaast haal ik de colom "liked recipes" eruit omdat die alleen nodig is bij het aanbevelen van een recept die iemand nog niet heeft gezien.
En haal ik de laatste twee rijen eruit omdat daar data stond die milan alleen even had gesimuleerd om de app te testen.
![selecting a model](https://github.com/Bram-tenCate/Minor-datascience/blob/main/selecting%20data.png)

De data is klaar om op getraind te worden. De kolom ['kitchen'] bestaat uit textuële waarden die voorspeld moeten worden.
Vandaar dat dat in de y-waarde is geladen.
Vervolgens heb ik de data gesplitst in train en test data, aangezien er na het testen er niks meer met het model zou gebeuren. 
Was het niet nodig om de test data ook nog op te splitsen in test en validatie data. 
Ik heb voor de train-test split 80% voor het trainen en 20% voor het testen gebruikt, dit gebruikten we standaard.
Als laatste voor het trainen heb ik gekeken of de uitkomsten ook overeenkomen met wat ik verwachtte dat voorspeld zou worden.
![training](https://github.com/Bram-tenCate/Minor-datascience/blob/main/training%20of%20the%20model4.png)

## Container

Voor het containerproject heb ik natuurlijk geen model echt getraind, ik heb de modellen omgezet in python en dit zag er als volgt uit. 
Ik heb hiermee veel ervaring opgedaan in verschillende LP libraries voor python. Waaronder docplex, guirobipy, en ortools.
Model 1 heb ik uiteindelijk in guirobipy gezet. Het voordeel hiervan was dat er een gratis academische versie voor studenten van de HHS beschikbaar was. 
Model 2 heb ik alleen werkend gekregen in docplex. Een minimalisatie binnen een restrictie is in het klassiek lineair programmeren niet normaal. 
Het zou mogelijk moeten zijn in elke library die ik tegen ben gekomen. De foutmelding die ik hier echter over kreeg in guirobi kon ik niet omzeilen. 
Er staat vrij weinig documentatie online, dus model 2 heb ik helaas alleen in docplex werkend kunnen krijgen.   

Ik zal hieronder laten zien hoe ik model 1 in python heb gezet. Model 2 is op een hele gelijke manier erin gezet, soms is de syntax net wat anders, en de beginstap is een beetje anders doordat LD niet meer binair is. Verder is het niet  zo verschillend dat het voor jullie echt interresant is.

**model 1**

importeren van packages. 

![de packages van guirobipy](https://github.com/Bram-tenCate/Minor-datascience/blob/main/packages%20guirobipy.png)

definiëren sets
![definiëren sets](https://github.com/Bram-tenCate/Minor-datascience/blob/main/setdeclaratie.png)

definiëren parameters
![dinieren parameters](https://github.com/Bram-tenCate/Minor-datascience/blob/main/parameter%20declaratie.png)

Dan is het tijd om de beginstap uit te voeren. Ik heb dit misschien netter kunnen doen met minder nested for loops, maar het werkt iniedergeval.
De rede dat ik op het laatst alle dictionairies opnieuw definieer heeft te maken met de restrictie declaratie. 
Er zitten namelijk in een paar restricties een i+1. Als in de beginstap container 8 er bijvoorbeeld uitgehaald wordt en ingedeeld wordt. Dan zou hij bij container 7 een foutmelding geven dat er helemaal geen volgende container in de tijdsreeks bestaat.  

![beginstap](https://github.com/Bram-tenCate/Minor-datascience/blob/main/beginstap%20guirobipy.png)

variabele en restricties delcareren

![variabele + constraint declaratie](https://github.com/Bram-tenCate/Minor-datascience/blob/main/variarble%20and%20constraint%20decl%20guirobipy.png)

doelfunctie declareren en optimazation uitvoeren
![doelfunctie](https://github.com/Bram-tenCate/Minor-datascience/blob/main/optimize%20function.png)

resultaten wegschrijven in een dictionary
![wegschrijven](https://github.com/Bram-tenCate/Minor-datascience/blob/main/oplossing%20wegschrijven%20guirobi.png)
