# SpeedDating

Project 1 - Group 3:  Analysis of SpeedDating Data


# Question 1: Of the total participants, how did matched and unmatched participants rate themselves and their partners in each of the five surveyed attributes: attractiveness, sincerity, intelligence, fun, and ambition?
- Matched participants rated partners high, as expected. Favorably across all attributes but particularly in attractiveness
- Unmatched participants rated themselves higher, most notably in intelligence
- Matched and unmatched participants rated themselves similarly across all attributes

## Analysis for people who matched and their perceptions of the five qualities
Created a dataset that included only the matched participants:
![image](https://user-images.githubusercontent.com/110507463/201763663-0d3bcfb5-e78e-4680-b063-044b37e7d5c8.png)

Isolating and creating a dataframe to find the mean for each rating a matched participant gave themselves and their partner. Then creating subplots to feed the data into comparable histograms with shared axes. Repeated this process for all attributes of matched participants:
![image](https://user-images.githubusercontent.com/110507463/201764137-9d6126c2-b947-4091-932d-78a88c88c954.png)

## Analysis for people who did not matched and their perceptions of the five qualities
Created a dataset that only included the unmatched participants:
![image](https://user-images.githubusercontent.com/110507463/201764403-605f5e10-5494-40d0-a843-e6a219a16f03.png)

Isolating and creating a dataframe to find the mean for each rating an unmatched participant gave themselves and their partner. Then creating subplots to feed the data into comparable histograms with shared axes. Repeated this process for all attributes of unmatched participants:
![image](https://user-images.githubusercontent.com/110507463/201764485-df91924f-beae-4e97-9d72-c6f323bf44c4.png)

# Question 2: Of the total participants how do men and women differ in how they rate the opposite sex and are there differences pre-speed-dating and post-speed-dating?

First, we create a dataframe for pre-speed-dating attribute ratings with rows for both genders. Then, using seaborn and iplot, generate a bar chart where columns for men and women are grouped above the appropriate attribute for the best comparison.
![image](https://user-images.githubusercontent.com/111237645/201791656-7813799a-fbab-45a5-87e0-292f3addd43d.png)
![image](https://user-images.githubusercontent.com/111237645/201791940-c68b9532-9403-4a3a-90d4-5cc0ee23fdd0.png)
Pre-speed-dating Men value attractiveness above all other traits while Women value Intelligence the most. Both men and women value ambition the least.

The method was then duplicated for ratings for what participants estimated the opposite sex would rate desired attributes as well as their post-spped-dating ratings to see if there were any changes from pre to post.
![image](https://user-images.githubusercontent.com/111237645/201792321-9dc5a85f-cd7c-4ab9-8c1a-60c8c7f16b83.png)
![image](https://user-images.githubusercontent.com/111237645/201792345-0edb4347-dd60-4b46-8373-080a43c279d1.png)
Women think men value attractiveness above all else. Men think the same of women, but less. Men think women value ambition more than they do in the pre-speed-dating bar chart.

![image](https://user-images.githubusercontent.com/111237645/201792390-df268f23-6d46-4086-82c6-49be0245fe58.png)
![image](https://user-images.githubusercontent.com/111237645/201792409-c3aeee05-369f-479f-8bef-ee86e3f36e38.png)
Post-speed-dating Men and Women prefer attractiveness more than pre-speed-dating. Both still prefer ambition the least of the attributes.

# Question 3: How does an individuals Career Goal influence how they rate themselves vs how they rate their partners attritubes?

We could not conclude that a person’s intended career has any significant influence on how they rate their own attributes or how they were rated by their partner. On average the rates were between 7 and 8 when rating themselves and 6 and 7 when rating others.  Because of this, we took the mean value of all the participant’s scores and looked closely on how they differentiate.  

First, we need to check how many unique careers are in the data. Then we need to determine which careers we should drop. Including carrers with very few entries would skew the data. Somebody can make the wrong assumption about certain career types with one or two individuals responses compared to a career type with many people.

<img width="684" alt="image" src="https://user-images.githubusercontent.com/76061893/201706111-028ad46d-954c-4665-bc78-9e0b4dfae403.png">

The data we are using has multiple rows per individual and those rows include unique values and duplicate values. Intended Career is duplicate value. To get a proper count I first dropped all duplicates based on Unique ID, keeping only the first entery (keeping the last would work all the same).
<img width="513" alt="image" src="https://user-images.githubusercontent.com/76061893/201706437-3103f4dd-b3a3-411a-b5ea-f553db310682.png">

Now we want to remove any Intended Career with too few participates. I removed Career tpes based on the middle quantile, 50th percentile.

<img width="513" alt="image" src="https://user-images.githubusercontent.com/76061893/201706562-2f8fa813-acb7-42f2-a11f-283eacf7a6a8.png">

Create a new database from the main_df and include only careers listed in the career_count_df. We use the main dataframe because it still includes all the individual datapoints we need to calculate the mean values of attribute ratings later on.

<img width="514" alt="image" src="https://user-images.githubusercontent.com/76061893/201706647-b7c50e29-ed17-4f7e-96a8-d8774635cd9a.png">

Now we want to simplify the dataframe by using the listing the interested columns and using the copy function.
(this is optional but it helps with writing code later on see all the column names in one place)

<img width="517" alt="image" src="https://user-images.githubusercontent.com/76061893/201706753-d17cdc37-7be8-4cbd-8964-1252222035e3.png">

To get the average scores by career type, use the groupby function to combine all the enteries by Intended Career and then calculate the mean of all those values.

<img width="515" alt="image" src="https://user-images.githubusercontent.com/76061893/201706826-210a985a-2520-40a9-8292-e296995bffdf.png">

Merge all these dataframes into one consolidated dataframe. One database will help simplify the coding needed to display the charts later on.

<img width="512" alt="image" src="https://user-images.githubusercontent.com/76061893/201707443-666697af-fb4b-47e2-90de-f2d3682e3d5f.png">

Using Seaborn we are able to use simple coding to create fast scatterplots and export png files. While scatterplots are best used to show many datapoints, We find it also be to a great visual tool to display two variables across many catagories.

<img width="514" alt="image" src="https://user-images.githubusercontent.com/76061893/201707303-e820c608-4ce4-4176-839a-e7c425b1f5cb.png">

# Question 4: How does a speed dating participant's "intended career" impact the amount of positive matches and positive partner decisions they receive? Does age have an effect on matching?

This anaylsis begins with creating a dataframe of relevant data; partner decisions, matches, and intended careers. A summary pie chart is produced to show the amount of positive and negative matches for all instances of speed dating. From there, calculations of positive or negative matches based on intended career were run. As well as partner positive or negative decisions(even if no match occurred) based on intended career. The total numbers as well as percentages were figured. These calculations were put into a summary dataframe. Next the intended careers with few participants were dropped in order to prevent skews in the results. The drop was calculated by overall total matches of less than 240 as suggested by the authors of the data. From there, the quartiles and the upper/lower bounds were calculated as well as a whisker box plot to see if there were any potential outliers. No outliers were shown and the lower quartile was set at 15.2 and upper quartile was set at 18.7. A bar chart was created to show the careers that had the best percentages of finding a positive match. The two careers that found the most success(in the upper quartile) were Psychologist and Lawyer. The two careers that found least success(lower quartile) were those who were undecided for their intended career and those looking to be apart of International Affairs. Positive Partner Decisions was the next focus. A positive partner decision is recorded as receiving a yes from your speed dating partner, even though you chose no for them leading to a negative match. Quartiles along with a box and whisker plot was also created. Psychologists and Academic Research were in the lower quartile, with Doctor and International Affairs in the upper quartile. But all percentages for each career were within 10 points of eachother, so there was no significance between intended career and the rate of positive partner decisions. Finally, there is a bar chart summarizing total numbers of matches and partner decisions per career.

The next piece of analysis looks into age and total number of positive or negative matches, starting with a trimmed dataframe of the relevant information. Again the dataframe had to be trimmed in order that ages with small numbers of participants did not skew the results. And the results turned out to also be insignificant. Scatter plots for both positive and negative matches per age were created along with linear regressions and correlation statistics. Negative matches based on age had a correlation of 0.14. This means there is no correlation between age and negative matches. Postive matches had a correlation of -0.08. Also no correlation.

<img alt="image" src="https://user-images.githubusercontent.com/113069752/201735888-a8fd47fb-4cf9-4c0b-9c07-6789b910ac74.png">

<img alt="image" src="https://user-images.githubusercontent.com/113069752/201736061-981d7edb-266a-458b-9a94-c2e68e5c2924.png">

<img alt="image" src="https://user-images.githubusercontent.com/113069752/201736128-eb323eaa-4917-405c-882b-03a043d91257.png">
