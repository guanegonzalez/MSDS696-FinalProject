# MSDS696-FinalProject
Data Science Practicum II Final Project
by Vanessa Gonzalez, August 2018

## Admissions' Yield Prediction by Gender in a Colorado Higher Education Institution.

# Project Overview

The term "Yield" in college admissions is the percent of students who choose to enroll in a particular college or university after having been offered admission. Higher Education Institutions and Institutions with focus in STEM in particular need to have a better handle of the yield between admitted and enroll students. With the need of increasing female population and limited resources the admissions office needs to know what students have a better chance to enroll so they can invest these resources and attention with increased yield rates.

In this case will utilize data from last year (complete cycle) and will be able to increase the data set to two years after Census of Fall 2018. This Colorado university bought a new software called "Slate" two years ago that captures not just the typical variables (race, age, act scores, etc.) from their admissions process but also captures more information like number of contacts with admission's staff, visits to the institution, number of clicks of the website etc. 

We will try to determine which are the variables or combination of variables with higher weight that determine importance by Gender. We will build a predictive model to help admissions utilize resources and attention of their staff more efficiently to increase yield. We will decide on the best model trying different algorithms. 


### Data Sets

The data used was extracted from the Admission's Slate University Database using the Slate application to query the database. Data from Fall 16 to Summer 2017 was used. The full dataset consisted of 11,162 records (number of applications) and 48 variables. A subset was created of just admitted students (6,235 students). This subset of data was used to create predicted models. A second subset of data was created including just female addmited students (2,046). Predictive models were created for this subset as well.

<img src="/Images/AdmittedStudentsGender.png" width="60%">

### Observations on the Quality and Cleaning of the Data

Changes and cleaning were necessary:
* In some variables the NA values were substituted by "Missing" or "None" as appropriate.
* Other NA values were substituted with KNN method.
* In the "State" variable all other states were substituted by "Other" having two outcomes; "CO" or "Other".
* Data types were transformed to appropriate type.
* Factor variables with more than 21 levels were omitted.
* Dummy variables were created for factor variabl es.
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
* Tableau – to clean, format, and combine csv files into two main files. Tableau was also used to create visualizations.
* R – Used to modify, and analyze the two main data sets. R files are located at the Rmd folders.
* A youtube presentation is located at: 

# EDA (Exploratory Data Analysis)

The full dataset was uploaded, summaries, data frames, tables, and plots created using the code in the files attached and Tableau for exploratory analysis and visualization.

<img src="/Images/Bubble.png" width="80%">  
<img src="/Images/PieChart.png" width="70%">  

Bar plots were created for "admitted enrolled" numbers and "admitted enrolled" students divided by gender.
<img src="/Images/BarChart.png" width="70%">. 
<img src="/Images/BarchartWithGender.png" width="70%">. 

![image7](/Images/AdmittedByEthnicity.png). 

Summaries were created.  

![image8](/Images/Summary.png). 

# Analysis
To start the analysis and after the data was cleaned and normalized the variable "Enrolling" was used as the factor to build the predictive models. Of all the students accepted we built models to predict which students have a higher probability of enrolling to the University. After models were built for all students then the model was built just for a subgroup of female students.

## Building the Models in R
Several Libraries were used to perform this task:
* library("mlbench"). 
* library("dplyr"). 
* library("caret"). 
* library("randomForest"). 
* library("lattice"). 
* library("ggplot2"). 
* library("rpart"). 
* library("e1071"). 
* library("stats"). 
* library(relaimpo). 
* library(party). 
* library("kernlab"). 

A Random Forest model was used to determine variable importance, to train, and test the model.A Support Vector Machine (SVM) model was used to compare the accuracy of the Random Forest Model. Four variations of the SVM Model were used:

* SVM with out scaling before model.  
* SVM with Scaling before Model. 
* SVM RBF or Bassian Kernel Model. 
* SVM Polynomial Kernel Model.  

75% of the data was used as the training set and 25% of the data was used as the testing set.

Models were created using all admission's variables and then subsequently variables with less importance were removed. New models were created for this new data set. Several methods were tried to increase accuracy. Size of training set was increased and different number of variables were removed (25 used in the final model). The ideal conditions for accuracy are the ones shown below.

### Random Forest Using All Variables
* Partitions Creation (75%/25%)
* Random Forest for Variable Importance
* Random Forest Method

### Models using less variables
* Partitions Creation (75%/25%)
* Random Forest for Variable Importance

# Analysis Results
Results were produced for Random Forest, Random Forest with 25 variables, and SVM Models:  

#### Random Forest All Variables. 
<img src="/Images/RFAllVariables.png" width="50%">

#### Random Forest Variable Importance. 
<img src="/Images/VariableImpAll.png" width="100%">

#### Random Forest with less Variables. 
<img src="/Images/RFLessVariables.png" width="50%">
 
#### Support Vector Machine (SVM). 
<img src="/Images/SVM.png" width="50%">

#### SVM with out scaling before model. 
<img src="/Images/SVMwoScaling.png" width="30%">

#### SVM with Scaling before Model. 
<img src="/Images/SVMScaling.png" width="50%">

#### SVM RBF or Bassian Kernel Model. 
<img src="/Images/SVMRBF.png" width="50%">

#### SVM Polynomial Kernel Model. 
<img src="/Images/SVMPoly.png" width="50%">
#### Random Forest just for Female Subgroup. 
<img src="/Images/WomenRF.png" width="50%">
#### Variable Importance for Female Subgroup. 
<img src="/Images/Female.png" width="100%">

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








