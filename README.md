# Call Center Report

Description 

## Table of Content

-[Project Overview](project-overview)
- [Data Source](data-source)
- [Tools](tools)
- [Data Cleaning & Transformation](data-cleanin-and-transformation)
- [Exploratory Data Analysis](exploratory-data-analysis)
- [Findings](findings)
- [Recommendation](recomendations)
- [Refrence](refrence)

  ## Project Overview

  This project analyses a Call Center's record for October 2020. It gives insight into the KPI's neccessary to drive growth and relevant decision making.

![CALL CENTER DASHBOARD_page-0001](https://github.com/user-attachments/assets/433ad04e-b574-44eb-a533-5a988c13b185)

## Data Source 

The primary source of the data is "call-center.csv" file. This file contains the calls received everyday in the month of October 2020

## Tools

- Excel - Data Cleaning and Dashboard
- SQL Workbench- Data Analysis

## Data Cleaning & Transformation

In order to prepare the data, I did the following;
- Data loading & inspection
- Handling missing values
- Data cleaning & analysis

  ## Exploratoty Data Analysis

  - what is the total number of calls for the month ?
  - what is the average satisfactory calls ?
  - what is the average call duration in minutes ?
  - what is the call trend for the month under review ?
  - what is the call channel by total call center ?
  - how many call centers by city ?
  - what are the highest reasons for customer calls ?
  - what is the time frame for customers call ?

total calls
~~~sql
SELECT COUNT(`customer id`) As Total_Calls FROM practice_db.call_center;
~~~

avg csat score
~~~sql
SELECT AVG(`csat_score`) As Avg_csat_score FROM practice_db.call_center;
~~~

avg call duration
~~~sql
SELECT AVG(`call duration in minutes`) As Avg_call_duration FROM practice_db.call_center;
~~~

call trend
~~~sql
SELECT call timestamp, COUNT(`call timestamp`) As Call_Trend  FROM practice_db.call_center
GROUP BY call_timestamp
ORDER BY call_timestamp ASC;
~~~

call trend by city
~~~sql
SELECT city, COUNT(`call_center`) As Call_Trend_by_city  FROM practice_db.call_center
GROUP BY city
ORDER BY city ASC;
~~~

call trend by channel
~~~sql
SELECT channel, COUNT(`call_center`) As Call_Trend_by_channel  FROM practice_db.call_center
GROUP BY channel;
~~~

call trend by state
~~~sql
SELECT state, COUNT(`call_center`) As Call_Trend_by_state  FROM practice_db.call_center
GROUP BY state
ORDER BY Call_Trend_By_State ASC;
~~~

reasons for calling
~~~sql
SELECT reason, COUNT(`call_center`) As Reason_For_Calling  FROM practice_db.call_center
GROUP BY reason;
~~~

response time
~~~sql
SELECT response_time, COUNT(`call_center`) As Response_time  FROM practice_db.call_center
GROUP BY response_time;
~~~

sentiment
~~~sql
SELECT sentiment, COUNT(`call_center`) As sentiment  FROM practice_db.call_center
GROUP BY sentiment;
~~~



 ## Findings

 After a careful analysis, I found that;

 - the most frequently used chanel was via calls, while the least used chanel was via the web
 - the most frequent reason for calling was billing questions
 - the averrage call duration was 25 minutes and this fell within the stipulated SLA

   ## Recomendations

   At the end of my analysis, the following are my recomendations;

   - since most customers prefered using call channels, more call center agents should be employed to further improve the response time that falls within the stipulsted SLA, or simply launch a campaign to promote other chanels
   - an average call duration of 25 minutes is rather on the high side, and call center agents should be further trained on hoe to resolve callers issues in the quickest possible time.
   - with the most frequent reason of calling being billing questions, the management should launch a customer education campaingn o questions concerning billing. 
