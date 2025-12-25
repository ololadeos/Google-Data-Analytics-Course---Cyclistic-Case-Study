<img width="1416" height="1276" alt="image" src="https://github.com/user-attachments/assets/3be1088f-62cf-4fd8-8d37-7b5506e42168" />


# Google-Data-Analytics-Course---Cyclistic-Case-Study

## Introduction

This project is the final capstone of the Google Data Analytics Professional Certificate (Coursera) and represents my first end-to-end data analytics case study using real-world data.

As my first full project, the initial challenge was understanding how to approach a large dataset, structure the analysis, and translate business questions into actionable insights. To address this, I intentionally broke the project into phases to build confidence and technical depth over time.

## Project Phases
### Phase 1: Sample-based analysis using spreadsheets and R
(Completed: September 14, 2025)

### Phase 2: Full dataset analysis using SQL and Tableau
(Completed: December 12, 2025)

### Phase 3: Compare insights from sample vs full dataset to assess impact

## Case Study Background

Cyclistic is a bike-share company based in Chicago. The company’s Director of Marketing believes that increasing annual memberships is key to long-term growth.

### Business Task

How do annual members and casual riders use Cyclistic bikes differently?

The goal is to understand usage differences so the marketing team can design targeted strategies to convert casual riders into annual members.

#### Rider Types

Casual Riders: Single-ride or full-day pass users

Annual Members: Subscription-based riders

#### Data Sources

Dataset: Cyclistic (Divvy) trip data

Period: August 2024 – July 2025 (12 months)

License:
https://divvybikes.com/data-license-agreement

## Data Cleaning & Preparation
### Phase 1 — Sample-Based Analysis

Due to Excel’s row limitations, a statistically representative sample was created: 

<img width="515" height="318" alt="image" src="https://github.com/user-attachments/assets/a85e6e84-f625-4373-917c-d77c4769cbd8" />

For each month’s file, I calculated the number of entries that would give me 99% confidence level and 1% margin of error. 
I then loaded each data set into R to extract the number of rows I needed from each file and extracted those files from R. 

_install.packages("tidyverse")
library(tidyverse)
aug_2024 <- read.csv("C:\\Users\\lldos\\OneDrive\\Desktop\\Google Data Analytics Course\\Cyclistic Case Study\\Original Data\\202408-divvy-tripdata.csv", nrows = 16283)_

To clean the data: 
-	I deleted the longitudes and latitudes columns as I did not require them for my analysis (I had already saved the original data files as is). 
-	I applied conditional formatting to all the cells to check for any blank cells and deleted those as well. 
-	I checked that the length of the ride_ids was consistent using the LEN() function. 


## Analysis & Visualization (Phase 1): 
I calculated the length of each ride (ride_length) and applied conditional formatting to check if there were any rides less than 1 minute as these could have been due to docking errors. I excluded these rows from the data for the analysis. 
I extracted the following information from the data for the analysis:
Column	Calculation / Formula
Ride_duration	started_at – ended_at (formatted as HH:MM:SS)
Day_of_week	=TEXT(“started_at”, "dddd")
Month_of_year	=TEXT(“started_at”, "mmmm")

To determine the season, I assumed the following:

<img width="635" height="72" alt="image" src="https://github.com/user-attachments/assets/ecef2760-ae3e-4a3f-bceb-57ec623bfc09" />

_IF(OR(MONTH(“STARTED_AT”)=12, MONTH(“STARTED_AT”)<=2), "Winter", IF(AND(MONTH(“STARTED_AT”)>=3, MONTH(“STARTED_AT”)<=5), "Spring", IF(AND(MONTH(“STARTED_AT”)>=6, MONTH(“STARTED_AT”)<=8), "Summer", IF(AND(MONTH(“STARTED_AT”)>=9, MONTH(“STARTED_AT”)<=11), "Fall"))))_

I compared the average ride durations for casual riders and members on a daily, monthly, and seasonal basis to understand the differences between them. This was achieved using pivot tables and an interactive dashboard.

_Figure 1: Average Daily Ride Duration_ 

<img width="614" height="427" alt="image" src="https://github.com/user-attachments/assets/9355be39-0244-4e85-817f-a2687d00e1a6" />

_Figure 2: Average Monthly Ride Duration_ 

<img width="610" height="439" alt="image" src="https://github.com/user-attachments/assets/deef5707-38ec-451a-ab5e-3067a44b77a9" />

_Figure 3: Average Seasonal Ride Duration_ 

<img width="611" height="431" alt="image" src="https://github.com/user-attachments/assets/04255cad-3f22-433d-8876-91de60dc867b" />

Figures 1 and 2 show that casual riders have average ride durations that are longer than those of members, day to day and month to month. They also reveal that that the average durations for members are similar across the days and months, with a slight spike during summer months compared to the significant spike for casual riders during the same period (this can be more clearly seen in Figure 3). This could indicate an opportunity to push marketing to casual riders during the summer months. 

_Figure 4: Number of Daily Rides_ 

<img width="593" height="415" alt="image" src="https://github.com/user-attachments/assets/dd2ecd63-063b-45fd-9b6c-c8ed5522ada1" />

_Figure 5: Number of Monthly Rides_ 

<img width="593" height="415" alt="image" src="https://github.com/user-attachments/assets/80a7cb85-f9a3-4499-81ce-f796b2eab991" />

_Figure 6: Number of Seasonal Rides_ 

<img width="593" height="415" alt="image" src="https://github.com/user-attachments/assets/68ee2ff2-6aa9-4c5a-a6f9-ee15ad7c22d6" />

Despite the longer rides by casual riders shown in Figures 1 – 3, Figures 4 – 6 reveal that there are more annual members taking rides than casual riders on a daily, monthly, and seasonal basis. 

_Figure 7: Number of Rides by Type 

<img width="593" height="415" alt="image" src="https://github.com/user-attachments/assets/64fe74ca-875b-43bb-bed8-a28fdd7b746c" />

Figure 7 shows that casual riders use the electric options more than members. There could be an opportunity to market around this observation. 


## Phase 2 – Completing the analysis using the full dataset; SQL and Tableau

Using SQL, I extracted the data I would need to run the same visualisations and in phase 1. All queries run are found here: sql queries. 

[Tableau Visualization](https://public.tableau.com/views/CyclisticRiders/CyclisticRiders?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

Comparing the results from using all of the data to using a sample data size, it is seen that the same conclusions can be drawn both ways. This shows the efficacy of sample data in cases where 


## Recommendations

Following the analysis of the data from Cyclistic, I can make the following recommendations to the Marketing team to target casual riders:
1.	More promotion of annual membership during the weekends and from spring into summer months, as there are significantly more rides taken by casual riders during those periods. 
2.	Taking advantage of the longer riders by casual riders, a promotion including redeemable points based on how long a ride is can be introduced as part of the rewards of an getting annual membership. 
3.	A discount on annual membership that highlights the benefits of a one-time payment as opposed to several payments. 
4.	Highlighting the benefits of using Cyclistic: fitness, traffic avoidance, saving on fuel. 
An additional analytical recommendation is to make use of rider ids to further determine the behaviour of casual riders. This will help in more personalised promotion of annual membership based on the behaviour of each rider. 




