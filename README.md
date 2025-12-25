# Google-Data-Analytics-Course---Cyclistic-Case-Study

Cyclistic Bike-Share Case Study

Google Data Analytics Capstone Project

📌 Introduction

This project is the final capstone of the Google Data Analytics Professional Certificate (Coursera) and represents my first end-to-end data analytics case study using real-world data.

As my first full project, the initial challenge was understanding how to approach a large dataset, structure the analysis, and translate business questions into actionable insights. To address this, I intentionally broke the project into phases to build confidence and technical depth over time.

Project Phases

Phase 1: Sample-based analysis using spreadsheets and R
(Completed: September 14, 2025)

Phase 2: Full dataset analysis using SQL and Tableau
(Completed: December 12, 2025)

Phase 3: Compare insights from sample vs full dataset to assess impact

🏢 Case Study Background

Cyclistic is a bike-share company based in Chicago. The company’s Director of Marketing believes that increasing annual memberships is key to long-term growth.

Business Task

How do annual members and casual riders use Cyclistic bikes differently?

The goal is to understand usage differences so the marketing team can design targeted strategies to convert casual riders into annual members.

👤 Rider Types

Casual Riders: Single-ride or full-day pass users

Annual Members: Subscription-based riders

📊 Data Sources

Dataset: Cyclistic (Divvy) trip data

Period: August 2024 – July 2025 (12 months)

Source: Motivate International Inc.

License:
https://divvybikes.com/data-license-agreement

🧹 Data Cleaning & Preparation
Phase 1 — Sample-Based Analysis

Due to Excel’s row limitations, a statistically representative sample was created:

99% confidence level

1% margin of error

Sampling performed using R

Example R code used:

install.packages("tidyverse")
library(tidyverse)

aug_2024 <- read.csv(
  "202408-divvy-tripdata.csv",
  nrows = 16283
)

Cleaning Steps

Removed unused latitude/longitude fields

Checked for null values and removed invalid rows

Verified ride_id length consistency

Removed rides shorter than 1 minute (likely docking errors)

Feature Engineering
Feature	Method
Ride Duration	ended_at - started_at
Day of Week	Extracted from started_at
Month	Extracted from started_at
Season	Month-based classification

Season Definition

Season	Months
Winter	Dec – Feb
Spring	Mar – May
Summer	Jun – Aug
Fall	Sep – Nov
📈 Analysis & Visualization (Phase 1)

Using Excel pivot tables and dashboards, I compared casual riders vs members across:

Daily usage

Monthly trends

Seasonal patterns

Ride duration

Ride counts

Bike type usage

Key Findings

Casual riders consistently take longer rides

Annual members take more rides overall

Casual riders show strong seasonal spikes in summer

Casual riders use electric bikes more frequently

📌 Recommendations

Based on the findings, I recommend:

Promote annual memberships during weekends and summer months

Introduce ride-duration-based rewards to appeal to casual riders

Offer annual membership discounts highlighting long-term savings

Emphasize benefits like fitness, traffic avoidance, and cost savings

(Future) Use rider-level data for personalized marketing campaigns

🧠 Phase 2 — Full Dataset Analysis (SQL & Tableau)

In Phase 2, I re-ran the analysis using:

SQL for data extraction and aggregation

Tableau for interactive dashboards

Deliverables

SQL queries used for analysis

Tableau dashboards showing trends across:

Ride duration

Ride volume

Rider type behavior

Seasonal patterns

🔗 Tableau Dashboard: (insert your Tableau Public link here)
📄 SQL Queries: (link to SQL file in repo)

🔍 Phase 3 — Comparison

Comparing sample-based insights with full-dataset results revealed:

Overall trends were consistent

Sample analysis slightly exaggerated seasonal effects

Full dataset provided more stability and confidence

🛠 Tools Used

SQL (SQLite / MySQL)

R

Excel

Tableau

GitHub

📂 Repository Structure
├── data/
│   └── cleaned_datasets/
├── sql/
│   └── cyclistic_queries.sql
├── tableau/
│   └── dashboard_link.txt
├── README.md

📚 Sources

Cyclistic Data: https://divvy-tripdata.s3.amazonaws.com/index.html

Data License: https://divvybikes.com/data-license-agreement

✨ Final Notes

This project represents my growth from beginner to confident junior data analyst, combining data cleaning, SQL querying, visualization, and business storytelling. It also highlights the importance of choosing appropriate tools for dataset scale.
This project was the last course in the Google Data Analytics course on Coursera and provided the opportunity to make use of the knowledge gained and practice the new skills acquired on real data. 

As my first data analysis project, it was a bit overwhelming at first as I did not really know where to start; I kept on reading the document over and over again, taking notes, having an idea of the information I needed to answer the business task but was a bit blocked on how to begin to tackle the large dataset I had to work with. 

My intentions were:

**Phase 1:** Complete the case study using a sample data size – I started with this method to help myself get a hang of managing data and getting insights from said data. (Completed September 14th, 2025). 

**Phase 2:** Complete the case study using all the data using SQL and visualising on Tableau (Completed December 12th, 2025). 

**Phase 3:** Compare the insights from Phases 1 and 2 to look at how using sample size data can affect results. 


**CASE STUDY BACKGROUND**
Cyclistic is bike-share company based in Chicago. The director of marketing believes that the company’s future success depends on maximizing the number of annual memberships. The marketing team has been tasked with understanding how casual riders and annual members differ in their use of the bike-shares and from these insights, will design a marketing strategy to convert casual riders into annual members. 
Scenario: I am a junior data analyst on the marketing team, and my specific task is to answer the question: “How do annual members and casual riders use Cyclistic bikes differently?”

**Business Task:**
The business task is to decipher how Casual Riders and Annual Members use Cyclistic differently to provide the marketing team with information that will help drive their tactics. 
Data Sources used: The data used for this analysis project is found here: Cyclistic and the time period chosen was: August 2024 – July 2025 (12 months of Data). The data was made available by Motivate International Inc. under this license.  

**Casual Riders:** Customers who purchase single-ride or full-day passes

**Annual Members:** Customers who purchase annual memberships

**Phase 1** – Completing the case study using a sample data size. 
I downloaded 12 months of data from source and did a quick scan of the csv files; each file had at least 150,000 rows of data. As this was my first project, I had decided to use spreadsheets (Excel specifically) to ease me into data analysis. To get insights from the year, I needed to combine all twelve data files. I attempted this on Excel using Power Query but there were more rows than are possible to have in Excel. 
For each month’s file, I calculated the number of entries that would give me 99% confidence level and 1% margin of error. 


