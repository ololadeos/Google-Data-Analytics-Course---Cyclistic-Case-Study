# Google-Data-Analytics-Course---Cyclistic-Case-Study
This project was the last course in the Google Data Analytics course on Coursera and provided the opportunity to make use of the knowledge gained and practice the new skills acquired on real data. 







INTRODUCTION
This project is the last course in the Google Data Analytics course on Coursera and provided the opportunity to make use of the knowledge gained and practice the new skills acquired on real data. 
As my first data analysis project, it was a bit overwhelming at first as I did not really know where to start; I kept on reading the document over and over again, taking notes, having an idea of the information I needed to answer the business task but was a bit blocked on how to begin to tackle the large dataset I had to work with. 
I did some research and was able to find a way forward and have results with which I am currently satisfied. I used the word “currently” because I intend to take the project further. 
My intentions are:
Phase 1: Complete the case study using a sample data size – I started with this method to help myself get a hang of managing data and getting insights from said data. (Completed September 14th, 2025). 
Phase 2: Complete the case study using all the data using SQL and visualising on Tableau. 
Phase 3: Compare the insights from Phases 1 and 2 to look at how using sample size data can affect results. 










CASE STUDY BACKGROUND
Cyclistic is bike-share company based in Chicago. The director of marketing believes that the company’s future success depends on maximizing the number of annual memberships. The marketing team has been tasked with understanding how casual riders and annual members differ in their use of the bike-shares and from these insights, will design a marketing strategy to convert casual riders into annual members. 
Scenario: I am a junior data analyst on the marketing team, and my specific task is to answer the question: “How do annual members and casual riders use Cyclistic bikes differently?”
Business Task: 
The business task is to decipher how Casual Riders and Annual Members use Cyclistic differently to provide the marketing team with information that will help drive their tactics. 
Data Sources used: The data used for this analysis project is found here: Cyclistic and the time period chosen was: August 2024 – July 2025 (12 months of Data). The data was made available by Motivate International Inc. under this license.  
Casual Riders: Customers who purchase single-ride or full-day passes
Annual Members: Customers who purchase annual memberships
Documentation of cleaning and data manipulation.
Phase 1 – Completing the case study using a sample data size. 
I downloaded 12 months of data from source and did a quick scan of the csv files; each file had at least 150,000 rows of data. As this was my first project, I had decided to use spreadsheets (Excel specifically) to ease me into data analysis. To get insights from the year, I needed to combine all twelve data files. I attempted this on Excel using Power Query but there were more rows than are possible to have in Excel. 
For each month’s file, I calculated the number of entries that would give me 99% confidence level and 1% margin of error. 

 
I then loaded each data set into R to extract the number of rows I needed from each file and extracted those files from R. 
install.packages("tidyverse")
library(tidyverse)
aug_2024 <- read.csv("C:\\Users\\lldos\\OneDrive\\Desktop\\Google Data Analytics Course\\Cyclistic Case Study\\Original Data\\202408-divvy-tripdata.csv", nrows = 16283)

I merged the files to get a full year’s view on excel using Power Query. 
Data Cleaning: 
-	I deleted the longitudes and latitudes columns as I did not require them for my analysis (I had already saved the original data files as is). 
-	I applied conditional formatting to all the cells to check for any blank cells and deleted those as well. 
-	I checked that the length of the ride_ids was consistent using the LEN() function. 

Analysis: 
I calculated the length of each ride (ride_length) and applied conditional formatting to check if there were any rides less than 1 minute as these could have been due to docking errors. I excluded these rows from the data for the analysis. 
I extracted the following information from the data for the analysis:
Column	Calculation / Formula
Ride_duration	started_at – ended_at (formatted as HH:MM:SS)
Day_of_week	=TEXT(“started_at”, "dddd")
Month_of_year	=TEXT(“started_at”, "mmmm")

To determine the season, I assumed the following:
Winter	Spring	Summer	Fall
December to February	March to May	June to August	September to November

The formula: = IF(OR(MONTH(“STARTED_AT”)=12, MONTH(“STARTED_AT”)<=2), "Winter", IF(AND(MONTH(“STARTED_AT”)>=3, MONTH(“STARTED_AT”)<=5), "Spring", IF(AND(MONTH(“STARTED_AT”)>=6, MONTH(“STARTED_AT”)<=8), "Summer", IF(AND(MONTH(“STARTED_AT”)>=9, MONTH(“STARTED_AT”)<=11), "Fall"))))








Visualisation
I compared the average ride durations for casual riders and members on a daily, monthly, and seasonal basis to understand the differences between them. This was achieved using pivot tables and an interactive dashboard.

Ride Duration.
 
Figure 1: Average Daily Ride Duration
 
Figure 2: Average Monthly Ride Duration
 
Figure 3: Average Seasonal Ride Duration
Figures 1 and 2 show that casual riders have average ride durations that are longer than those of members, day to day and month to month. They also reveal that that the average durations for members are similar across the days and months, with a slight spike during summer months compared to the significant spike for casual riders during the same period (this can be more clearly seen in Figure 3). This could indicate an opportunity to push marketing to casual riders during the summer months. 

 
Figure 4: Number of Daily Rides
 
Figure 5: Number of Monthly Rides

 
Figure 6: Number of Seasonal Rides

Despite the longer rides by casual riders shown in Figures 1 – 3, Figures 4 – 6 reveal that there are more annual members taking rides than casual riders on a daily, monthly, and seasonal basis. 
 
Figure 7: Number of Rides by Type
Figure 7 shows that casual riders use the electric options more than members. There could be an opportunity to market around this observation. 

Recommendations
Following the analysis of the data from Cyclistic, I can make the following recommendations to the Marketing team to target casual riders:
1.	More promotion of annual membership during the weekends and from spring into summer months, as there are significantly more rides taken by casual riders during those periods. 
2.	Taking advantage of the longer riders by casual riders, a promotion including redeemable points based on how long a ride is can be introduced as part of the rewards of an getting annual membership. 
3.	A discount on annual membership that highlights the benefits of a one-time payment as opposed to several payments. 
4.	Highlighting the benefits of using Cyclistic: fitness, traffic avoidance, saving on fuel. 
An additional analytical recommendation is to make use of rider ids to further determine the behaviour of casual riders. This will help in more personalised promotion of annual membership based on the behaviour of each rider. 


Phase 2 – Completing the analysis using the full dataset; SQL and Tableau
Using SQL, I extracted the data I would need to run the same visualisations and in phase 1. All queries run are found here. 
Tableau Visualization found here. 
Comparison: 
 
  

 
 

Sources:
-	Cyclistic Data (August 2024 – July 2025): https://divvy-tripdata.s3.amazonaws.com/index.html
-	Data License Agreement: https://divvybikes.com/data-license-agreement



