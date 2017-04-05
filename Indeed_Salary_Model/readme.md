# Indeed Scrape and Salary Model

What better way to practice web scraping and data science than to evaluate my worth as a data scientist!?!

In this project I scrape hundreds of 'Data Scientist' and 'Data Analyst' positions posted on [Indeed.com](https://www.indeed.com/ "Indeed Homepage") from cities all accross the U S of A.

#### Gather
Using the BeautifulSoup library I was able to make requests to hundreds of pageds of job postings on Indeed much faster than a human ever could. I gathered information from postings such as title, location, company, short description and salary(where available).  I encorporated a good deal of Regex in the scraper so my data would need less cleaning later on.
Unfortunately, the boiler plate descriptions did not hold all the information I desired and so another scraper was built to go into all of the individual postings and gather full job descriptions.

#### Prep
The full job descriptions were text vectorized using a Term Frequency Inverse Document Frequency vectorizer (I am curious to see what the models would have been like with a standard text vectorizer as well).  Other information like location and title were made into dummie variables.  

#### Model
I decided to experiment with two model goals.  The first was a two-class classifier to identify it a position was above or below the median salary.  The second was a five-class classifier that would classifier positions bases on the quartile ranges of the salarys that I had.

Standard Decision Tree, Random Forest Classifiers, Random Forest Regressors and Logistic Regressors were built.  In the End the Standard Decision Tree binary classifier was the most accurate of the models.

### Suggestions
I believe a stronger text extraction could have seriously helped my model.  Even though stop words were considered, there are also tons of other descriptive words like 'Specializing' or 'Adamant' that may show up in a post and be awarded too much weight by the TFIDF text vectorizer, when in actuality they are not representative of the position at all.  Using a list of skill and technologies as features would most likely prove to be more beneficial. As the model could weigh individual skills as well as understand how those skill complement each other and come to a more justified prediction.  

This is definitely a project that I would like to revisit.  



### Technologies
- Language(s): Python, HTML
- Libraries: BeautifulSoup, Pandas, Numpy, SKLearn, Urllib, Matplotlib, Seaborn.
- IDE: Jupyter Notebook
- BI/Other Tools: Selenium, Regex
