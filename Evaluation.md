# Evaluation

## Foodboost
geen Evaluation bijdrage geleverd

## container project

In de paper voor het containerproject heb ik in het hoofdstuk "future work" de rode stukken text samen Juriaan geschreven. 

![future work](https://github.com/Bram-tenCate/Minor-datascience/blob/main/future%20work.png)


**Edit:**
inmiddels is de paper een beetje ingekort waardoor deze stukken veranderd zijn, de essentie is hetzelfde gebleven.

Ik had heel graag in deze minor hiervoor een model werkend gekregen die op stukken kade van reeële grote. De meest optimale feasible oplossing teruglevert. 
Lineair progrommeren was voor mij alweer 2 jaar geleden. Dus ik ben heel blij opnieuw geleerd te hebben hoe je een model kan opstellen. Voor het future work is het dus als eerste van belang om te kijken of het model zelf dus echt goed in elkaar zit (waar ik van overtuigd ben, Karin volgens mij ook). Vervolgens kijken waarom het model dan toch een onjuiste oplossing teruggeeft. 

Daarna zou ik zelf een optimalisatieslag in de beginstap van het grootste belang vinden. Daarmee bedoel ik dat het helemaal niet optimaal is om altijd de eerste containers te pakken. Om dit uit te leggen met een voorbeeld. Stel je hebt een veld van 2*4*2 om te vullen, en er komen 14 containers aan. Je weeet dat de eerste 6 containers die gepakt worden voor schip 3 zijn, dan 2 containers voor schip 2, dan 2 containers voor schip 1, en dan weer 4 containers voor schip 3. Door de eerste 8 containers te pakken voor schip 3 om weg te zetten in een rijtje, forceer je jezelf naar een infeasible oplossing toe. Het zou in dit geval veel handiger zijn om de laatste 8 containers (beodeld voor schip 3) te pakken hiervoor. Misschien is dit in worden moeilijk te volgen, dus heb ik dit hieronder proberen uit te tekenenen. Hierin staat in de eerste afbeelding hoe het nu gaat, de tweede afbeelding hoe het na een optimalisatieslag hierin zou kunnen gaan. 

![future work 1](https://github.com/Bram-tenCate/Minor-datascience/blob/main/future%20work1.png)

![future work 2](https://github.com/Bram-tenCate/Minor-datascience/blob/main/future%20work2.png)
