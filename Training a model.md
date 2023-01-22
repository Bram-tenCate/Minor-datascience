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
