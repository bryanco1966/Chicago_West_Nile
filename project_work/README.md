### Executive Summary


Problem
West Nile Virus, an arthropod-borne virus, is a threat to the health and productivity of the people of Chicago.

Can we use machine learning to predict West Nile Virus such that the city of Chicago can maximize the impact of its integrated pest management system?

Data
The training data set consists of data from 2007, 2009, 2011, and 2013; the test set consists of data from 2008, 2010, 2012, and 2014.
The training data includes:
Id: the id of the record
Date: date that the WNV test is performed
Address: approximate address of the location of trap. This is used to send to the GeoCoder.
Species: the species of mosquitos
Block: block number of address
Street: street name
Trap: Id of the trap
AddressNumberAndStreet: approximate address returned from GeoCoder
Latitude, Longitude: Latitude and Longitude returned from GeoCoder
AddressAccuracy: accuracy returned from GeoCoder
NumMosquitos: number of mosquitoes caught in this trap
WnvPresent: whether West Nile Virus was present in these mosquitos. 1 means WNV is present, and 0 means not present.
The testing data set consists of all of these variables with the exception of NumMosquitoes.

For the weather dataset, we replaced missing values M (missing) and T (unrecorded trace amounts signified only with the string T) with -1. This allows the iterative model to treat everything with a missing or trace value the same.

Solution
Careful thought was required in order to determine our model should optimize. Since spraying for mosquitoes engenders cost for governmental entities, should we optimize our model for accuracy?  After considering the monetary, temporal, environmental, and medical costs of West Nile Virus and its associated preventative and management strategies, we decided to optimize our model for sensitivity: we aimed to catch all of the positive West Nile cases, even if that meant that we also caught some negative West Nile cases. Due to West Nile’s high cost to human wellness and life, we determined that it would be better to spray in an area that does not have West Nile than to not spray in an area that does have West Nile.

After testing our data using several models, we determined that the Adaboost model was the best model for this dataset. We chose the Adaboost model because: 1) we saw non-normality in the distribution of our data during our Exploratory Data Analysis; 2) we had large categorical variables (e.g. block) and didn’t want to decrease computational efficiency by dummying these large categorical variables and adding them to an already sizable data set.

We were able to increase our sensitivity rate for a baseline of just over 4% to almost 80% while maintaining a specificity rate of  80%.   These rates used a threshold probability of .5.  We can adjust our rates to optimize for the desired ratio determined by the city.


We recommend that the city consider the following features in order to maximize the impact of its integrated pest management system:

* Use predictions to identify high volume West Nile areas for spraying when trap data is not available.

* Use risk factors identified by prominent features to predict when spraying season would be more prevalent.

* Use predictions of West Nile to inform medical providers of presence of West Nile in the area.


Recommendations for Next Steps
We are concerned about the differing collection methods of the two stations from which the weather data was collected.  Station 1, the Chicago O’Hare International Airport, collected data on several elements of weather that Station 2, Chicago Midway International Airport, did not. The lack of uniformity makes it difficult to configure a plan for the entirety of Chicago -- although it is clear that the plan should be granulated as needed to serve the heterogeneous communities of the city, weather data could be increasingly important to measure in as much detail as possible as the climate heightens and the conditions for this type of mosquito improve.
