# Iowa Liquor Store and Sales Research
___

Given my Marketing background I thought it would be fun to see how I can combined what data science skills I have learned with my marketing knowledge in somewhat of a 'Market Research' problem.

Iowa has a Liquor problem! Not the 'AA' type, but that there are not enough stores to handle the statewide alcohol demand. 
Using the statewide sales data from 2015 and some of 2016 I'm going to identify some ideal county locations for opening some new stores.

--- 

## Portfolio 2 - Iowa Liquor Sales

### Data Acquisition and Prep
The data was provided by General Assembly, but is also publicly available on the [data.iowa.gov](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy "Iowa Liquor Sales") website. 
Do a quick exploratory analysis gaining insight on sales per county and monthly sales across Iowa as well.  In this phase I also merge in population data found on [iowa-demographics.com](http://www.iowa-demographics.com/counties_by_population "Iowa Counties by Population") and find county aggregates.

It is important to mention these sales records are Distributor to Store and recorder by the state who monitors alcohol sales.  These are not sales to private citizens.  It took me a while to realize this, as almost all the transactions are bulk transactions.  This being said some of the transactions were in the hundreds of thousands of dollar ranges, as these were few and far between it was unsafe to assume the a store or county would receive these types of sales regularly and so they were dropped from the data.

### Data Analysis and Insight
Using the engineer features 'Per Capita Sales (USD)' and 'AVG Store Sales per County' I created a simple [scatter plot with Tableau](https://public.tableau.com/profile/samuel.stack#!/vizhome/Project2Iowa/Sheet1) to compare the two features.  Ideally there would be a trending relation between the two and outlying points would warrant a further investigation.  According to the visualization there was one county that stuck out from the rest, Dickinson.  Dickinson had over twice the average per capita sales and clocked in as sixth in store sales.  1 through 5 were all cities with large population centers.
This combination led me to nominate Dickinson county for further investigation into opening up a new liquor retailer.  

The **TL;DR** of my research show that Dickinson would be the best county for further investigations as far as opening up a new Liquor Score.

### Technologies Used
- Language(s): Python
- Libraries: Pandas, Seaborn, Matplotlib
- IDE: Jupyter Notebook
- BI/Other Tools: Tableau




## Iowa Redux

I am currently working on creating a predictive model that will take in sales features from the first 3 months of a year and predict the annual sales.  

Additionally, I will be doing some more investigation as far as the types of liquor Iowa likes to consume.
