> 19.5/20

## Problem Set 1

1. West
2. The plot function graphs the modern map. Col= controls the color of the figure. Rgb is used to dictate colors, the 1 makes the graph red, while the 0s make there no green or blue used. The lty=0 makes there be no lines. add=TRUE adds it so it overlays the other plot. 
3.  ````AlbianMap<-downloadPaleogeography(Age=110)````
4. ````plot(AlbianMap,col=rgb(0,1,0,0.33),lty=0,add=TRUE)````
5. North and South.
6. East and West

#### Problem Set 2
1. ````> PaleoceneEocene<-downloadPaleogeography(Age=56); > plot(PaleoceneEocene, col=rgb(1,0,0,.33))````
2. ````>DataAnthozoan<-downloadPBDB(Taxa=c("Anthozoa"),StartInterval="Paleocene",StopInterval="Eocene")````
3. 2847
````R
Occurrence_no: A unique identifier of the occurrence
Record_type: The type of object. I.e: occurrence.
Reid_no: if this is marked, it indicated that the occurrence was reidentified.
Flags: If an R is present, the record representing an identification has been superceded by a more recent identification. 
Collection_no: Identifier of the collection that the occurrence is a part of
Identified_name: Occurrence’s taxonomic name
Identified_rank: taxonomic rank
Identified_no: identifier of the taxonomic name
Difference: marked if the identified name is different than the accepted name.
Accepted_name: accepted taxonomic name
Accepted_attr: year and author of the of the accepted name.
Accepted_rank: taxonomic rank of the accepted name
Accepted_no: the unique identifier of the accepted name
Early_interval: the lower bound of the time range of the occurrence
Late_interval: the upper bound of the time range of the occurrence
Max_ma: specific year in Ma of the lower bound, associated with the occurrence
Min_ma: specific year in Ma of the upper bound, associated with the occurrence
Reference_no: identifier of the reference for the entry of this date
Paleomodel: primary model specified by the parameter pgm. 
Paleolng: paleolongitude of the collection
Paleolat: paleolatitude of the collection
Geoplate: the geoplate where the collection lies
Phylum, Class, Order, Family, Genus: the taxonomic classification of the occurrence.
````
5. ````points(DataAnthozoan[,"paleolng"], DataAnthozoan[,"paleolat"])````
6. They seem to cluster around the Mediterranean region. Anthozoa are marine organisms, therefore there must have been an ocean present at the time. 

#### Problem Set 3
   1. ````DataPerissodactyla<-downloadPBDB(Taxa=c("Perissodactyla"),StartInterval="Paleogene",StopInterval="Paleogene")````
   2. They are odd-toe ungulates. Some examples are horses, zebras, and donkeys.
   3. ````112723<-DataPerissodactyla[which(DataPerissodactyla[,"collection_no"]==112723)````
   
   > Try to avoid naming objects with numeric strings.
   
   4. geoplate=501
   
   > -0.5 points. It's pakistan! 
   
   5. ````> RegionX<-DataPerissodactyla[which(DataPerissodactyla[,"geoplate"]==501),]```` There are 84 occurences. 
   6. From the Albian to the Cretaceous, the geoplate moved South West. From the Cretaceous to the Modern, the geoplate moved further South and back East, to about where it was in the Albian. 
   7. A: I do not think this is likely because looking at the overall occurrences of Perissodactyla, we do not see any occurrences between the location in geoplate 501 and China. 
      B: For the same reasons as stated above, I do not think this is likely, because we would see more occurrences between the two locations.
      C: I find this the most likely because it would explain why there are not any occurrences of Perissodactyla during the Paleogene.
