# Analysis of Kickstarter Campaigns

## Overview of Project
In this analysis we want to want to examine past Kickstarter campaigns in the hopes of developing insightts that will help identify trends and patterns that will allow us to launch our own succesful Kickstarter. We want to be able to mirror other succesful campaigns in our chosen category.

### Purpose
Our analysis is centered on *Louise* and her new Kickstarter campaign. She is an up and coming playwright and wants to develop her own Kickstarter campaign to launch her new play ***Fever***.  We will be using excel to examine past Kickstarter campaigns and see if succesful campaigns had any simalarities that *Louise* can take into account whe launching her own campaign.
## Analysis and Challenges
For our analysis we will be using the Kickstarter Dataset provided. [data-1-1-3-StarterBook.xlsx](https://github.com/rulma/Kickstarter-Anlaysis/files/6412494/data-1-1-3-StarterBook.xlsx). We will breakdown the campaigns by their respective outcome (Succesful, Failed, Cancelled, Live), Campaign Goal for Funding, and Pledged Funding amounts. We will then breakdown the campaigns based on their Parent Category and Subcategory. 

***Fever*** is going to be a play so we will pay close attention to campaigns in the "Plays" subcategory. We will also look to see if the launch date and goals set by past campaigns had any impact on their performance.

### Analysis of Outcomes Based on Launch Date
When looking at our dataset we wanted to see if there was any relationship between when a campaign was launched and the likelihood that it would be succesful. We wanted to look at campaign launch dates by Months. 

For our PivotTable we wanted to count the total number of campaigns based off of the month they were launched and that fell under the Parent Category *Plays*.
To do this we used the following settings to create our table.

![Date Pivot Table Settings](https://user-images.githubusercontent.com/82015631/116833176-43b30700-ab7d-11eb-92b8-260af7310bf3.PNG)

Once we did that our we then filtered by the *Parent Category* so that it only displayed campaigns that were labeled as *Plays*. Our table then gave us the following information.

![Date Pivot Table](https://user-images.githubusercontent.com/82015631/116833195-62190280-ab7d-11eb-8c39-4c21eeadf260.PNG)

Using this table we were able to create a line graph that visualized the relationship between a campaigns launch date and the likelihood that it either was succesful, canceled or failed.

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/82015631/116832802-e36f9580-ab7b-11eb-9296-ada7b3694ccf.PNG)



### Analysis of Outcomes Based on Goals
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/82015631/116832805-e9657680-ab7b-11eb-8a54-723ab7c83226.png)

### Challenges and Difficulties Encountered
We ran into a challenge right away, unfortunately, the raw dataset only had the dates formatted in XML (Extensible Markup Language). So first we had to convert all of our dates into a more readable format. 

To do this we created a new column in our workbook titled "Date Created Conversion" and utilized the following formula to convert the data found in column "launched_at":

```
=(((K2/60)/60)/24)+DATE(1970,1,1)
```

Once we had nice readable dates formatted for every campaign we then wanted to create a pivot table to help us filter and sort the data we wanted to graph. 

Another issue with out dataset is that we are comparing campaigns from all across the world to one another. This can be misleading because of the discrepency asscociated with costs around the globe. For example, it would cost you more to launch a new play in New York City when compared to a small town in Mexico. Our inability to account for this discrepency may skew our data and conclusions.

In order to account for this in the future maybe we could use an additional column that gave the Cost of Living Index for each campaign and its respective campaign. Using this index we could develop a way to weight our campaigns and their relative success to the cost of living in their area. In addition, we could convert all of our currency values into a uniform currency such as the USD. This would make it easier to compare a campaign that raised MX$ 40,0000 to one that raised USD $40,0000.
## Results
