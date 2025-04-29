# New Zealand Motor Vehicle Theft Analysis

## Project Background
This project looks into motor vehicle theft data covering a seven month period from late 2021 into early 2022. The data was collected from the New Zealand Police department's vehicle of interest database. 

Records in the data contain information regarding New Zealand's regions, details about the stolen vehicles, as well as the date and location of each theft. Any patterns uncovered could be valuable for various groups, such as  public safety analysts trying to allocate resources, police departments aiming to prevent crime, car insurance companies assessing risk, or concerned citizens who want to raise their awareness.

The analysis is based on three main questions:

* **Where are thefts happening?**
    * Looking at which regions experience the most thefts, both overall and adjusted for population size (per capita), as well as investigating if there's a link between a region's population or density and the number of thefts it sees.
* **What kinds of vehicles are being targeted?**
    * Exploring the most common characteristics of stolen vehicles, such as their average age, make (brand), and general type (like sedan, SUV, etc.).
* **When are thefts occurring?** 
    * Examining the timing of thefts to see if they are more frequent during certain months or days of the week.

## Data Structure & Preparation
The dataset consists of 3 separate tables:
![5FrHfTah7R](https://github.com/user-attachments/assets/ef146ea5-afaa-45b4-898d-650416aaf642)

Initially, there were 4553 recorded thefts. Some records were removed due to the fact they only contained partial information and were missing crucial vehicle data, leaving the dataset with **4538** records.

To help with the analysis, I calculated two extra pieces of information for each theft:
1.  The approximate **age of the vehicle** at the time it was stolen (based on its model year).
2.  The **day of the week** the theft occurred.

## Summary of Findings

### Regional Trends: Where is the risk?

* Vehicle thefts were recorded in **13 out of New Zealand's 16 regions**. The three regions with no reported thefts during this period were West Coast, Tasman, and Marlborough - some of the least populated regions.
* Unsurprisingly, **Auckland** had the highest number of thefts by a large margin (1630 incidents), nearly triple the next highest region, Canterbury (660). This aligns with Auckland being the most populated and dense area.

    ![Thefts by Region](https://github.com/user-attachments/assets/551d47b0-7c38-49be-b453-0d7eb775a6f8)


* However when adjusted for population size (looking at **thefts per 1000 residents**), Auckland falls to 6th on the list. The regions with the highest theft *rates* were actually **Gisborne, Nelson, and Bay of Plenty**. This suggests residents in these areas faced a higher relative risk during this period.
* There's a **very strong connection between a region's population size and the total number of thefts**.The analysis showed a tight linear relationship (R-squared = 0,96), meaning population alone explains about 96% of the variation in theft numbers between regions. Removing the largest region, Auckland, didn't change this overall trend much (R-squared only dropped slightly to 0,84).

   ![Screenshot 2025-04-28 204609](https://github.com/user-attachments/assets/e908ae86-8d0f-4711-8447-0da007ed4768)


* The link between **population *density* and thefts is far less clear**. Although initially appearing correlated (R-squared = 0,65), this connection was almost entirely caused by Auckland. Once Auckland was excluded, the correlation essentially disappeared (R-squared dropped to 0,002). This indicates that for most regions, higher density doesn't necessarily mean more thefts in a predictable way.

    ![Screenshot 2025-04-28 204918](https://github.com/user-attachments/assets/491c6213-30a7-450d-9bcf-55ebe67ede3c)


### Vehicles Targeted: What's being stolen?

* A wide variety of vehicles were stolen, spanning **138 different makes (brands)**. The vast majority (96%) were standard brands, while only 4% were classified as luxury makes.
* Older vehicles appear to be common targets: the **average age of a stolen vehicle was 16 years**. This is probably due to the fact that newer cars have improved anti-theft measures and advanced security features, making them much harder to steal.
* The most frequently stolen car brands are shown below: 

    ![Vehicle Make](https://github.com/user-attachments/assets/f8fa623a-49e5-4858-86b9-f616a5bd7d9b)

* Looking at the *type* of vehicle, the top 5 most stolen categories were very diverse: **Station Wagons, Saloons (Sedans), Hatchbacks, Trailers, and Utilities**. This suggests thieves aren't targetting just one specific kind of vehicle.

### Seasonal Analysis: When do thefts happen?

* The data covers thefts from **October 7th, 2021, to April 6th, 2022**. During this time period 1663 thefts occurred in the last few months of 2021, and 2875 thefts occurred in the first few months of 2022.
* There was a **gradual increase in thefts over the months**, starting with 462 in October and rising to 1050 in March. April had 327 thefts in just the first 6 days. While this hints that warmer months *might* see more crime, this dataset covers too short of a period to confidently confirm a seasonal pattern. 
* Looking at the specific **day of the month**, no clear pattern emerged. The number of thefts seemed fairly random throughout the month, with various fluctuations.
  ![Day of Month](https://github.com/user-attachments/assets/bc60421b-7ff4-4e0e-a5d2-65385f1cedda)

* However, there was a noticeable pattern across the **days of the week**. Thefts were most common early in the week (Monday: 762, Tuesday: 708) and dropped significantly on the weekend (Saturday: 576, Sunday: 595). This heatmap visualizes the daily theft patterns across different vehicle types, showing if specific days are riskier for certain vehicles.
  ![WeekdayVehicle Type](https://github.com/user-attachments/assets/4eb39c48-9e2a-44f4-b912-fe172d30796f)


## Conclusion

Based on this 7-month's worth of data, here are a few recommendations:

* **Focus Resources:** Although Auckland has the highest volume of thefts, regions like **Gisborne, Nelson, and Bay of Plenty** experienced the highest *rate* of theft relative to their population. Public safety and insurance risk assessments should consider both total numbers and per-capita rates. Population size seems to be a much more reliable indicator of theft volume than density.
* **Vehicle Vulnerability:** Owners of **older vehicles**, particularly of common brands like Toyota or Nissan, should be especially careful. The wide range of stolen vehicle *types* suggests opportunism rather than targeting just one style.
* **Timing Matters (Weekly):** The clear trend of higher thefts on **Mondays and Tuesdays** compared to weekends could inform policing schedules or public awareness campaigns. Further data is needed to confirm any reliable monthly or seasonal trends.
