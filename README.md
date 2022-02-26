# power_bi_first_introduction

Documenting the steps taken in terms of **Data Preparation**, **Data Modeling** and **Data Visualisation** using **Power BI** for the first time.

## **Data Preparation**

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

## **Data Modeling**

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

- 
