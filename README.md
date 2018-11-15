# GHG repository in Github
Capstone Project Ryerson
5 raw data sets 2011, 2012, 2013, 2014, 2015

(1) Data cleansing
For each numerical variable converted the data to the same unit of measure. 
For missing values in the numerical columns inserted 0 because not applicable means quantity is 0. Now there are no missing values.
Removed the variabls - address, the unit of measure - from the raw dataset.
Removed records that had partial or inconsistent data.


(2) Initial Analysis of the data:
29 variables
 [1] "Year"                                      "Sector.Name"                              
 [3] "OrganizationName"                          "OperationName"                            
 [5] "OperationType"                             "City"                                     
 [7] "PostalCode"                                "FloorArea.Sqft"                           
 [9] "AverageHoursPerWeek"                       "AnnualFlow"                               
[11] "Electricity.kwh"                           "NaturalGas.Cubicmeter"                    
[13] "FuelOil1.2"                                "FuelOil4.6"                               
[15] "Propane"                                   "Coal"                                     
[17] "Wood"                                      "DistrictHeat"                             
[19] "DistrictHeatRenewable"                     "DistrictHeatRenewableEmissionFactor"      
[21] "DistrictCool"                              "DistrictCoolingRenewableEmissionFactor.GJ"
[23] "SwimmingPool"                              "NumberofPortables"                        
[25] "GHGEmissions.Kg"                           "EnergyIntensity.GJ.MegaLitres"            
[27] "EnergyIntensity.ekWh.sqft"                 "EnergyIntensity.GJ.m2"                    
[29] "EnergyIntensity.ekWh.MegaLitres"          

                            
Year = 2011, 201, 2013, 2014, 2015
Operation Type   35 distinct values
Distinct operation types
                Operation.Type
1       Administrative offices
2                    Libraries
3              Water treatment
4                Water pumping
5             Sewage treatment
6               Sewage pumping
7              Police stations
8                Fire stations
9  Vehicle storage maintenance
10           Community centres
11                  Classrooms
12           Hospital purposes
13          Ambulance stations
14                Laboratories
15          Student residences
16     Recreational facilities
17                     Library
18       Indoor swimming pools
19            Indoor ice rinks
20         Cultural facilities
21             Parking garages
22                      School
23               Art galleries
24  Performing arts facilities
25                 Auditoriums
26                   Multi-use
27            Indoor Ice Rinks
28                      Vacant
29          Student Residences
30                     Storage
31                  Child Care
32                      Museum
33                      Office
34                       Pools
35                      school

Variables fall into these classes:
factor integer logical numeric 
  6       3       2      18 

Analysis of 2011 data
Largest count of records:
Operation.Type               freq   totalGHG
   <fct>                       <int>      <dbl>
 1 School                       4639 735863335.
 2 Administrative offices       2344 328578271.
 3 Vehicle storage maintenance  1452 115072942.
 4 Sewage pumping               1330  16745245.
 5 Fire stations                1273  36740319.
 6 Community centres            1208  61028625.
 7 Water pumping                1132 225414759.
 8 Recreational facilities       729 113764354.
 9 Libraries                     689  34374593.
10 Cultural facilities           614  27069315.


Highest emissions of GHG:
Operation.Type               freq    totalGHG
   <fct>                       <int>       <dbl>
 1 Hospital purposes             298 6229095513.
 2 School                       4639  735863335.
 3 Classrooms                    314  541169154.
 4 Administrative offices       2344  328578271.
 5 Water pumping                1132  225414759.
 6 Sewage treatment              418  150038978.
 7 Vehicle storage maintenance  1452  115072942.
 8 Recreational facilities       729  113764354.
 9 Indoor ice rinks              416  100153447.
10 Water treatment               456   79395796.
  
  
Data set was split into 2 subsets based on whether energy intensity was given per square feet (area) or per Megaliters (volume) - mainly sewage and water treatment operation types.  Each of these subsets were split into test and training sets (70:30) ratio.

Multivariate Linear regression was done on the normalized data.
Computed the root mean square error and found the percentage of cases with less than 25% error.
"RMSE: 0.0207054807189309"
 "PRED(25): 0.229122055674518"
 
 Used the forward selection algorithm. Started with 'null', which means none of the independent variables are selected. Will come up with a selection of independent variables between 'null' and 'full'. 'full' means all the independent variables are included. Do we end up using all the variables. We set 'trace=TRUE' to see all the steps.
