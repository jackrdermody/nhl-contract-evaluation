# NHL Player Contract Evaluation
## Introduction
### School: Martha and Spencer Love School of Business, Elon University
### Course: Data Wrangling
### For this assignment we were asked to come up with our own proposal for a data project where we would be collecting and merging data from multiple sources. The data you collect should allow your proposal to be explored sufficiently. Due to my love of hockey (go Bruins), my proposal was the following:
### *How does an NHL general manager assess the market value for a player during contract negotiations?*
### The National Hockey League is an incredibly profitable organization with teams generating revenues between $120 and $281 million dollars over the 2023-24 season. (Visual Capitalist, 2024) The top grossing teams of the league are either competitive, longstanding/historic teams, in lucrative markets, or are a combination of these characteristics.  With competitiveness being the only factor that teams have somewhat direct control over, fielding a roster that can win games is of the utmost importance. But since there is a hard salary cap in the NHL, general managers must allocate the salary cap effectively. Games can be won and lost at the negotiation table; a star player being on a below market value contract can allow management to put together a better supporting cast, but not wanting to budge on a number can risk making the player walk. There is a plethora of factors to consider when evaluating a player, such as age, contract eligibility, position, on-ice production and more. With advanced statistics and analytics growing rapidly leaguewide, how effective can a model be at predicting whether a contract is an overpay or not? (The Athletic, 2022)

## The Data
### To start an analysis of NHL players, the first step is to gather their on-ice statistics. Evolving Hockey is an advanced NHL statistic website which has a model for GAR (games above replacement), a metric that quantifies, in goals, how productive a player is. They also have charts containing basic player statistics.  Steps for accessing the data are below:
1.	**Go to the Evolving Hockey website.  (https://evolving-hockey.com)**
2.	**Become a subscriber to get full access to all their charts. (Standard - $4.99/mo: gives access to standard charts.  Pro - $9.99/mo: gives access to all charts.)**
3.	**Download standard skater data.**
   
   Using the banner at the top of the page, navigate to standard skater data.
-  Standard -> Skater Tables

Change search parameters to show 2023-24 skater data.
-	 Season(s): 2023-2024
-  Grouping: Season

Scroll to bottom of the page and click download in the bottom left.

4.	**Download advanced skater data.**

   Using the banner at the top of the page, navigate to GAR skater data.
-  GAR | xGAR -> GAR Skater Tables

Change search parameters to show 2023-24 skater data.
-  Season(s): 2023-2024
-  Grouping: Season
-  Add Info: Yes

Scroll to bottom of the page and click download in the bottom left.
#### Using python, I then merged the two datasets so I have a csv file with the full skating data of each NHL player from the 23-24 season. 

### Evolving Hockey is a statistical database meant for people to be able to explore their advanced models.  The focus of their work is to enhance the accuracy of these models and better quantify each player’s on-ice contribution and effectiveness.  Using this data to then evaluate the contracts to which the players are signed is simply not the focus of the site, therefore, they do not collect contract information. There are a handful of sites which compile contract information for NHL teams and players. PuckPedia, one of the more well-known sites, has an intuitive interface and player search dashboard. To retrieve this information, I created a web scraper on python. The steps to do so are listed below:

1.	**Import necessary packages.**
2.	**Obtain the page source.**
3.	**Create the web scraper.**
-	Create an empty list and start driver.
-	Iterate through the rows on the first page of the site and store the data.
-	Click the next page button and repeat the previous step.
4.	**Export the resulting data frame to a csv file.** 

## Merging and Preparation
### I started by editing the names in the contract data file, ensuring they all match with the names from the skating data, before altering the names and data types of each column as needed. Then, after merging the skating data with the contract data, I created my two new columns, Surplus Value and Evaluation, which will be used to analyze the value of each player's contract. 
### By scaling both the players' cap hits and GAR values, it allows me to compare the two numbers. 
### Surplus Value is calculated by subtracting scaled cap hit from scaled GAR. A positive surplus value indicates the player produces more value than he's being paid. A negative surplus value indicates the player produces less value than he's being paid. 
### Evaluation is a binary variable that looks at Surplus Value. If a player has 1 in the Evaluation column, his Surplus Value is Positive. If a player has 0 in the Evaluation column, his Surplus Value is negative. 

#### I have provided the files necessary to run my code for yourself. Download the python workbook (.ipynb file) and both csv files, then make sure you have the necessary packages installed on your device. 


