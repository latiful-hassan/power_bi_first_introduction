# power_bi_introduction

Documenting the steps taken in terms of **Data Preparation**, **Data Modeling** and **Data Visualisation** using **Power BI**.

## **Data Preparation**

The raw data needs to be cleaned and formatted before we can proceed with visualisation/analysis.

- Open **Power Query** and connect to *population-1950-1999*, *population-2000-2049* and *population-2050-2100*

- Below is an example of the raw data from 1950-1999:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/population-1950-1999_raw.png)

- Formatted data:
  * Removed top rows
  * Use first row as headers
  * Filtered null values
  * Removed blank rows
  * Append all three queries
  * Removed columns
  * Renamed columns
  * Replaced incorrect values
  * Changed data types
  * Handled errors

- After basic formatting:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/population_combined_formatted_p1.png)

- **Unpivoted** *Population Male* and *Population Female* columns
- Split the **Attribute** column 

- After unpivoting:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/unpivot.png)

I will be using a ***Star Schema*** to create the data model, below are the steps taken.

### DIM Region

- Created a **Reference** from *population-combined* to create a *Dim-Region* table
- Removed duplicates
- Connected to the *codes-country-region* text file and formatted to import region data
- Created a new table called *region-full-names*
- Copied the *Region Code* into the new table and gave them names
- Performed a **Merge** on *codes-country-region* and *region-full-names*
- There are some *null* values so I created a separate query called *countries-added* to appened to *codes-country-region*
- Removed duplicates
- Now we can merge *DIM-Region* to *codes-country-region to obtain region data

- A sample of the finished *DIM-Region* table:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/dim_region.png)

### DIM Age

- Created a **Reference** from *population-combined* to create a *Dim-Age* table
- Removed duplicates
- Created a new **Index Column** starting from 1 called *Age ID*
- Created a new column called *Age Group Max* based on the *Age Group* by using **Extract**
- Created a **Conditional Column** to add aage categories based on *Age Group Max*

- A sample of the finished *DIM-Age* table:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/dim_age.png)

### FACT Population

- Created a **Reference** from *population-combined* to create a *FACT-Population* table
- Merged *FACT_Population* with *DIM-Age* to import *Age ID*
- Multiplied the *Population* column by 1000

- A sample of the finished *FACT-Population* table:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/FACT_population.png)

## **Data Modeling**

- In the **Model View** in Power BI, I created relationships on our tables via the respective IDs:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/relationships.png)

## **Data Visualisation**

- Below is an example of a basic line and bar bar:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/basic_charts.png)

- Here we can see an edited **Tooltip** where *AveragePopulation* is also shown at each point:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/tooltips.png)

- Creating a **Hierarchy** to be able to **Drill** the data points more effectively:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/hierarchy.png)

- Adding **Conditonal Formatting**:

![](https://github.com/latiful-hassan/power_bi_introduction/blob/main/first_project_screenshots/conditional_formatting.png)

- After some additional formatting to clean things up:

![]()
