# Moving Violations and Crash Relationship and Causality analysis.

What is the general solution for Washinton's poor driving habbits?  Red-Light Cameras and Speed Traps.  
Using data available on opendata.dc.gov, I compare the causality relations of Crashes and Automated ticket traps at hundreds of locations within the District of Columbia.

------

### TICKETS AND CRASHES WRANGLING & CLEANING PART 1 Notebook
In this notebook I take a look at the data I gathered from Open Data DC and assessed what needed to be done in order to prep that data for an analysis.  The data files for moving violations were broken down by months and years so most of this notebook is repetitive actions for adjusting and dropping unneeded features as well as combining files into larger aggregate files.  I admit, I should have created a function for this.  

##### Technologies Used: 
- Language(s): Python
- Libraries: Pandas, Numpy
- IDE: Jupyter Notebook

---

### Data Prep for Visual Presentation Notebook
In this notebook I do a quick visual eda and create some plots that I used later for my presentation.  Additionaly, All the yearly moving violations data files are merged into one dataframe as well.  Two datasets a crafted that are used to display regions where crashes occur and deaths related to crashes in Tableau, which can be viewed on my [Tableau Public Profile.](https://public.tableau.com/profile/samuel.stack#!/vizhome/DCCrashesTicketsVisualAnalysis/CTTimeSeries "Crashs and tickets given for January 2009") 
- *Tableau Public has an issue where pages don't work properly, so dates need to be clicked through instead of playing.*

##### Technologies Used: 
- Language(s): Python
- Libraries: Pandas, Numpy, Seaborn, Matplotlib
- IDE: Jupyter Notebook
- BI/Other Tools: Tableau

---

### Granger Causaility Test Notebook
Here I do final data prep for the information to be passed through a Granger Causaility function.  The Granger Causaility function is a means to assess if a given event is caused by a prior event occuring.  In my situation I am testing to see the the event of placing a speed trap (increase in a locations tickets) causes the ideal reaction (decrease in the locations vehicle related accidents).  I also tested for the inverse of that increase in tickets and placement of cameras also increased the number of vehicle related incidents. 
As I was testing thousands of locations and values in one go I created a function to test various lag periods for both Granger cause hypothesis.  

Some additional library and model experiments were attempted towards the end of the notebook.  As locations were provided in longitude and latitude accurate up to centimeters I had to generalize to create broader regions, like intersection side where records from the moving violation data could match with records for vehicle insident data. In the end longitude and latitude were truncated via rounding to created broader regions with more overlap.  

I tried to use the **Geopy** library to create location codes instead of longitude and latitude, however the computational expense proved to be too much, even for the AWS isntance I spun up (64 core, +250gb ram; pretty sure these resources are shared simultaneosly with others.)

I also experimented with **DBSCAN**, a unsupervised clustering model, in order to create unique location aggregates and create clusters representing general locations within the district.  This also proved to be computationally expensive and did not produce the desired fruit.  While the model was able to be fit and created, the function used to assess how well the model had created clusters proved to be too much for my machine to manage.

##### Technologies Used: 
- Language(s): Python
- Libraries: Pandas, Numpy, SKLearn, GeoPy, StatsModels
- IDE: Jupyter Notebook
- BI/Other Tools: Amazon Web Services

---

### Interpretting Results
The results of the GC Test were stored in a dataframe and needed to be massaged out and then evaluated.  For the final results of the test I take regions who had P-values less than 0.05 (in either Tickets GC crashes(loss) or crashes GC tickets).  These values were then extracted a made into a Tableau Visualization part of this [Tableau Story.](https://public.tableau.com/profile/samuel.stack#!/vizhome/DCCrashesTickets/Story1)

##### Technologies Used: 
- Language(s): Python
- Libraries: Pandas, Numpy
- IDE: Jupyter Notebook
- BI/Other Tools: Tableau
