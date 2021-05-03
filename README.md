# Analysis of Kickstarter Campaigns

## Overview of Project
In this analysis we want to want to examine past Kickstarter campaigns in the hopes of developing insights that will help identify trends and patterns that will allow us to launch our own successful Kickstarter. We want to be able to mirror other successful campaigns in our chosen category.

### Purpose
Our analysis is centered on *Louise* and her new Kickstarter campaign. She is an up-and-coming playwright and wants to develop her own Kickstarter campaign to launch her new play ***Fever***.  We will be using excel to examine past Kickstarter campaigns and see if successful campaigns had any similarities that *Louise* can consider when launching her own campaign.
## Analysis and Challenges
For our analysis we will be using the Kickstarter Dataset provided. [data-1-1-3-StarterBook.xlsx](https://github.com/rulma/Kickstarter-Anlaysis/files/6412494/data-1-1-3-StarterBook.xlsx). We will breakdown the campaigns by their respective outcome (Successful, Failed, Cancelled, Live), Campaign Goal for Funding, and Pledged Funding amounts. We will then breakdown the campaigns based on their Parent Category and Subcategory. 

***Fever*** is going to be a play so we will pay close attention to campaigns in the "Plays" subcategory. We will also look to see if the launch date and goals set by past campaigns had any impact on their performance.

### Analysis of Outcomes Based on Launch Date
When looking at our dataset we wanted to see if there was any relationship between when a campaign was launched and the likelihood that it would be successful. We wanted to our campaign launch dates by months. By grouping by months, we can get an overview of the seasonality of campaign's success throughout the calendar year.

For our PivotTable we wanted to count the total number of campaigns that fell under the Parent Category *Plays* and grouped by the month they were launched.
To do this we used the following settings to create our table.

![Date Pivot Table Settings](https://user-images.githubusercontent.com/82015631/116833176-43b30700-ab7d-11eb-92b8-260af7310bf3.PNG)

Once we did that we then filtered by the *Parent Category* so that it only displayed campaigns that were labeled as *Plays*. Our table then gave us the following information.

![Date Pivot Table](https://user-images.githubusercontent.com/82015631/116833195-62190280-ab7d-11eb-8c39-4c21eeadf260.PNG)

Using this table, we were able to create a line graph that visualized the relationship between a campaigns launch date and the likelihood that it either was successful, canceled or failed.

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/82015631/116832802-e36f9580-ab7b-11eb-9296-ada7b3694ccf.PNG)



### Analysis of Outcomes Based on Goals
The next focus of our analysis is the relationship between a campaign listed goals and the rate at which they were successful. We wanted to see if there was any relationship to a campaign having a higher or lower ($) amount Goal and their ability to receive full funding. We wanted to know of higher cost campaigns outperformed lower cost campaigns.

To do this we had to create table that organized our data by several variables. First, we wanted to breakdown our campaigns into buckets based off the goal they set in the **goal** column. Those buckets were as follows: 
- Less than $1,000
- $1000 to $4999
- $5000 to $9999
- $10000 to $14999
- $15000 to $19999
- $20000 to $24999
- $25000 to $29999
- $30000 to $34999
- $35000 to $39999
- $40000 to $44999
- $45000 to $49999
- Greater than $50000

Within these buckets we then wanted to count the number of campaigns that were successful, failed, and were canceled. To do this in Excel we utilized the following formula
```
=COUNTIFS('Kickstarter Data'!$G$2:$G$4115,"successful",'Kickstarter Data'!$E$2:$E$4115,"<1000",'Kickstarter Data'!$P$2:$P$4115,"plays")
```
The three criteria we are checking in the above example is that the campaign was *Successful*, had goal of less than $1,000, and fell into the *Plays* category. The criteria changed depending on the outcome we were counting and the respective Goal bucket it fell into. Once we had a count of all campaigns and their outcomes, we were able to calculate the percentage of successful, failed, and canceled campaigns. 

Our finished table looked as follows: 

![Outcome_vs_Goals_Table](https://user-images.githubusercontent.com/82015631/116834235-b8d50b00-ab82-11eb-97a6-7ba56295fff3.PNG)

With this table we were then able to create an additional line graph to visualize the relationship between a campaign’s outcome and the initial goal set by its creators.

Our graph is shown below:

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/82015631/116832805-e9657680-ab7b-11eb-8a54-723ab7c83226.png)

### Challenges and Difficulties Encountered
We ran into a challenge right away, unfortunately, the raw dataset only had the dates formatted in XML (Extensible Markup Language). So first we had to convert all of our dates into a more readable format. 

To do this we created a new column in our workbook titled "Date Created Conversion" and utilized the following formula to convert the data found in column "launched_at":

```
=(((K2/60)/60)/24)+DATE(1970,1,1)
```

Once we had nice readable dates formatted for every campaign it was much easier to conduct our analysis.

Another issue without dataset is that we are comparing campaigns from all across the world to one another. This can be misleading because of the discrepancy associated with costs around the globe. For example, it would cost you more to launch a new play in New York City when compared to a small town in Mexico. Our inability to account for this discrepancy may skew our data and conclusions.

In order to account for this in the future maybe we could use an additional column that gave the Cost-of-Living Index for each campaign and its respective campaign. Using this index, we could develop a way to weight our campaigns and their relative success to the cost of living in their area. In addition, we could convert all our currency values into a uniform currency such as the USD. This would make it easier to compare a campaign that raised MX$ 40,0000 to one that raised USD $40,0000.

With the inclusion of a COI index and uniformed currency we could create a more accurate graph to compare the relative financial success of the campaigns. We could accurately compare a campaign that raised $400,000 in NYC with a campaign in small town Mexico that raised $2,000. Without accounting for the difference in costs of living we would assume that the NYC campaign was more successful or better performing but in comparison the campaign in Mexico may have a raised a greater amount of money relative to the GDP of its community.

## Results

With our analysis we can draw several conclusions. In our initial analysis we looked at the relationship between a campaign launch date and its outcome. We found that from the month of January to May we saw the total number of successful campaigns doubled, meanwhile, the total number of canceled and failed campaigns held relatively constant. The number of successful campaigns peaks in the month of May and then slowly regresses as the summer comes to an end. 

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/82015631/116834627-96dc8800-ab84-11eb-885d-c9d0d114655f.PNG)

As we can see not only are more campaigns successful in the summer but the ratio of successful campaigns to failed campaigns grows as well. In the month of May successful campaigns outnumber failed campaigns by more than 2:1. Now this dataset is looking at campaigns from around the world, but most of the theater campaigns took place in the United States. 

![category breakdown](https://user-images.githubusercontent.com/82015631/116834829-7660fd80-ab85-11eb-97c5-85b21140a9bd.PNG)

Over 60% of theatre campaigns took place in the US. Now in the United States taxes must be filed by April 15th and once one has filed their taxes, they can be eligible for a tax refund. By the month of May most citizens eligible for a refund have received it. This influx of disposable income may explain the increased levels of successful campaigns through the summer months. 

The noticeable downturn of campaigns created in the winter months may be related to the Holiday season. Many people are focused on saving to travel, purchase gifts, and visit their extended family. The average person may have less disposable income in the winter months and therefore may be less likely to give to Kickstarter campaign that they would've supported at another time during the year. 

This downturn is especially notable in the month of December which had not only the least number of successful campaigns but also the lowest total of campaigns started. This points to people who would normally create campaigns do so outside of the busy holiday season. 

Lastly, when looking at campaign outcomes relative to their goals we notice an interesting trend. 

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/82015631/116835047-64cc2580-ab86-11eb-8cf5-e5f0761a6c05.png)

We can see that campaigns that set a goal of less than $1,000 saw nearly a ~%80 success rate. Meanwhile, on the opposite end of the spectrum, campaigns with a goal greater than $45,000 saw >80% chance to fail. We may be able to assume that people creating campaigns for under $1,000 have realistic goals for what they want to accomplish and have accurately estimated the costs associated. It is also easier to convince a smaller loyal group of supporters to offer small donor donations. As the cost of a campaign increases so too will either the number of backers or the average dollar donation. Doing either of these things is challenging. 

Think for example that you want to raise money to repair the basketball court in your community. It would be quite easy for you to raise $1,000 by collecting money from community residents who enjoy and use the court. But let us say you wanted to raise money to build a swimming pool, this could cost upwards of $200,000. Those in your community may be just a supportive but are unable to provide either the necessary number of backers or the average donation size needed to make the campaign successful. 

Having small clear though out campaigns that are targeted well to your potential stakeholders will increase the likelihood that you are able to receive the funding that you are requesting. 

In conclusion, we recommend that *Louise* launches her Kickstarter campaign in the summer with a small and concise goal of less than $10,000. By doing this she should increase the chances of having a successful campaign thus bringing the joy of her play ***Fever*** to the public.
# Analysis of Kickstarter Campaigns

## Overview of Project
In this analysis we want to want to examine past Kickstarter campaigns in the hopes of developing insightts that will help identify trends and patterns that will allow us to launch our own succesful Kickstarter. We want to be able to mirror other succesful campaigns in our chosen category.

### Purpose
Our analysis is centered on *Louise* and her new Kickstarter campaign. She is an up and coming playwright and wants to develop her own Kickstarter campaign to launch her new play ***Fever***.  We will be using excel to examine past Kickstarter campaigns and see if succesful campaigns had any simalarities that *Louise* can take into account whe launching her own campaign.
## Analysis and Challenges
For our analysis we will be using the Kickstarter Dataset provided. [data-1-1-3-StarterBook.xlsx](https://github.com/rulma/Kickstarter-Anlaysis/files/6412494/data-1-1-3-StarterBook.xlsx). We will breakdown the campaigns by their respective outcome (Succesful, Failed, Cancelled, Live), Campaign Goal for Funding, and Pledged Funding amounts. We will then breakdown the campaigns based on their Parent Category and Subcategory. 

***Fever*** is going to be a play so we will pay close attention to campaigns in the "Plays" subcategory. We will also look to see if the launch date and goals set by past campaigns had any impact on their performance.

### Analysis of Outcomes Based on Launch Date
When looking at our dataset we wanted to see if there was any relationship between when a campaign was launched and the likelihood that it would be succesful. We wanted to our campaign launch dates by months. By grouping by months we can get an overview of the seasonality of campaign's success throughout the calendar year.

For our PivotTable we wanted to count the total number of campaigns that fell under the Parent Category *Plays* and grouped by the month they were launched.
To do this we used the following settings to create our table.

![Date Pivot Table Settings](https://user-images.githubusercontent.com/82015631/116833176-43b30700-ab7d-11eb-92b8-260af7310bf3.PNG)

Once we did that we then filtered by the *Parent Category* so that it only displayed campaigns that were labeled as *Plays*. Our table then gave us the following information.

![Date Pivot Table](https://user-images.githubusercontent.com/82015631/116833195-62190280-ab7d-11eb-8c39-4c21eeadf260.PNG)

Using this table we were able to create a line graph that visualized the relationship between a campaigns launch date and the likelihood that it either was succesful, canceled or failed.

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/82015631/116832802-e36f9580-ab7b-11eb-9296-ada7b3694ccf.PNG)



### Analysis of Outcomes Based on Goals
The next focus of our analysis is the relationship between a campaigns listed goals and the rate at which they were succesful. We wanted to see if there was any relationship to a campaign having a higher or lower ($) amount Goal and their ability to receive full funding. We wanted to know of higher cost campaigns outperformed lower cost campaigns.

To do this we had to create table that organized our data by several variables. First we wanted to breakdown our campaigns into buckets based off of the goal they set in the **goal** column. Those buckets were as follows : 
- Less than $1,000
- $1000 to $4999
- $5000 to $9999
- $10000 to $14999
- $15000 to $19999
- $20000 to $24999
- $25000 to $29999
- $30000 to $34999
- $35000 to $39999
- $40000 to $44999
- $45000 to $49999
- Greater than $50000

Within these buckets we then wanted to count the number of campaigns that were succesful, failed, and were canceled. To do this in Excel we utilized the following formula
```
=COUNTIFS('Kickstarter Data'!$G$2:$G$4115,"successful",'Kickstarter Data'!$E$2:$E$4115,"<1000",'Kickstarter Data'!$P$2:$P$4115,"plays")
```
The three criteria we are checking in the above example is that the campaign was *Succesful*, had goal of less than $1,000, and fell into the *Plays* category. The criteria changed depending on the outcome we were counting and the respective Goal bucket it fell into. Once we had a count of all campaigns and their outcomes we were able to calculate the percentage of succesful, failed, and canceled campaigns. 

Our finished table looked as follows: 

![Outcome_vs_Goals_Table](https://user-images.githubusercontent.com/82015631/116834235-b8d50b00-ab82-11eb-97a6-7ba56295fff3.PNG)

With this table we were then able to create an additional line graph to visualize the relationship between a campaigns outcome and the initial goal set by its creators.

Our graph is shown below:

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/82015631/116832805-e9657680-ab7b-11eb-8a54-723ab7c83226.png)

### Challenges and Difficulties Encountered
We ran into a challenge right away, unfortunately, the raw dataset only had the dates formatted in XML (Extensible Markup Language). So first we had to convert all of our dates into a more readable format. 

To do this we created a new column in our workbook titled "Date Created Conversion" and utilized the following formula to convert the data found in column "launched_at":

```
=(((K2/60)/60)/24)+DATE(1970,1,1)
```

Once we had nice readable dates formatted for every campaign it was much easier to conduct our analysis.

Another issue with out dataset is that we are comparing campaigns from all across the world to one another. This can be misleading because of the discrepency asscociated with costs around the globe. For example, it would cost you more to launch a new play in New York City when compared to a small town in Mexico. Our inability to account for this discrepency may skew our data and conclusions.

In order to account for this in the future maybe we could use an additional column that gave the Cost of Living Index for each campaign and its respective campaign. Using this index we could develop a way to weight our campaigns and their relative success to the cost of living in their area. In addition, we could convert all of our currency values into a uniform currency such as the USD. This would make it easier to compare a campaign that raised MX$ 40,0000 to one that raised USD $40,0000.

With the inclusion of a COI index and uniformed currency we could create a more accurat graph to compare the relative finacial success of the campaigns. We could accurately compare a campaign that raised $400,000 in NYC with a campaign in small town Mexico that raised $2,000. Without accounting for the difference in costs of living we would assume that the NYC campaign was more succesful or better performing but in comparison the campaign in Mexico may have a raised a greater amount of money relative to the GDP of its community.

## Results

With our analysis we are able to draw several conclusions. In our initial analysis we looked at the relationship between a campaigns launch date and its outcome. We found that from the month of January to May we saw the total number of succesful campaigns doubled, meanwhile, the total number of canceled and failed campaigns held relatively constant. The number of sucesful campaigns peaks in the month of May and then slowly regresses as the summer comes to an end. 

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/82015631/116834627-96dc8800-ab84-11eb-885d-c9d0d114655f.PNG)

As we can see not only are more campaigns succesful in the summer but the ratio of successful campaigns to failed campaigns grows as well. In the month of May sucsesful campaigns outnumber failed campaigns by more than 2:1. Now this dataset is looking at campaigns from around the world but the vast majority of the theater campaigns took place in the United States. 

![category breakdown](https://user-images.githubusercontent.com/82015631/116834829-7660fd80-ab85-11eb-97c5-85b21140a9bd.PNG)

Over 60% of theatre campaigns took place in the US. Now in the United States taxes must be filed by April 15th and once one has filed their taxes they can be eligble for a tax refund. By the month of May most citizens eligible for a refund have received it. This influx of disposable income may explaing the increased levels of sucessful campaigns through the summer months. 

The noticible downturn of campaigns created in the winter months may be related to the Holiday season. Many people are focused on saving to travel, purchase gifts, and visit their extended family. The average person may have less disposable income in the winter months and therfor may be less likely to give to Kickstarte campaign that they would've supported at another time during the year. 

This downturn is especially notable in the month of December which had not only the least number of succesful campaigns but also the lowest total of campaigns started. This points to people who would normally create campaigns do so outside of the busy holiday season. 

Lastly, when looking at campaign outcomes relative to their goals we notice an interesting trend. 

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/82015631/116835047-64cc2580-ab86-11eb-8cf5-e5f0761a6c05.png)

We can see that campaigns that set a goal of less than $1,000 saw nearly a ~%80 success rate. Meanwhile, on the opposite end of the spectrum, campaigns with a goal greater than $45,000 saw >80% chance to fail. We may be able to assume that people creating campaigns for under $1,000 have realistic goals for what they want to accomplish and have accurately estimated the costs associated. It is also easier to convice a smaller loyal group of supporters to offer small donor donations. As the cost of a campaign increases so too will either the number of backers or the average dollar donation. Doing either of these things is challenging. 

Think for example that you want to raise money to repain the basketball court in your community. It would be very easy for you to raise $1,000 by collecting money from community residents who enjoy and use the court. But lets say you wanted to raise money to build a swimming pool, this could cost upwards of $200,000. Those in your community may be just a supportive but are unable to provide either neccesary number of backers or average donation size to make the campaign succsful. 

Have small clear thoughtout campaigns that are targeted well to your potential stakeholders will increas the likelihood that you are able to receive the funding that you are requesting. 

In conclusion, we recommend that *Louise* launches her Kickstarter campaign in the summer with a small and concise goal of less than $10,000. By doing this she should increase the chances of having a succesful campaign thus bringing the joy of her play ***Fever*** to the public.
