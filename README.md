## Overview

### Purpose
The purpose of this analysis is to compare the outcomes of kickstarters that are plays based on their launch date, to kickstarters that are plays based on their goal amount.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
1. I performed my analysis of Outcomes based on Launch Date by first creating a pivot table of the data in the Kickstarter worksheet. 
2. I filtered the data by parent category and by years because I want to see how specifically the 'theater' category did over a period of time. I used the 'outcomes' data for my columns, and 'Date Created Conversion' as data for my rows, and populated the intersection of this data with the outcome values. 
3. This still gives me data for all parent categories, so I needed to filter Parent Categories on 'theater'.
4. Per the Challenge instructions, I needed to sort the outcomes of the pivot table in descending order as well.
5. I was then able to create a line chart of the pivot table data to represent the Count of Theater Outcomes Based on the Launch Month.

![Count of Theater Outcomes based on Launch Month Line Chart](/resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals
1. I performed my analysis of Outcomes (of Plays) based on Monetary Goal of the Kickstarter by creating a table of data derived from the 'Kickstarter' worksheet.
    - This table needed to include:
      - the number of successful/failed/canceled outcomes (using the `COUNTIF` function),
      - the sum of the total projects based on their outcomes (using the `SUM` function),
      - and the percentages of successful/failed/canceled outcomes out of the Total Projects (by dividing the number of successful/failed/canceled by their total).
2. To create the `COUNTIF` function for _number of successes_ for _goals <$1,000_, I used this function: `=COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays",Kickstarter!$D:$D,"<1000")`
    -  **criteria_range1** is `Kickstarter!$F:$F`, which selects all outcomes in Column F. **critera1** is "successful", which counts only the cells which contain the value "successful"
    -  **critera_range2** is `Kickstarter!$R:$R`, which selects all subcategories in Column R. **critera2** is "plays" because we only want to count the cells which contain the value "plays"
    -  **criteria_range3** is `Kickstarter!$D:$D`, which selects all monetary value goals in Column D. **criteria3** is "<1000" because we only want to count the cells which have a value of less than $1,000.
3. I can copy and paste this formula for the rest of the goal categories. For all goals _greater than or equal to $1,000_, I needed to change **critera3** and create a **criteria_range4** and **criteria4**. **critera3** would need to become the new lower bound for the goal category, **critera_range4** would be the same as **critera_range3**. **critera4** would need to be the upper bound of the goal category.
4. I was able to copy the forumlas from `B2:B12` and paste them into `C2:C12` and `D2:D12`. I used the Find & Replace function of Excel to find all instances of "successful" and replaced them with "failed" for Column C, and "canceled" for Column D.
5. I used the `SUM` function and the range `B2:D2` to find the Total Projects with goals <$1,000. Because the range was not fixed, I could drag this formula down and the sums would populate for all the monetary goal ranges.
6.  To calculate the Percentages for "successful" outcomes, I divided the number of "successful" outcomes by the sum of Total Projects. Because this range is not fixed, I could then drag this formula down to populate the percentages of "successful" outcomes for the rest of the monetary goal ranges. I could repeat this process for "failed" outcomes and for "canceled" outcomes.

![Count of Outcomes based on Monetary Goals, Line Chart](/resources/Outcomes_vs_Goals.png)

### Challenges and Difficulties Encountered
A challenge that I came across occurred during my analysis of Theater Outcomes by Launch Date. When I was creating the pivot table for the data, some of my row labels for the Date Created Conversion included data that did not fit under any of the month filters - I have a (blank) category to filter by which I did not know where it came from, as all of the dates in my data table from the Kickstarter worksheet have values for them. Thankfully I was able to just filter them out without affecting my data and analysis any meaningful way.

I've also found that between some of my classmates, there was a discrepancy between my total number of plays for the Outcomes Based on Goals and their total. I was not accounting for 1 play, and I found this out from Dennis Kreger and Jennifer Reyes. I went back and found that I had been calculating my Goal filters incorrectly! I For example, I used `=COUNTIFS(...">=1000",..."<4999")` instead of `=COUNTIFS(...">=1000",..."<5000")`. I was going to the wrong upper limit on all of them. This has since been fixed and my total number of plays is correct.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
	- I can conclude that the count of Theater Kickstarters that were successful were the highest with a launch date in May. I can also conclude that the count of Theater Kickstarters that failed were the highest if they launched in May, June, July, or October.

- What can you conclude about the Outcomes based on Goals?
	- I can conclude that the highest percentage of successful plays had a goal of <$1,000.
- What are some limitations of this dataset?
	- Some limitations of the data set are that we aren't able to explain why Theater Kickstarters launched during the month of May were so successful, we only know that that month had the highest number of successes. Similarly, we are also not able to explain why Theater Kickstarters launched during that month also had the highest percentage of failure. This is because there is not metric or data to determine how popular the individual plays were.
	- Dennis Kreger also pointed out that all of the data for the canceled plays show a monetary value of $0, but had we known what the Kickstarter goals for those plays were, we could have calculated a trend in the data and made an analysis based on them. It may have been helpful in determining why those plays were canceled, and could have helped **Louise**. Not only this, but he discovered that there is a discrepancy between the number of plays from the Outcomes Based on Goals worksheet and the total number of plays that there should be, minus the plays with a "live" outcome.

- What are some other possible tables and/or graphs that we could create?
	- To help **Louise**, we could create a table that measures the percentage of successful/failed/canceled plays based on data from the Date Created Conversion date and Date Ended Conversion data. This would show the success/failure/cancel rate of plays based on how long they were available for attending to the public.
