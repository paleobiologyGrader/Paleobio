## Problem Set 1

> 19/20

1) Max_ma: The early bound of the geological time range of occurrences. 
        Min_ma: The late bound of the geological time range of occurrences. 

2) `tapply(DataPBDB[,"max_ma"],DataPBDB[,"genus"],max)`

3) `tapply(DataPBDB[,"min_ma"],DataPBDB[,"genus"],min)`

4) 

`Ostrea, occurrances<-table(DataPBDB[,"identified_no"])`
````R
> max(occurrances)
[1] 890
> which(occurrances==890)
16870 
 214
```` 

> Strange, Anadara is the most, Ostrea is second. -1 Points
 
5) 66 Ma through the present

````R
Ostrea<-DataPBDB[which(DataPBDB[,"accepted_name"]=="Ostrea"),]
> tapply(Ostrea[,"min_ma"],Ostrea[,"genus"],min)
Ostrea 
    0 
> tapply(Ostrea[,"max_ma"],Ostrea[,"genus"],max)
Ostrea 
   66
````

## Problem Set 2
1) First, the length function is used in order to obtain the size of the vector, Lucina[,"paleolng"]. This is important because the size is needed for the sample function that is also being used. The sample function is then used to take a sample of the argument: Lucina[,"paleolng"]. It does this with replacement, specified by Replacement=TRUE. Finally, the mean is taken of the sampling that is achieved from the sample() function. 

2) `plot(density(ResampledMeans))`. Yes, I would say that it is roughly Gaussian because it has the general bell shape to the curve and there is symmetry. The graph is centered around 24 and stretches roughly 4 units in either direction where it meets the x axis.

3) The mean is 24.16227. This is very similar to the original mean of 24.1997. 

4) `ResampledMeans<-sort(ResampledMeans)`

5) 2.5%= 21.82094, 97.5%= 26.28630.  `> quantile(ResampledMeans, c(.025, .975))`

6) Confidence intervals are the bounds where 95% of the data will fall. Therefore, 2.5% will fall below these bounds and 2.5% will be above. Therefore, by finding the 2.5% and 97.5% percentiles, we are actually just finding the confidence intervals.

## Problem Set 3

1)  Almost certainly. The earliest bound of the confidence interval is at 0, therefore, we can be 97.5% sure that it is extant.

2) 

````R
> Dallarca<-subset(DataPBDB,DataPBDB[,"genus"]=="Dallarca")
> estimateExtinction(Dallarca[,"min_ma"],0.95)
Earliest   Latest 
2.58800 -3.88749
````

3) Then end of the Pliocene falls at the low bound of the confidence interval. However, the top bound of the confidence interval is almost 4 million years into the future. Therefore, it seems logical, looking at the estimateExtinction function that it could be extant.

4) We should compromise somewhere in between the two. We have seen a lot of examples of how the fossil record is not perfect and can be flawed, for example the signor lipps effect. However, the fossil record does contain meaningful data and we should not ignore it to blindly follow statistics which do not take into account ecological factors such as mass extinction.

## Problem Set 4

1) Extinction does not occur randomly. Population growth and decline responds to the environment that they are in. This can cause quick growth and quick decline. Mass extinctions events can even lead to the end of a population completely abruptly.
2) Likewise, fossil preservation does not occur randomly. Preservation responds to factors such as rock availability or erosion. 

## Problem Set 5
1) DataPBDB= 67,618. ExtantData= 57,097. 10,521 occurrences were lost.

2) 486. Unique<-c(DataPBDB, ExtantData), Unique<-unique(Unique), length(Unique) 
        52.3% are still living.
1) `tapply(ExtantData[,"max_ma"],ExtantData[,"genus"],max)`
   `tapply(ExtantData[,"min_ma"],ExtantData[,"genus"],min)`
   
4) `> MinData[which(MinData!=0)]`
5) 
````R
> Acrosterigma<-subset(DataPBDB,DataPBDB[,"genus"]=="Acrosterigma")
> estimateExtinction(Acrosterigma[,"min_ma"],0.95)
Earliest    Latest 
0.011700 -3.481128
Then repeated for each. 
9 out of 10, or 90% had confidence intervals that showed they may still be extant.
````
