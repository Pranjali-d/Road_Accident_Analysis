# Road_Accident_Analysis


## Dashboard Preview:
![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/dashbaord%20preview.jpg)

## Objective:

The aim of this project was to analyze road accidents in the UK for the year 2021 and 2022 so as to gain insights into the following requirements:

###  Primary KPIs — 
Total casualties taken after accidents, total casualties and percentage of total casualties with result to accident severity and maximum casualties by type of vehicle.

### Secondary KPIs — 
Total casualties with respect to vehicle type, monthly trend showing the comparison of casualties for the current year and previous year, maximum casualties by road type, distribution of total casualties by road surface, the relation between casualties by area/location and by day/night

## Project Stakeholders:

This project analysis will particularly be useful for the following stakeholders: the Ministry of Transport, Road Transport Department, Police Force, Emergency Services Department, Road Safety Corps, Transport Operators, Traffic Management Agencies, the Public, and the Media.

## About the dataset:

The dataset used for this project was gotten from Data Tutorials on YouTube, which in turn was obtained from Kaggle. This dataset is not a real-time data, it is a demo data which was used solely for practice purpose.

## Metadata:
The dataset contains 307,974 rows and 21 columns and the file extension is an .xlsx file

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/raw%20dataset.jpg)

This data analysis project utilized the following steps: Data Cleaning, Data Processing, Data Analysis, Data Visualization and Report/Dashboard.

## STEP 1: DATA CLEANING

After loading the dataset into Microsoft Excel, I proceeded to duplicate it onto another sheet, which I named “Working Dataset.” The purpose of this duplication was to preserve the integrity of the original data and prevent any irreversible changes.

During the data cleaning process, I observed that the columns exhibited varying widths and were not adjusted appropriately based on the content within each cell. To fix this, I selected all the cells and double-clicked the black arrow situated at the right border of the first column heading. This action automatically adjusted the column width to accommodate the contents within the cells. I also applied a filter to the column headers. Following the application of the filter, I proceeded to filter each column individually to identify any missing data or typographical errors that required rectification. This step allowed me to meticulously examine and clean the dataset to ensure its accuracy and consistency.

#### The Accident Index —
This column serves as the primary key in the dataset, with each entry possessing a unique index number. As a result, it is essential to ensure that there are no duplicate values or blank cells within this column. To verify this, I utilized the filter button to examine all the values within the Accident Index column. Through this process, I confirmed that there were no instances of duplicated values or blank cells.

#### Accident Date: 
The column for Accident Date only includes dates from 2021 and 2022, which was appropriate for my analysis.

Days of the Week, Junction Control and Junction Detail: There were no blank cells or spelling mistakes in these columns.

#### Accident Severity: 
This column contains four categories of accident severity: Fatal, Fetal, Serious and Slight. However, Fetal is not a valid category as I observed it was a spelling mistake made during data entry. To correct this, I selected the first cell in column F (Accident Severity) and pressed the Ctrl+Shift+down arrow to select the whole column. Then I pressed Ctrl+F to open the Find and Replace dialogue box and replaced “Fetal” with “Fatal”. This resulted in 49 replacements. The accident severities in Column F were corrected to three categories namely: ‘Fatal’, ‘Serious’ and ‘Slight’.

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/49%20replacemnet%20were%20made.jpg)

#### Carriageway hazards, Road surface conditions and Weather conditions — 
I detected that these columns had 3, 1534 and 6057 blank rows respectively, however, I decided not to clean these columns because removing these blank cells could lead to loss of important information or skew the analysis results.

#### Other Columns:
I checked the remaining 12 columns namely: latitude, light conditions, Local authority, Longitude, Number of casualties, Number of vehicles, Police force, Road type, Speed limit, Time, Urban or Rural, and Vehicle type and found out there wasn't a typo error or data cleaning required .


## STEP 2: DATA PROCESSING

To perform a monthly trend analysis of the casualties for the current and previous year, based on the secondary KPI, I created two customized columns in the dataset: “Month” and “Year”. I used the TEXT function to extract the month and year values from Column B (accident date) into cells C2 and D2 respectively. The formulas I used were (=TEXT B2, “mmm”) for the month and (=TEXT B2, “yyyy”) for the year. I filled the formulas to the entire month and year columns by double-clicking on the auto-fill feature in cells C2 and D2 respectively.

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/text%20function%20for%20month.jpg)

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/after%20aauto%20fill%20the%20month.jpg)


![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/text%20function%20for%20year.jpg)

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/auto%20fill%20year.jpg)

## STEP 3: DATA ANALYSIS/DATA VISUALISATION

I performed these two steps together because I created the charts as I built the pivot tables. To build a pivot table, I selected any cell in the “Working Dataset” and from the Insert tab, I clicked on Pivot table > Table/Range > New Worksheet > Ok. After inserting the Pivot Table, I named the sheet “KPI”.

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/inserting%20pivot.jpg)

Excel’s pivot tables serve as a powerful data analysis tool capable of various operations such as sorting, grouping, reorganizing, counting, summarizing, averaging, and totalling data from extensive tables. These tables also offer advanced calculation capabilities, allowing for customized report layouts, highlighting crucial information, and incorporating charts and slicers. By leveraging pivot tables, data becomes more manageable, facilitating improved comprehension and reducing complexity. Additionally, pivot tables contribute to time savings and interactivity, enhancing the overall data analysis experience.

### Generating pivot tables and charts for the Primary KPIs:

#### Total number of casualties and the total number of casualties with respect to accident severities —
I created these pivot tables to display the sum of all casualties and the sum of casualties with respect to fatal, serious and slight accident severities.

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/sum%20of%20casualities.jpg)


### Percentage of total casualties with result to accident severity and maximum casualties by type of vehicle

#### Fatal Casualty— 
I used the GETPIVOTDATA function to extract the number of fatal casualties from the pivot table above. I extracted the total number of fatal casualties into cell E10 with the formula =GETPIVOTDATA(“Number_of_Casualties”,$A$9,”Accident_Severity”,”Fatal”). I also extracted the total number of non-fatal casualties (i.e., serious and slight casualties) into cell E11 using the formula =GETPIVOTDATA(“Number_of_Casualties”,$A$9,”Accident_Severity”,”Serious”)+GETPIVOTDATA(“Number_of_Casualties”,$A$9,”Accident_Severity”,”Slight”). I named this category “Other”. To get the maximum number of fatal casualties, I divided the number of fatal casualties (E10) by the sum of fatal casualties (E10) and others (E11) in cell F10 using the formula =E10/($E$10+$E$11) and converted the value to a percentage. To find the maximum number of non-fatal casualties, I divided “others”(E11) by the sum of fatal casualties (E10) and “other”(E11) in cell F11 using the formula =E11/($E$10+$E$11) and converted the value to a percentage.

NB: The sum of fatal casualties (E10) and “other” (E11) is also the sum of all three casualties.

#### Serious and Slight accident casualties —
I applied the same method to calculate the serious and slight accident severities.
I utilized doughnut charts to visualize the percentage of fatal, serious and slight accident casualties.


![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/donut%20charts.jpg)


### SECONDARY KPIs

#### Total casualties with respect to vehicle type —
I created a pivot table to display the sum of number of casualties by vehicle type.

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/sum%20by%20vehicl%20etype.jpg)


I applied the calculated items in pivot table to group similar vehicle classes, such as car and taxi/hire car, motorcycle 125cc, motorcycle 50cc, motorcycle over 125cc and motorcycle over 500cc, bus and minibus etc.


![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/combining%20vehicle%20type%20by%20pivot.jpg)

After combining all similar vehicle types, I had 6 vehicle types namely, agricultural vehicle, cars, bus, van, bike and others

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/vehicle%20type.jpg)


I also created a pivot table for car casualties where I used the GETPIVOTDATA function to extract the number of car casualties from the pivot table above. I extracted the total number of car casualties into cell I26 using the formula: =GETPIVOTDATA(“Number_of_Casualties”,$A$25,”Vehicle_Type”,”Cars”). I also extracted the total number of non-car casualties (agricultural vehicle, bus, van, bike and others) into cell I27 with the formula: =GETPIVOTDATA(“Number_of_Casualties”,$A$25,”Vehicle_Type”,”Agricultural vehicle”)+GETPIVOTDATA(“Number_of_Casualties”,$A$25,”Vehicle_Type”,”Bus”)+GETPIVOTDATA(“Number_of_Casualties”,$A$25,”Vehicle_Type”,”Van”)+GETPIVOTDATA(“Number_of_Casualties”,$A$25,”Vehicle_Type”,”Bike”)+GETPIVOTDATA(“Number_of_Casualties”,$A$25,”Vehicle_Type”,”Others”) and named this category “Others”. After this, I calculated the percentage of car casualties with the formula =I26/($I$26+$I$27) and calculated the percentage of “Others” with the formula = I27/($I$26+$I$27). I converted the values to percentages and visualized the percentage using a doughnut chart.


![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/donut%202.jpg)

#### Monthly comparison of casualties for the year 2021 and 2022 —
I used a pivot table to display the monthly comparison of casualties for the year 2021 and 2022. To make a combo chart, I copied and pasted the values for both years outside the pivot table. Then I applied these values to generate a combo chart.

PS: To create a combo chart, which is a type of PivotChart that displays two chart types on the same chart, you need to extract the values outside the pivot table first. This is because the combo chart needs to access the values directly from the worksheet, not from the pivot table.

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/max%20casua%3Bitties.jpg)


#### Maximum casualties by road type —
I created a new worksheet named “Road type” where I displayed the maximum casualties by road type in a pivot table. I formatted the values to show thousands with a “K” suffix by selecting the values, pressing Ctrl+1 and choosing a custom number format (0.0, “K’). Then I generated a bar chart to visualize these values.


![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/customized%20number%20category.jpg)

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/pivot%20for%20sum%20of%20casualties.jpg)


#### Distribution of total casualties by road surface — 
To analyze the total number of casualties based on road surface conditions, I utilized a pivot table. By leveraging the “calculated item” feature in Pivot table Analyze section, I grouped the road surfaces into categories such as Dry, blank (indicating missing data), Wet, and Snow/Ice. To generate a tree map visualization, I extracted the values from the pivot table, enabling me to represent the data in a visually informative manner.

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/casualties%20by%20area%20or%20loacation.jpg)

#### Casualties by area/location and by day/night —
In another sheet titled “doughnut chart”, I created a pivot table to display the number of casualties by location and light conditions. I converted the values using the customized number category (0.0, “K”) and visualized them using doughnut charts.

![image](https://github.com/Pranjali-d/Road_Accident_Analysis/blob/main/References/donut%202.jpg)

## STEP 4: DASHBOARD CREATION 
I created a dedicated sheet called “Dashboard” where I extracted the KPI values (total casualties, fatal, serious, slight casualties, car casualties, etc) into my dashboard. To personalize the dashboard’s appearance, I customized the font, size, and colors of its elements according to my preferences.

Please note that to extract values from the pivot table into the dashboard, it is necessary to copy and paste them outside the pivot table first. Failure to do so will prevent the dashboard from accessing the values stored in the pivot table.

To enhance the interactive nature of the dashboard, I implemented a timeline functionality, allowing effortless navigation across different time periods such as years, months, and quarters. Furthermore, I integrated a slicer that simplifies the selection of specific localities, including urban and rural areas. To optimize the dashboard’s overall functionality, both the slicer and timeline were interconnected with all the sheets in the dashboard. On the leftmost section of the dashboard, I integrated interactive tools that provide diverse functionalities. These tools enable users to access an analysis sheet, presenting the comprehensive results of my calculations and analyses. Additionally, I included an email link for individuals who wish to contact me, as well as a separate hyperlink directing users to the Wikipedia page containing road accident data. Additionally, I developed a data analysis sheet where I meticulously documented all the calculations performed during the project. This sheet serves as a comprehensive record of the extensive analyses conducted as part of the project.

To explore the full interactivity of my dashboard, kindly click on this [link.](https://onedrive.live.com/view.aspx?resid=6285C6C965D079A4!381&ithint=file%2cxlsx&wdo=2&authkey=!ALL_cUuo81tx82E)
