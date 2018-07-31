# MSDS696-FinalProject
Data Science Practicum II Final Project
by Vanessa Gonzalez, August 2018

## Admissions' Yield Prediction by Gender in a Colorado Higher Education Institution.

# Project Overview

The term "Yield" in college admissions is the percent of students who choose to enroll in a particular college or university after having been offered admission.(1) Higher Education Institutions and Institutions with focus in STEM in particular need to have a better handle of the yield between admitted and enroll students. With the need of increasing female population and limited resources the admissions office needs to know what students have a better chance to enroll so they can invest these resources and attention with increased yield rates.

In this case will utilize data from last year (complete cycle) and will be able to increase the data set to two years after Census of Fall 2018. This colorado university bought a new software called "Slate" two years ago that captures not just the typical variables (race, age, act scores, etc.) from their admissions process but also captures more information like number of contacts with admission's staff, visits to the institution, number of clicks of the website etc. 

We will try to determine which are the variables or combination of variables with higher weight that determine importance by Gender. We will build a predictive model to help admissions utilize resources and attention of their staff more efficiently to increase yield. We will decide on the best model trying different algorithms. 


### Data Sets

The data used was extracted from the Admission's Slate University Database using the Slate application to query the database. Data from Fall 16 to Summer 2017 was used. The full dataset consisted of 11,162 records (number of applications) and 48 variables. A subset was created of just admitted students (6,235 students). This subset of data was used to create predicted models. A second subset of data was created including just female addmited students (2,046). Predictive models were created for this subset as well.

![image1](/Images/AdmittedStudentsGender.png)

### Observations on the Quality and Cleaning of the Data

Changes and cleaning were necessary:
* In some variables the NA values were substituted by "Missing" or "None" as appropriate.
* Other NA values were supbstituted with KNN method.
* In the "State" variable all other states were substituted by "Other" havin two outcomes; "CO" or "Other".
* Data types were transformed to appropriate type.
* Factor variables with more than 21 levels were omitted.
* Dummie variables were created for factor varialbes.
* All variables but the "Enrolling" variable were transformed into number variables.
* All numerical variables were normalized.

After modifications the finished data sets consisted of the fallowing variables:  
#### Data Set of Admitted Students

'data.frame':   6235 obs. of  48 variables:  
 $ Enrolling             : chr  "N" "N" "N" "N" ...  
 $ Sex                   : chr  "M" "M" "M" "M" ...  
 $ Expel                 : chr  "N" "N" "N" "N" ...   
 $ First.Gen             : chr  "N" "N" "N" "N" ...  
 $ Challenge Tag         : chr  "N" "N" "N" "N" ...  
 $ Pathway Tag           : chr  "N" "N" "N" "N" ...  
 $ Boettcher.Semi        : chr  "N" "N" "N" "N" ...  
 $ Boettcher.Final       : chr  "N" "N" "N" "N" ...  
 $ Daniels.Semi          : chr  "N" "N" "N" "N" ...  
 $ Daniels.Final         : chr  "N" "N" "N" "N" ...  
 $ Harvey.App            : chr  "N" "N" "N" "N" ...  
 $ Harvey.Final          : chr  "N" "N" "N" "N" ...  
 $ FC.App                : chr  "N" "N" "N" "N" ...  
 $ FC.Final              : chr  "N" "N" "N" "N" ...  
 $ Thorson.App           : chr  "N" "N" "N" "N" ...  
 $ Thorson.Admit         : chr  "N" "N" "N" "N" ...  
 $ Summet.App            : chr  "N" "N" "N" "N" ...  
 $ Summet.Participant    : chr  "N" "N" "N" "N" ...  
 $ Mines.Medal           : chr  "N" "N" "N" "N" ...  
 $ SPS                   : chr  "N" "N" "N" "N" ...  
 $ Veteran               : chr  "N" "N" "N" "N" ...  
 $ Legacy                : chr  "N" "N" "N" "N" ...  
 $ Athlete               : chr  "N" "N" "N" "N" ...  
 $ State                 : chr  "CO" "Other" "Other" "CO" ...  
 $ Citizenship           : chr  "U.S. Citizen" "U.S. Citizen" "U.S. Citizen" "U.S. Citizen" ...  
 $ Ethnicity             : chr  "Asian" "White" "White" "White" ...  
 $ Major.App             : chr  "Civil Engineering" "Mechanical Engineering" "Mechanical Engineering" "Mechanical Engineering" ...  
 $ First Contact         : chr  "ACT" "ACT" "GPA Form" "Campus Visit" ...  
 $ First Visit           : chr  "None" "Campus Tour" "None" "Campus Visit" ...  
 $ Sport                 : chr  "None" "None" "None" "None" ...  
 $ App.Created.Days      : num  339 339 339 339 335 335 333 333 333 333 ...  
 $ Age                   : num  20 24 31 35 35 23 33 18 19 19 ...  
 $ HS.GPA                : num  3.88 3.48 4 3.16 3.9 ...  
 $ SATR.Converted        : num  1370 1400 1400 1460 1370 1540 1190 NA 1430 1350 ...  
 $ Review.OutsideActivity: chr  "3" "3" "1" "3" ...  
 $ Review.Leadership     : chr  "2" "1" "0" "0" ...  
 $ Review.WorkExp        : chr  NA "2" "0" "1" ...  
 $ Review.WorkEthic      : chr  NA "3" "0" "0" ...  
 $ Review.ExpDiversity   : chr  "3" "2" "0" "1" ...  
 $ Review.DesireAttend   : chr  NA "2" "0" "2" ...  
 $ Review.Affinity       : chr  NA "2" "1" "0" ...  
 $ Review.InnovEntrep    : chr  NA "0" "0" "0" ...  
 $ Review.Teamwork       : chr  "3" NA "0" "1" ...  
 $ Review.OverallFit     : chr  "7" "8" "7" "8" ...  
 $ Logins.60Days         : num  0 0 0 0 0 0 0 0 0 0 ...  
 $ EventCount.All        : num  0 1 0 0 0 0 0 0 0 2 ...  
 $ EventCount.Admitted   : num  0 0 0 0 0 0 0 0 0 2 ...  
 $ EventCount.Campus     : num  0 1 0 0 0 0 0 0 0 2 ...  


#### Data Set 2

2,046 Female Students. Same variables than above.

### Process for Project and Major Tools Used

This project was completed utilizing:
* Slate -  to query the University data base and produce a csv file to be used by Tableau and R-Studio.
* Tableau – to clean, format, and combine csv files into two main files. Tableauwasalso used to create some visualization.
* R – Used to modify, and analyze the two main data sets. R files are located at:
* A youtube presentation is located at: 

# EDA (Exploratory Data Analysis)

The full dataset was uploaded, summaries, data frames, tables, and plots created using the code in the files attached and Tableau.

![image2](/Images/Bubble.png =250x250 )
![image6](/Images/%EnrolleAdmittedStudents.png)
![image3](/Images/PieChart.png). 

Bar plots were created for "admitted enrolled" numbers and "admitted enrolled" students divided by gender.

![image4](/Images/BarChart.png)
![image5](/Images/BarchartWithGender.png)
![image7](/Images/AdmittedByEthnicity.png)

Summaries were created.  

![image3](/images/SummaryLastClass.png)

To start the analysis for four year graduation success the need of creating a subset of the data arised. It was necessary to look at just the students that had completed the CS program succesfully in four years. It was also helpful to find the correlation between the courses taken by the students. The code below was used to achieve this.

![image4](/images/CorrelationPlot.png). 

# Analysis
## Building the Models in R
Several Libraries were used to perform this task:
* library("mlbench"). 
* library("dplyr"). 
* library("caret"). 
* library("randomForest")  
* library("lattice"). 
* library("ggplot2"). 
* library("rpart"). 
* library("e1071"). 
* library("caret"). 

Three main models were used to determine variable importance, to train, and test the model.

* Regression Partition with method "class". 
* Random Forest model. 
* Logistic Regresion.  
80% of the data was used as the training set and 20% of the data was used as the testing set.

Models were created using all courses variables and then subsequently variables with less importance were removed. New models were created for this new data set. Several methods were tried to increase accuracy. Trees were prunned, size of training set was increased and different number of variables were removed. The ideal conditions for accuracy are the ones shown below.

### Regression Classification Trees and Random Forest Using All Variables
* Partitions Creation
* Regression Partition with method "class".
* Random Forest Method
* Logistic Regression Method for Variable Importance

### Models using less variables
* Regression Partition with method "class" for set with less variables
* Random Forest model with less variables
* Logistic Regression with less variables

### Prediction of Students at Risk on Fifth Semester

* Random Forest model using less variables for semester 5
* Regresion Partition with method "class" for less variables for 5th semester courses.
* Random Forest method with less variables on 5th semester.
* Logistic Regression method for variable importance

# Analysis Results
Results were produced for Regresion Partition with all variables, after pruning, and Random Forest for three data sets:  
## All courses variables
#### Regression Partition with method "class".
![image5](/images/RegressionAllV.png)
#### Pruned Tree
![image6](/images/PruneAll.png)
#### Random Forest
![image7](/images/RFAll.png)
![image8](/images/RFAllPlot.png)
## Less Course Variables
#### Regression Partition with method "class".
![image9](/images/RpartLess.png)
#### Pruned Tree
![image10](/images/PruneLess.png)
Importance of varialbes.  
![image11](/images/ImpVarLess.png)
Plot of importance of variables.  
![image12](/images/ImpVarPlot.png)
#### Random Forest
![image13](/images/RFLess.png)
## 5th Semester Variables
#### Random Forest
![image14](/images/FifthSemRF.png). 
![image18](/images/VarPlot.png). 

## Last course taken by students that left the program
The analysis for last CS highest course taken by students was done in three different data sets:
#### All Students that left the CS program
![image15](/images/AllStudentsLeft.png)
#### Students that left the institution
![image16](/images/LeftInst.png)
#### Students that went to other majors in the same institution
![image17](/images/OtherMajor.png)


# Conclusions

536 Students were registered with a CS first major in the 2008-2014 time frame. By Spring 2018, 73.88% of those students graduated, 20.15% left the institution and 5.97% left the CS program and graduated from a different major.

It is important to predict which students are at risk of not graduating in 4 years, of leaving the program, or of leaving the institution and provide the additional support needed to increase the four-year graduation rate. The produced model can be applied when students are starting their 6th semester of the Computer Science program and predict if the student will graduate in four years or not graduate in four years with a 75.74% accuracy.

Considering that the no information rate was 71.8% it is an acceptable result with a Kappa of 0.37. I would like to see a higher accuracy but even if just one extra student is detected, helped, and graduates on time it would be a success.

There is a strong correlation between different CS courses in the sequence but was interesting to find a strong correlation of the MATH201 (Statistics Course) with so may of the CS courses.

With the second data set it was found that most students that leave the program do so after taking the CSCI261 course fallowed by CSCI442, CSCI358, and CSCI262. This information provides insight to the Computer Science Department on doing additional research to figure out why this is. By modifying the class or provide students with additional help on this course student retention may increase.

It was interesting to find the main course variables that affect the 4-year graduation rate and how they correlate with each other. Some CECS courses were important as expected but the MATH201 statistics class was found to be important by every method and we really do not know why this is. Additional research should be done to figure out the reason.

There is a lot more to be done. More questions to to be answered and other angles to be explored. It would be interesting to add more variables to our data set including gender, nationality, instate or out of state tuition, and race.
It would also be interesting to apply the same model and process to other programs course sequences and reach out to students at risk to provide them with additional support.





# References 
Github: [1] (https://github.com/guanegonzalez/MSDS692-Final-Project).   

Github R PDF Files: [2] (https://github.com/guanegonzalez/MSDS692-Final_Project-Vanessa_Gonzalez/tree/master/R_PDF_Files).   

Github R RMD Files: [3] (https://github.com/guanegonzalez/MSDS692-Final_Project-Vanessa_Gonzalez/tree/master/rmd_files).   

Github Presentation in PDf: [4] (https://github.com/guanegonzalez/MSDS692-Final_Project-Vanessa_Gonzalez/tree/master/Presentations). 

Youtube Presentation: [5] (https://youtu.be/eOgN_IJm3YI)








