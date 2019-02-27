Sports Analytics Hackathon

This hackathon is about predicting the following results of the upcoming cricket series between India and Australia, March 2019.

Winner of the series.
Series output.
Highest run scorer.
Highest wicket-taker.
Maximum sixes.
Maximum fours.

Data Selection:

We have selected 3 types of data:
1) Match Results
    - Match results of all the ODI matches played by India within India in last 10 years.
	- Match results of last series played between India and Australia in Australia.

2) Batting Statistics
	- Batting statistics of all Indian and Australian players for all the matches played within last one year duration.
	
3) Bowling Statistics
	- Bowling statistics of all Indian and Australian players for all the matches played within last one year duration.


Data Cleaning:

1) Match Results:
	- Since this data contains the results of all the matches played between India and other teams in last 10 years, we have only selected the results of matches played with Australia.
	- Some of the matches were abandoned due to rain or some other factors, those rows have been filtered out from the dataset.
	  (As the weather report does not forecast any rains during the upcoming series.)
	- Converted 'Start Date' column from object type to datetime type. 
	  Later a new column 'Year' was derived from 'Start Date' column which was used to group the matches year wise/series wise.
	  
2) Batting Statistics:
	- In this data, 'Highest Score' column contains some of the scores in X* format (i.e. batsman was not out in that particular match)
      we removed that * from data and converted it to numeric type.
	- For some of the batsman, batting average was not provided, '-' was entered in the columns.
	  For such entries we imputed the columns with 0.
	  
3) Bowling Statistics:	  
	- Following columns were changed to numeric types - 'Inns', 'Overs', 'Mdns', 'Runs', 'Wkts', 'Ave', 'Econ', 'SR', '4', '5'.
	- NaN values were dropped.
	
Data Analysis:
1) Match Results:
	- To find out the series winner, we plotted the charts of number of matches won by each team
		- in last 10 years within India.
		- in the last series between India and Australia played in Australia.
	  Both the charts displayed India with most number of wins, which could be inferred as - India has a good past record against Australia in India and current form of India is also good.
	  Based on these anslysis we concluded India will win this series.
	  
	- Since, we had formatted the data in series wise format, we picked the match results of last two series between India and Australia one played in India and other in Australia.
		-  We have observed that in last two series performance of India was great losing only one match per series.
		-  Based on this we concluded that in this series also, out of the 5 matches India will lose only one match winning the series 4-1.
	
2) 	Batting & Bowling Statistics:
	- Sorting this data in descending order of 'Runs', 'Wkt' would have directly given the highest run scorer and highest wicket-taker.
	  but total runs scored and total wickets taken depends on the number of the matches played. 
	  This would not have given us the fair idea who will score highest runs and pick highest wickets in upcoming series.
	  
	  So to get the more accurate predictions, we picked few variables on wchich highest runs and wickets by a players could depend.
	  For e.g. Highest runs by a player could depend upon -  'HS', 'Ave', 'SR', '100', '50', '4s', '6s'
	  Similarly highest wickets by a player could depend upon - 'Mdns', 'Wkts', 'Ave', 'Econ'
	  
	  Plotting a correlation matrix between these variables showed that some of these variables are highly correlated with each other.
	  So we applied PCA of them:
		- Removed the multicollinearity between the variables.
		- Reduced the number of variables.
	  With less number of variables, we could predict - Rohit Sharma as highest run scorer of the series and Jasprit Bumrah as highest wicket-taker of the series.
	  
	- Scoring fours and sixes depends on the technical skills of a batsman, 
	  i.e., there are some batsmen who play technical shots and go for scoring boundaries, however, there are few batsmen who like to hit big shots and clear the boundaries from the top.
	  
	  So for predicting maximum sixes and fours, from the past data we selected the players based on the number of sixes and fours they have scored.
	  Based on this we predicted Shikhar Dhawan will hit maximum number of 4s and Rohit Sharma will hit highest number of 6s in this series.
	  
Final Prediction:

Winner of the series  -	India
Series output         -	4-1
Highest run scorer    -	Rohit Sharma
Highest wicket-taker  -	Jasprit Bumrah
Maximum sixes         -	Rohit Sharma
Maximum fours         -	Shikhar Dhawan
