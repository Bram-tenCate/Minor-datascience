# Literature research

## Foodboost

Voor foodboost hebben we wat literatuur onderzoek gedaan.

Ik had zelf het volgende onderzoek gevonden die ook een machine learning algoritme gebruiken om maaltijden aan te raden:

[Machine Learning Based Food Recipe Recommendation System](https://link.springer.com/chapter/10.1007/978-981-10-5146-3_2 )

Deze link gaat over een onderzoek waar ze item-based vergelijken met user-based. item-based rekent sneller, user based levert voor hen betere resultaten.
Wij zijn door gebrek aan user-data met item-based aan de slag gegaan.


Ook hebben we een soortgelijke app gevonden waar wij inspiratie voor onze eigen app uit hebben gehaalt. 
Deze app heet 
[yummly](https://www.yummly.com/)
Ik heb hier zelf geen delen van overgenomen, wel hadden we in gedachten om voor future work het gedeelte van de allergiëen eruit over te nemen. 

## Containerproject

Voor het containerproject heb ik ook iets van literatuur onderzoek gedaan. Toen ik besloot om het lineair programmeren op mij te nemen,
ben ik opzoek gegaan naar soortgelijke onderzoeken.

Ik ben helaas door slechte organisatie op mijn laptop veel bestanden kwijt die handig waren voor dit hoofdstuk. 

Één van de bronnen die ik terug kon vinden is:

[An Integer Linear Program to Combine Container Handling and Yard Crane Deployment](https://apps.dtic.mil/sti/citations/ADA469932)

Ik zag gelijkenissen tussen onze opdracht en dit onderzoek. Ze gaan beide over de overslag van containers op en in de haven.
Het grote verschil zit erin dat deze paper probeert het werk over kranen op de haven zo gelijk mogelijk te verdelen, omdat ze ervanuitgaan dat dat tijdswinst oplevert.
Door deze paper kon ik starten met het werken aan het LP-model, ik heb eerst zoveel mogelijk van hun set/variabele/parameter overgenomen.
Vervolgens heb ik al hun restricties voor mijzelf uitgeschreven, het doel was voor mij om hierdoor beter hun model te begrijpen.
En hoe je lineair programmeren in het algemeen kan gebruiken om een vergelijkbaar probleeem op te lossen. 
Ik dacht destijds als ik dit zo uit zou schrijven en zo snappen hoe het model in elkaar zou zitten, dat ik het zelf makkelijk zou hebben om mijn probleem op te stellen.
Ik heb de restricties vervolgens overgenomen, waar het maar om één kraan ging. én sommige restricties van meerdere kranen terug naar één proberen te brengen 
als ik dacht dat dit in mijn probleem zou helpen. Verder heb ik hier uitgehaald dat ik met penalties wilde gaan werken in de doelfunctie.

Na een paar weken proberen door te bouwen op deze paper heb ik uiteindelijk het grootste deel van het werk weggegooid. 
Ik kwam er langzaam achter dat werken met penalties niet nodig zou zijn. 
En dat ik mijn restricties veel handiger kon gebruiken als ik ze niet teveel op deze paper probeerde te laten lijken.
Wat ik hier wel uitgehaald heb, zijn een paar ideëen waar ik aan moet denken bij het opstellen van restricties. 
Namelijk dat ik de containers kon definiëren dat ze aankomen in een vaste tijdsvolgorde, en dat ik een ristrictie nodig zou hebben dat er maar 1 container op 1 plek kan staan. 
