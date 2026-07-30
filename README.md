INTERACTIVE MUSHROOM CLASSIFICATION

Hi! Thank you for stepping by! This is a learner's project on Power BI reporting. I would publish it, but alas I am self-employed ATM.
Here you can find the downloadable .pbix file plus the links to the public databases I used.

Methodology:  
1. The Database  
Used the comprehensive Kaggle Mushroom Classification Dataset (https://www.kaggle.com/datasets/uciml/mushroom-classification).
While originally built for identifying edibility and made over 10 years ago, its detailed structural and environmental attributes perfectly simulate a biological
screening dataset. Besides, it is a relatively small for download. Thanks UCI Machine Learning!
________________________________________
2. The Made-up Biotech Problem  
Problem Statement: An agritech startup is cultivating specific fungal strains for sustainable biomaterials and meat alternatives.
They need an interactive dashboard to map physical phenotypes (cap shapes, gill spacing, surface types) against biological classes to isolate the exact morphologic
indicators of specific strains.

Key Metrics to Calculate (DAX)  
•	Total Specimen Population: Total count of unique samples.  
•	Phenotype Dominance %: Percentage distribution of specific structural traits (e.g., broad vs. narrow gill size).  
•	Attribute Variance Score: Identifying which combinations of cap color and shape correlate with specific classifications.  
________________________________________
3. Power BI Guidelines: Import to Visualization  
Step 1: Import and Clean the Data  
1)	Open Power BI Desktop.
2)	Click Get Data > Text/CSV. Load the dataset.
3)	Click Transform Data to launch Power Query.  
4)	De-code Categorical Features: The raw data uses single letters (e.g., cap-shape has x for convex, f for flat).  
a)	Create a new table "TranslationMap" to bulk translate single letter codes with whole words by filtering ColumnName. Follow the code in the original
Kaggle database description.  
b)	Use the Advanced Editor to introduce code to replace all values in one step (used AI to optimize this code)
6)	Click Close & Apply.  
Step 2: Build the Mycology Data Model (DAX)  
Go to the Report View, click New Measure, and write these expressions to build your performance indicators:  
•	Total Strains = COUNTROWS(mushrooms)  
•	Edible Selection = CALCULATE([Total Strains], mushrooms[class] = "Edible")  
•	Safety Ratio = DIVIDE([Edible Selection], [Total Strains], 0) (Format this measure as a percentage)  
Step 3: Create the Fungi Phenotype Dashboard  
Use an "Earth-toned" color palette (forest greens, rich browns, warm ochres).  
•	Cards: Total Strains, Edible Selection, and Safety Ratio  
•	Matrix Visual: Put cap-color on rows and cap-shape on columns. Drop Total Strains into values and turn on conditional formatting Data Bars to quickly
highlight the most common biological overlaps.  
•	Stacked Bar Chart: Place habitat on the Y-axis and Total Strains on the X-axis, using population (the type of fungal organization) as the Legend. 
•	Place interactive buttons: To select specific habitats where these combinations are found  
•	Key Influencers AI Visual: Put class as the target variable to analyze, and drag all the columns that you find interesting to analyze into the "Explain By"
 bucket. Power BI will automatically run a back-end regression to tell you exactly which physical trait is the strongest mathematical predictor of the strain's
class.   
•	Place interactive tables: for fun. I did this by placing a Treemap on habitats, and interactive buttons for odor and spore-print color. Pressing the buttons
will change combinations and display of habitats where to find mushrooms with those characteristics.  

________________________________________


