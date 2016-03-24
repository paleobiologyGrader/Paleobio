Nathan Loveless
Lab 5

> 14.25/20

## Problem Set 1
1) 634. table(BivalveAbundance[“Miocene”,]) take the number of 0s, subtracted from the total. 2272-1638= 634

> Interesting approach!

2) .22. 

````R
PlioceneBrachiopod<-BrachiopodAbundance["Pliocene",]
> max(PlioceneBrachiopod)
> sum(PlioceneBrachiopod)
> 22/99 
````

3) 0.9784588. 

````R
BrachiopodsOrdovician<- BrachiopodAbundance["Late Ordovician",]
> sum(BrachiopodsOrdovician)
[1] 6154
> 1-sum((BrachiopodsOrdovician/6154)^2)
[1] 0.9784588
````

4) 7.338286  

````R
if (min(BivalvesLateCretaceous) < 0 || sum(BivalvesLateCretaceous) <= 0) return(NA)
p.norm <- BivalvesLateCretaceous[BivalvesLateCretaceous>0]/sum(BivalvesLateCretaceous)
-sum(log2(p.norm)*p.norm)
````

> Whoa you got a bit off base here, you did not need an if( ) statement. -1 Points


5. 6.508088

````R
if (min(BivalvesPaleocene) < 0 || sum(BivalvesPaleocene) <= 0) 1return(NA)
p.norm <- BivalvesPaleocene[BivalvesPaleocene>0]/sum(BivalvesPaleocene)
-sum(log2(p.norm)*p.norm)
````

> -1 Points

6. -11.31324% This difference can be related to the mass extinction that took place at the boundary of the two time periods.

> -0.25 Points, How did you get this number?

7. -56.40371659% This does better demonstrate the true difference that occurred. This is because the diversity indices are not an accurate measure of diversity until they are converted to effective numbers by exponentiating them. 

> -0.5 Points

## Problem Set 2

1) 
````R
> specnumber(BivalveMiocene)    [1] 634
````

2) 
````R
> diversity(BrachiopodsOrdovician, index = "simpson")      [1] 0.9784588
````

3) 
````R
> diversity(BivalvesLateCretaceous)     [1] 5.086512
````

> You didn't notice this is different from what you got above?

4) > diversity(BivalesPaleocene)        [1] 4.511063


## Problem Set 3

1) 
````R
> cor(BivalveRichness, BrachiopodRichness)      
[1] -0.567095
````     
Therefore, the Brachiopod richness is negatively correlated to Bivalves.

2) 
````R
> cor(BivalveDiversity, BrachiopodDiversity)
[1] 0.4853795
````

> That is not the correct number, I'm not sure where you got it from! -1 Points

The diversity of Brachiopods is positively correlated to Bivalve diversity.

3) The greatest drop in Brachiopod richness occurred between Early Devonian and the Pridoli.

> No, during the end-Permian mass extinction -1 Points.

## Problem Set 4

1) 
````R
> SampleBrachiopodAbundances<-apply(BrachiopodAbundance,1,sum)
> SampleBrachiopodAbundances[which(SampleBrachiopodAbundances==min(SampleBrachiopodAbundances))]
Pleistocene 
        63 
> StandardizedBrachiopodRichness<-apply(BrachiopodAbundance,1,subsampleIndividuals,Quota=63)
> StandardizedBrachiopodRichness
   Mississippian     Pennsylvanian  Early Ordovician Middle Ordovician   Late Ordovician 
           42.26             35.14             38.25             46.74             41.70 
      Llandovery           Wenlock            Ludlow           Pridoli    Early Devonian 
           42.05             43.71             44.07             41.17             50.33 
 Middle Devonian     Late Devonian        Cisuralian     Late Jurassic            Eocene 
           40.71             38.85             50.45             33.99             26.82 
 Late Cretaceous  Early Cretaceous   Middle Jurassic         Paleocene         Lopingian 
           28.49             36.50             37.20             17.06             43.53 
  Early Jurassic       Guadalupian   Middle Triassic     Late Triassic           Miocene 
           30.76             50.45             33.55             36.72             24.48 
  Early Triassic          Pliocene       Pleistocene         Oligocene 
           23.71             18.96             19.00             25.42
````

2)  

````R
> cor(BrachiopodRichness, StandardizedBrachiopodRichness)
[1] 0.879321
````

We can see that the the correlation between standardized and nonstandardized Brachiopod richness is very high because perfect correlation is 1 and the .879 value is very close to that.  

3) 

````R
> plot(StandardizedRichness, StandardizedBrachiopodRichness, xlab = "Bivalve", ylab = "Brachiopod")
> plot(BivalveRichness, BrachiopodRichness, xlab = "Bivalve", ylab = "Brachiopod") 
````
The standardized plot has a fairly random distribution across the plot. The non-standardized plot is more clustered close to the axis of the plot. The standardization does matter because it allows us to have a more evenly balanced set of data that is unbiased for one epoch over another. 

> That is not quite how you should read this plot, think of it as a line going from youngest to oldest, and you are seeing the ups and downs in biodiversity. -1 Points

4. I think that the negative correlation that Brachiopods have with Bivalves where richness is concerned and the plot of the richness of the two genera prove that when Bivalves increase in richness, Brachiopods decrease. However, I don’t think that there is enough data here to show that out competition was the overall cause of this relationship. There could be a correlation to another variable that this lab does not consider.

> Great Answer!
