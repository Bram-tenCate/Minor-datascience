# Conclusion

## foodboost

Voor het foodboost hebben we de volgende conclusies getrokkken.

deelvraag 1: Aan de hand van welke methode kunnen de voorkeuren van een gebruiker achterhaald worden?

Er zijn meerdere methodes om de voorkeuren van een gebruiker te achterhalen.
Uit de bron die ik onder het kopje Domain Knowledge- Literature research laat zien blijkt, wanneer je genoeg gebruikersdata hebt, een systeem dat user-based is het beste recommendaties en daarmee voorkeuren voor een gebruiker kan voorspellen.
Echter hebben wij geen echte gebruikersdata. Waardoor wij de true-labels hier niet voor hebben, en het moeilijk zal worden om er een model voor te trainen. 
Een item-based model weet het alsnog beter te voorspellen dan random recepten aan te raden. 
Daarom hebben wij aangenomen dat een gebruiker één favoriete keukens heeft, en proberen wij aan de hand van Machine learning modellen te achterhalen op basis van ingrediënten en tags welke keuken iemmand het lekkerst vind.


deelvraag 2: Doormiddel van welk model kan de favoriete keuken van een gebruiker voorspeld worden?

Tijdens het onderzoek hebben wij veel Machine learining modellen geprobeerd. Hieronder vallen k-nearest, decision tree, decision forrest, en naive bayes.
Meerdere machine learning modellen konden de favoriete keuken met een hoge accuracy, precision en recall bepalen voor gesimuleerde gebruikersdata.
Wij zijn voor onze applicatie gegaan voor een k-nearest neighbors die dit op test data met respectievelijke percentages van 93.594; 94.908; en 93.571 wist te voorspellen. 

deelvraag 3: Op basis van welke methode kunnen er passende recepten aanbevolen worden?

In onze testdata hebben alle gesimuleerd-gebruikers 10 recepten uit één keuken geliked. Aan de hand daarvan is dus een knn-model getrained dat de favoriete keuken van de gebruiker probeert te achterhalen. Door in de app dit uiteindelijk ook te kunnen doen laten wij mensen eerst 10 gerechten liken uit een lijst van recepten die random wordt aanbevolen. Vervolgens laten wij het model dat wij getrained en getest hebben op de gesimuleerde gebruikers voorspellen welke keuken iemands favoriet is. Vanaf dan zullen de komende gerechten die worden aanbevolen in de app geselecteerd worden door een random gerecht uit deze keuken te nemen.

Hoofdvraag: Hoe kan de applicatie de dichts aansluitende hoofdgerechten aanraden op basis van de voorkeuren van de gebruiker?

Wij hebben aangenomen dat het best dichts aansluitende hoofdgerecht voor iemand een nieuw hoofdgerecht uit zijn favoriete keuken is. Daarom laten wij een gebruiker 10 gerechten liken op onze tinderachtige applicatie liken. Aan de hand van tags en ingrediënten laten wij een knn-model de favoriete keuken van iemand achterhalen. Vervolgens wordt er uit deze keuken een random gerecht gekozen.

## Containerproject

De hoofdvraag tijdens het Containerproject was “In hoeverre zijn Reinforcement Learning en Lineair Programmeren geschikt voor het optimaliseren van het stapelingsproces in de haven?”

We zijn als groep hierop op de volgende conclusie ervoor uitgekomen:

"Uit de resultaten van het onderzoek naar de geschiktheid van Reinforcement learning en lineair programmeren voor het optimaliseren van het stapelingsproces in de haven is gebleken dat het RL-model consistenter is dan het huidige LP-model, echter kan er geen uitspraak worden gedaan over de bruikbaarheid in een reële situatie doordat de uitwerking op zeer kleine schaal is uitgevoerd." 

Ik ben het hiermee eens. Het lineair programmeergedeelte waar ik mij op gefocust heb, geeft helaas in de helft van de gevallen namelijk een onjuiste oplossing terug. Met onjuist bedoel ik dat er een container zo staat, dat het andere containers blokkeert. En je deze dus weg zou moeten halen op het moment dat je de schepen in wilt gaan laden.
