Nathan Loveless
Lab 4
Nathan Loveless
Lab 4

> 17.7/20

## Problem Set 1

1) 

````R
# Miocene: 602 
Miocene <- PresencePBDB["Miocene",]       
> sum(Miocene)

# Early Jurassic: 162
> EarlyJurassic <- (PresencePBDB["Early Jurassic",])
> sum(EarlyJurassic)

# Late Cretaceous: 375 
LateCretaceous <- (PresencePBDB["Late Cretaceous",])
> sum(LateCretaceous)

# Pennsylvanian: 133
Pennsylvanian <- (PresencePBDB["Pennsylvanian",])
> sum(Pennsylvanian)
````

> Nice!

2)  

````R
dim(PresencePBDB)
[1] 29
````

3) Pridoli, Early Devonian, Cisuralian, Late Jurassic, Eocene, Late Cretaceous, Early Cretaceous, Middle Jurassic, Paleocene, Oligocene, Miocene, Early Jurassic, Pleistocene, Middle Triassic, Late Triassic, Pliocene, Early Triassic. 

````R
Mytilus <- (PresencePBDB[,"Mytilus"])
````

4) Middle Devonian, Late Devonian, Mississippian, Pennsylvanian, Guadalupian, Lopingian. 

We know this because Mytilus was present in the epochs surrounding these epochs. The taxa would not have gone extinct and then originated again.

> Truth

## Problem Set 2
1) 

````R
> Pleistocene <- (PresencePBDB["Pleistocene",]
> MiocenePleistocene <- c("Pleistocene", "Miocene")
  MiocenePleistocene <- data.frame(Miocene, Pleistocene)
> Sumsepochs <- rowSums(MiocenePleistocene)
> table(Sumsepochs)
Sumsepochs
  0   1   2 
287 106 509 
> 509/(902+902-509)
[1] 0.3930502
````

> It should be 509/(106+509) I'm not sure what you were trying to do. -1 point

2) 1-Jaccard Index=Jaccard Distance

3)

````R
> MiocenePleistocene<-PresencePBDB[c("Miocene", "Pleistocene"),]
 vegdist(MiocenePleistocene, methods="jaccard")
               Miocene
Pleistocene 0.09430605
````

4) The Paleocene and Pleistocene are most dissimilar at  0.28498468.

````R
> Epochs <- PresencePBDB[c("Pleistocene", "Pliocene", "Miocene", "Oligocene", "Eocene", "Paleocene"),]
> vegdist(Epochs, methods="jaccard")
````

## Problem Set 3

1) 
````R
> RandomEpochs <- PresencePBDB[c("Pliocene", "Oligocene", "Paleocene", "Early Cretaceous", "Late Jurassic", "Middle Jurassic"),]
````

2) 
````R
> vegdist(RandomEpochs, methods="jaccard")
````

3) 
Poles: Middle Jurassic, Pliocene.
Gradient: Middle Jurassic, Late Jurassic, Early Cretaceous, Paleocene, Oligocene, Pliocene

4) The thing that stuck out to me is that there seemed to be a more diverse amount of marine life on the Middle Jurassic end of the gradient. This could create more competition and favor certain species more than others. Another possibility is that the Pliocene side of the spectrum seemed to be cooler.

> So, if you look closely at the order, you'll see that the epochs are in temporal order. Middle Jurassic is the oldest and the Pliocene is the youngest. So the polar gradient you made is responding most strongly to *time*. Also, what you posited, that one end is high-diversity and the other end is cooler doesn't quite match the idea of a gradient. Rember a gradient represents a single variable that is along a continuum. So high to low diversity, or high to low temperature would work, but from high diversity to low temperature doesn't really work as a spectrum. It is true that there has been a long-term cooling trend from the Middle Jurassic through to the present. -0.75 points


5) There was a mass extinction between the two epochs which could create dramatically different ecosystems, promoting some species to go extinct and others to originate, resulting in the dramatic difference.

## Problem Set 4

1) 

````R
URL <- https://paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=animalia&interval=Ordovician,Ordovician
Ordovician <- read.csv(URL)
````

> Why didn't you use the downloadPBDB function?

2) 

````R
Ordovician <- cleanGenus(Ordovician)
````

3) 

````R
Ordovician<-presenceMatrix(Ordovician,SampleDefinition="early_interval")
Ordovician<-cullMatrix(Ordovician,minOccurrences=2,minDiversity=25)
````

> You needed to use "geoplate", not "early_interval" -0.5 points

4)

````R
Ordovician[1:5,c(“geoplate”,”paleolat”,”paleolng”)]
````

> The code above doesn't quite make sense given your answer to question 3, based on the code you gave above, there would be no "geoplate", "paleolat" or "paleolng" columns to reference.

tapply(Ordovician[,“paleolat”], Ordovician[,geoplate], mean)
                            [,”paleolat”]

I think that the samples are oriented based to the latitudes. I was able to decide this based on the the means that were the results of my code.

> They are not based on either the latitudes or the longitudes. I'm not sure why thought they would be, and I'm actually not sure how you could have matched it up since your answer to Question 3 was wrong. -1 points
