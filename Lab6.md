Nathan Loveless
Lab 6

> 18/20

## Problem Set 1

1)  25,153 occurrences were lost. 

````R
>dim(DataPBDB) 
> dim(MacroPBDB)
>34166-9013=25153
````

2) Data is lost because it falls outside North America and that is the range of the Macrostrat database.

## Problem Set 2
1) 
````R
Forteau Fm, Parker Slate, Snowy Range Fm, Weymouth Fm, Langston Fm, Wheeler, Shale Marjum Limestone, Stephen Fm, Kinzers Fm, and Chancellor.                                              > specnumber(OrderMatrix), > StratOrderRichness <- sort(StratOrderRichness)
````

2) 

````R
> GenusFrequency<-colSums(GenusMatrix)
````

3)

````R
> hist(GenusFrequency)
````

4) This is a hollow curve

5) 
````R
median(GenusFrequency)
RareGenera <- which(GenusFrequency <= 2)
````

## Problem Set 3

1) 
````R
CandidateMatrix <- GenusMatrix[CandidateUnits,]
````

2) Weymouth Fm, Chancellor, Forteau Fm, Stephen Fm. I thought that these were the most likely because they were all in the top five in the Percent Shared number. Stephen Fm was fifth and not fourth, but I thought it was more likely than the Marjum Limestone because it had more richness of orders.

3) The Stephen Formation. This is famous because it contains the Burgess Shale which has extremely good preservation of a wide variety of fossils, many of which contained soft tissue. It is important because it significantly helped to understand the Cambrian paleobiology.

> This is a good guess, but the Chancellor formation is a better fit and it also contains the Burgess Shale. -2 Points
