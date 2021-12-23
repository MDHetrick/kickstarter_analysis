# Analysis of Kickstarter Campaigns

## Overview of Project

### Purpose
The client, Louise, has interest in theater kickstarters. She is primarily interested in play kickstarters and the success of these kickstarters as it relates to their goals and launch dates. She has some interest in musicals as well.
## Analysis and Challenges
First, I looked at the data in entirety to get a good overview of what data was contained in the dataset. To get a better sense of the extent of the data, I used filters to look at some of the different categories and what they contained. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I1.png)

I also did some sorting to see what the scope of the data was. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I2.png)

To be able to get a quick visual of the data outcomes, I applied conditional formatting, and was able to see the outcome at a glance.

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I3.png)

Another piece of analysis I did was to calculate the percentage funded. I used the goal and pledged columns to calculate what percent of the goal was funded. I incorporated this into the round function in order to get a whole number. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I4.png)

With this information, I used the value shading conditional formatting in order to quickly visualize which campaigns were close to reaching their goals and which campaigns did not yet reach their goals. When I initially applied the filters, all of my values except three were solid red. To understand why, I sorted the column in descending order, and I saw that there was one significant outlier. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I5.png)

To compensate for this outlier, I changed the maximum field from highest value to 90th percentile, which gave a better distribution of colors. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I6.png)

I then used the pledged and backers_count columns to calculate the average donation for each kickstarter. I used the round function to 2 decimal places to better represent the dollar amount. The =ROUND function worked well, however there were some cells with errors. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I7.png)

The cells with errors were those with zero pledges and zero backers, so for these cells, instead of an error message I wanted a 0. To incorporate this, I nested the round function within the IFERROR function with an error message of 0. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I8.png)

Another step I performed was to split the category and subcategory into separate columns in order to be able to sort it in a more granular fashion. I copied the category/subcategory column and pasted the contents into a new column. I then used the text to columns converter to convert the category and subcategory to two columns using “/” as the delimiter.

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I9.png)


![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I10.png)


From these two new columns, I created a pivot table, and looked at outcomes for the categories and the countries. 


![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I11.png)

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I12.png)


From this pivot table, I was able to insert a chart to visualize the data. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I13.png)

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I14.png)

To add additional detail to the data, I added subcategory to the pivot table 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I15.png)

I charted the subcategories on their own the same way, with parent category in filters instead of rows. This allowed me to look at the data in a little different way to better understand it.

I also did a data transformation to convert the timestamps to dates. I did this by using the following formula: =(((timestamp/60)/60)/24)+DATE(1970,1,1). With this data, I created another pivot table, and with the pivot table, I created a chart to visualize the trends.

The client, Louise, provided a list of five plays she viewed at the Edinburgh film festival and requested funding information for these specific plays. To pull this data from the main spreadsheet, I typed the list of these plays into a new sheet, and used the VLOOKUP function to pull the Blurb, Goal, and Pledged amounts into the new spreadsheet. 


![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I16.png)


![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I17.png)



I also wanted to do some statistical analyses of the funding pledges and goals for the US kickstarters about plays, so I created two new sheets. Using filters on the main kickstarter sheet, I filtered for the play subcategory, US country, and successful outcomes, and copied and pasted that data into a new sheet titled Successful US Kickstarters. I did the same for failed outcomes and pasted that data into a new sheet titled Failed US Kickstarters. With these two new sheets, I calculated mean, median, quartiles, and IQR of goal and pledged for successful and failed kickstarters. 


![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I19.png)


![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I20.png)

Louise also showed interest in a musical in Great Britain with an estimated budget of £4,000. So I filtered the main dataset to show the country of GB, and the subcategory of musicals. I created a box plot of this data to visualize where Louise’s budget falls. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I21.png)


![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/Great_Britain_Musical.png)


### Analysis of Outcomes Based on Launch Date

Once I evaluated the kickstarter funding data, I moved on to evaluating the outcomes of different kickstarters. First, I evaluated outcomes based on launch date. To do this, I created a new column, and used the YEAR function to pull the year out of the date created conversion column. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I22.png)

I then created a new pivot table with filters of parent category & years, outcomes in the columns, date created conversion (month) in rows, and count of outcomes in values. Using this pivot table, I filtered by theater to show the data that the client is interested in. I visualized this data by creating a line chart.

![Image](https://github.com/MDHetrick/kickstarter_analysis/blob/main/Resources/Theater_Outcomes_vs_Launch.png)


### Analysis of Outcomes Based on Goals

To evaluate the kickstarter outcomes based on their goals, I created a new sheet and created several categories ranging from <1000 to >50000. Using the COUNTIFS function, I populated the number successful, number failed, and number canceled for plays for each of the categories. 

![Image](https://raw.githubusercontent.com/MDHetrick/kickstarter_analysis/main/M1I23.png)

While the highest category was supposed to be greater than 50000, I followed the pattern of the previous categories and included 50000 in the counts of this row and renamed greater than to greater than or equal to. I summed the total projects in each goal category and calculated the percentage successful, failed, and canceled. Using the percentages, I created a line chart to quickly visualize the data.

![Image](https://github.com/MDHetrick/kickstarter_analysis/blob/main/Resources/Outcomes_vs_Goals.png)

### Challenges and Difficulties Encountered

Occasionally excel would freeze and crash, especially when I had many other excel files open at the same time. I learned to save more frequently. I also learned to close everything I wasn’t working on and just have one file open at a time. This has turned out to be a good practice for me to maintain focus as well.

An additional challenge was that initially when I used the VLOOKUP function, the table array was not fixed, so when I dragged the formulas across the rows, I had to edit this piece as well. However, I learned to use the F4 key to fix the selection, or just rows or columns, which was very helpful. I realized this in deliverable 2 while using the countifs function

When I filtered the main kickstarter spreadsheet, I knew that when I copied the data, it copied hidden and visible rows. Initially I tried to find a paste special option that only pasted the visible rows, but after doing a web search, I was able to use the F5 key to select only the visible rows.

In challenge deliverable 1, I had a little trouble figuring out how to show just months in the rows, but once I realized that the table automatically created several categories,
I was able to remove the ones I was not interested it.
Another point of confusion for me was within the submission. The submission instructions direct me to delete “Successful US Kickstarters” and “Failed US Kickstarters” sheets. However I used these worksheets to populate the descriptive statistics sheet, so deleting the successful and failed sheets gave me invalid cell reference errors.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

I can conclude that the middle of the year is likely the optimal time to launch a theater kickstarter. I can also conclude that theater kickstarters that were launched in the winter months were less successful than those launched in May.

- What can you conclude about the Outcomes based on Goals?

The play kickstarters with goals greater than or equal to 450000 were far more likely to fail than succeed. The play kickstarters with lower goals (15000) succeeded more than those with goals between 15000 and 30000.

- What are some limitations of this dataset?

As the goal increases, the number of play kickstarters decreases until a goal of 30000. At this point, the number of kickstarters is very small, which makes it challenging to know if the percentages in this analysis are truly representative of the population. For example, based on this data, it might be recommended to set a higher goal (35000 instead of 30000) because 27% of kickstarters with goals between 30,000 and 34,999 were successful, while 67% of kickstarters with goals between 35,000 and 39,999 were successful. However these categories had total numbers of 11 and 6, respectively.

- What are some other possible tables and/or graphs that we could create?

I would suggest to create tables to look at the number of backers as it relates to goals, outcomes, and launch date. 
