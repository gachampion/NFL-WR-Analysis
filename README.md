# NFL WR Analysis
Final Project for Data Engineering Course from Masters of Science in Analytics Program 

## Executive Summary:
Each year, hundreds of new players enter the NFL draft with the hopes of becoming the next league MVP.  Because college players entering the draft could have unique backgrounds in terms of team, conference, schedule, etc., the NFL combine is held each spring before the draft to standardize metrics related to player athletic ability. This project will analyze these metrics historically to gauge the accuracy of combine results & draft position on the impact the players have made in the NFL. 

## Business Case:
A lot of pressure rides on NFL team owners & coaches to select the right player at the right time in the draft.  Therefore, they need to understand how performance in the NFL combine relates to the performance of the player in future NFL games.  We believe that this could be accomplished by comparing NFL combine statistics (height, weight, hand size, 40 yard dash, vertical jump, etc), draft position, to actual NFL career statistics (receptions, receiving yards, TDs, etc) of certain player positions to help understand the relevant indicators of top-tier, NFL talent.  

## Data Source:
https://www.kaggle.com/toddsteussie/nfl-play-statistics-dataset-2004-to-present 

## Data Model:

![image](https://user-images.githubusercontent.com/80867370/112909092-5f2a7e00-90b6-11eb-9b99-db6a95ee6db1.png)


## Dashboards (from Tableau):

![image](https://user-images.githubusercontent.com/80867370/112909126-749fa800-90b6-11eb-9efb-aab794c0fe70.png)

![image](https://user-images.githubusercontent.com/80867370/112909136-79645c00-90b6-11eb-95f9-5a500ab0ce21.png)

![image](https://user-images.githubusercontent.com/80867370/112909148-7cf7e300-90b6-11eb-8901-cc1793530cb1.png)

![image](https://user-images.githubusercontent.com/80867370/112909160-808b6a00-90b6-11eb-9119-8100d3d92a26.png)

![image](https://user-images.githubusercontent.com/80867370/112909171-84b78780-90b6-11eb-8263-f966f50d4db6.png)

![image](https://user-images.githubusercontent.com/80867370/112909183-897c3b80-90b6-11eb-9d1a-950976da8ae9.png)


## Methodology & Tools Used:
●	Python: used to combine various datasets, aggregate play-by-play data into season data, calculate our custom touchdown field, and remove data that we do not need for our analysis.  
●	MySQL: We used MySQL to create tables, import data, and add foreign keys. We split table and foreign key creation in order to handle importing errors. Additionally, while we manipulated some of the data in python, we decided to import the data via a SQL script to make the process more streamlined. Once we created the database, we cleaned the data further by creating scripts to drop an additional 150 or so players that had not participated in the draft or combine and therefore lied outside the purview of our analysis.  
●	Tableau: Used to analyze & visualize interesting findings


## Data Cleaning & Profiling:


Data Profiling:  
●	As the game play data only goes back until 2004, we will remove combine & draft data for players prior to 2004  ●	Since player statistics are only counted for the regular season, we will remove game play data from pre-season & playoffs  
●	Remove game play data for players who did not participate in the combine and/or get drafted  
●	Remove player data for players who have not participated in at least one receiving play  
●	Aggregated data from play by play level to populate the stats table  
●	There was no column for touchdowns so had to calculate manually based off values in other columns  
●	As we were combining our various datasets in Python, we discovered there was an issue with missing data for some plays/games for a few seasons.  At first, we tried to link other sources of data for these missing games; however, due to the time constraints we had with the project, we realized it would not be feasible to start from scratch. At this point, we decided to pivot our project a bit to include only statistics for rookie season (rather than entire career) and only analyze data for years in which we had complete data (2004-2007, 2010, 2014, 2017, 2019). So, we had to further clean our data to remove any combine/player/draft data for seasons not included.  
●	Assumption made about data was that if a player did not participate in the combine and/or get drafted, we are assuming they didn’t make a large enough impact in the NFL to analyze their game play stats

## Recommendations & Lessons Learned:  
●	Do a thorough data check before using the data.  We did some spot checks, but until we aggregated all of the files together, we were unable to see there was missing data.  Had we aggregated the datasets together earlier, we could have caught it and had more time to fix any missing data.  
●	Duplicated data can indicate missing data.  
●	If using Kaggle, look at the number of downloads/contributors.  Ours didn’t have that many and now looking back, we realize that is probably due to the complexity of the files & the missing play data.  
●	In an ideal world, we would have loved to include data for all seasons the wide receivers played.  This would have allowed us to analyze more of an impact the players had on the NFL, as well as do comparison for how rookie performance may predict performance in an entire career. This is the reason why we had the players, stats, and teams tables separate.  If all would have gone according to plan, each player would have had a unique season-year ID.  As a player may get traded over the course of their career, that is why we kept the teams table separate so that we could see what team they were on each year.  After discovering the issue with our missing data, unfortunately this was no longer possible using the available data we had.  Due to the time constraints of the project we kept our model the same with the separated out tables.  
●	We also ran into a few challenges with the creation of our database. In the combine table, there are quite a few variables that can be null. We decided to label these attributes this way because deleting rows with missing values from this table would have resulted in a fairly large loss of observations. We view this as an area of improvement to the database in the future. 



