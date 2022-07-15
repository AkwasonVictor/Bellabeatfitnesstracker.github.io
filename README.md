# akwasonvictor.github.io
Bellabeat-(FitBit fitness tracker)

About the Bellabeat
Bellabeat is a high-tech company that manufactures health-focused smart products that collects data on activity, sleep, stress, and reproductive health that empowers women with knowledge of their own health and habits. Since it was founded in 2013, Bellabeat has grown rapidly and quickly positioned itself as a tech-driven wellness company for women. By 2016, Bellabeat had opened offices around the world and launched multiple products such as their app called Bellabeat app, there smart bracelet called Leaf, their smart watch called Time and their smart water bottle called Spring. Bellabeat products became available through a growing number of online retailers in addition to their own e-commerce channel on their website.

Ask Phase
Business task: Focus on a Bellabeat product and analyze smart device usage data in order to gain insight into how people are already using their smart devices.
Stakeholders
Urška Sršen: Bellabeat’s cofounder and Chief Creative Officer
Sando Mur: Mathematician and Bellabeat’s cofounder; key member of the Bellabeat executive team.
Bellabeat marketing analytics team: A team (me included) of data analysts responsible for collecting, analyzing, and reporting data that helps guide Bellabeat’s marketing strategy.
Product Focus: 
•      Bellabeat app: The Bellabeat app provides users with health data related to their activity, sleep, stress, menstrual cycle, and mindfulness habits. This data can help users better understand their current habits and make healthy decisions. The Bellabeat app connects to their line of smart wellness products.
•      Leaf: Bellabeat’s classic wellness tracker can be worn as a bracelet, necklace, or clip. The Leaf tracker connects to the Bellabeat app to track activity, sleep, and stress.

Prepare Phase
Data Name: Fitbit Fitness Tracker Data
Data Source & licensing: CC0: Public Domain, dataset made available through Mobius (Kaggle data set).
Data integrity verification: The data was stored in Kaggle and it contains personal fitness tracker from thirty Fitbit users. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to explore users’ habits.
Data Problem: The data was bias. the data was selection bias. Due to it being a small set of data, the samples were not a representation of the overall population of women.

Process Phase
Tools
Excel/Google Sheets: Clean and organize data
SQL: Analyze Data
Tableau: Visualize Data

Data Cleaning Report:
Fix typos
Remove outliers
Format columns and Convert data values into consistent metrics
Inspect each data frame for missing values and blank spaces
Check and removing if there was any duplication of the data
 
Data Set Used:
Daily Activity
Steps per day
Hourly Calories Merged
Hourly Steps Merged
Sleep Day Merged
Daily calories

Analyze & Share Phase


--Number of Participants: 33

SELECT  
COUNT(DISTINCT Id) AS Individual_Id
FROM `capstone-project-355722.Bella_beat_fitness.daily_Activity`

--Total number of days to conduct the experiment: 31

SELECT Id,
COUNT(Id) AS Number_of_days
FROM `capstone-project-355722.Bella_beat_fitness.daily_Activity`
WHERE Id IS NOT NULL
GROUP BY Id
ORDER BY Number_of_days DESC

--User category by Number of days participants used the Fitbit device

SELECT Id,
COUNT(Id) AS Number_of_days_used,
CASE 
WHEN COUNT(Id) BETWEEN 28 AND 31 THEN 'High Level User'
WHEN COUNT(Id) BETWEEN 18 AND 27 THEN 'Mid Level User'
WHEN COUNT(Id) < 18 THEN 'Low Level User'
END AS User_category
FROM `capstone-project-355722.Bella_beat_fitness.daily_Activity`
GROUP BY Id
ORDER BY Number_of_days_used DESC

--Average number of steps per day

SELECT Id, AVG(StepTotal) AS Average_daily_steps
FROM `capstone-project-355722.Bella_beat_fitness.daily_steps`
WHERE Id IS NOT NULL
GROUP BY 1

--Average calories burnt per day

SELECT Id, AVG(Calories) AS average_calories_burnt_daily
FROM `capstone-project-355722.Bella_beat_fitness.daily_Calories`
WHERE Id IS NOT NULL
GROUP BY 1

--Average sleep duration 

SELECT Id, AVG(TotalMinutesAsleep) AS Average_sleep_duration
FROM `capstone-project-355722.Bella_beat_fitness.sleep_Day`
WHERE Id IS NOT NULL
GROUP BY 1
ORDER BY 2 DESC

-- correlation between steps taken and calories burned

SELECT Id, SUM(Calories) AS total_calories_burned, SUM(TotalSteps) AS total_steps_taken
FROM `capstone-project-355722.Bella_beat_fitness.daily_Activity`
WHERE Id IS NOT NULL
GROUP BY 1
ORDER BY 2 DESC, 3 DESC
LIMIT 5

 Visualization was done using Tableau: https://public.tableau.com/views/FitBitFitnessTracker/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link

Act Phase

Conclusion
The data that was provided was very health focus. There were 33 women who participated in this experiment. the activities, intensity, steps, calories and sleep data were all sufficient enough to draw a conclusion. By understanding the daily activities, sleep patterns, number of calories burnt I was able to recognized the trends and relationship between the data set.

Recommendation
Based on analysis of the fitbit Fitness tracker. It is possible to keep track of a person's routine, monitored daily activities, as well as persons vitals, this can be applied in, the bellabeat app and leaf products, to help Monitor and regulate users vitals and activities. a feature on the app can notify user if the average amount of steps wasn't taking or the daily average calories wasn't burnt. it can also suggest that the user take more rest. If the daily sedentary minutes isn't met. This can significantly boost user and product integration.
