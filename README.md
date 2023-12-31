# Factorial_ANOVA_ToothGrowth_Dataset
I consider the 'ToothGrowth' data set that is an in-built data set in R. I perform all required steps and finally conduct the Factorial ANOVA test.
### **Introduction to Project:**
This project is a part of Design and Analysis of Experments which is very helpful in analysing a model most efficiently by making different designs out of it. In this project we consider the **ToothGrowth** data set which is available in the base R package. InFactorial designs we consider Independent predictor variables and dependent response variable. The most important point to note is in Factorai design not only the response variable must be continous, but also the predictors variables must be categorical having some number of categories. For example suppose there are 2 categorical variables A and B and each having 2 levels for example say High and No then the design thus obtained is 2^2 factorial design. Here the base 2 denotes the Number of levels in each factor and the power 2 denotes number of independent factors in the design.

Now, the most efficient way to analysis these Factorial designs are to compute the ANOVA table that contains degree of Freedom, Total Sum of Squares , Mean Square and F-Ratio. As this ANOVA table is used to analyse Factorial designs, we name it as Factorial ANOVA. 

### **Project Steps:**

#### 1.Installing and Loading Packages: 
The first step of any project is Installing and Loading the required packages. In this project we use total three packages. They are **tidyverse** , **car** and **emmeans**. 

#### 2. Loading the data set:
As we discussed above, the ToothGrowth Data set is a build in data set in the base R package. So to load this in the R environment we use the **data()** function and name it as toothData as it minimizes the naming error. 

#### 3.Exporting the data:
After loading the data, we can easily make a copy of the data in csv format using the **write_csv()** function that comes under the **tidyverse package** and **tidyverse library**. It makes a copy of the data set in csv format in the same directpry where R works.

#### 4. Basic Data Explanatory Process:
In this step we conduct some basic data exploration works to understand the data more efficiently. This includes-
* Checking the first 5 rows of the data set.
* Getting the column names.
* Checking the number of rows and number of columns.
* Printing the structure if the data set along with type of column elements.
* Getting the Statistical Summary of the data set.

#### **Observation:**
Here we are conducting Factorial ANOVA test. So the predictor variables must be categorical. Here we observe that the predictor variable named dose is not in factor format. So we fisrt convert it the factor format having three levels. Low, Medium and High respectively. Here there are 2 factors and one has 2 levels and the another one has 3 levels. So it is not a generalied 2^k Factorial model. It is a (2*3)=6 factorial models as 6 combinations are possible in this case. 
  
#### 5. Creating the Contingency table:
Then I create a contingency table using the table() function with the supp and dose column of the data set. We also called this table as cross tabulation table. If all the entries of the cross tabulation table are almist equal then we say that the design is balanced or balanced design. In our data set all elemnts are equal to 10 indicating that this is a balanced design. 

#### 6. Visualizing the Distribution of Predictors on Response Variable:
To know the distribution on a avriable with respect to another variables we consider the Box plot. Here we also create three boxplots. They are-

* Distribution of tooth length over supplement used (supp).
* Distribution of tooth length over dosage of medication (dose).
* We alslo consider an interaction term between Supp and Dose to observe any effect on Response variable

#### 7. Interaction Plot:
Here we are considering an interaction term between the supp and dose variable. Interaction plot is very helpful in such cases. This includes the average change in the tooth length in its mean form. We use the with() function to create a box plot and can ciustomize the plot sing different code segments. 

**Note:** When two intercation plots are parallel to each other, we conclude that there is no type interaction effect exsists between the variables. In other hand if the interactions plot intersects each other or tend to intetrsect each other, then we say there is interaction effect between the variables. The dots that we can see on the interaction plot indiactes the mean value of tooth length with respect to each and every combinations. 

#### 8. Assumption for this Test:
There are manily two observations or assumptions that we can make before going to the main project of factorial design. They are-
* All the continuous column should be Normally distributed and
* There will be Homogeneity of Variances between the elements of the design.

#### 9.Checking The Normality of Continuous Response Variable:
It is the first assumption that is to be satisfied to go in the future steps. The most well known test we use for checking Normality is **Shapiro test**. In R we can easily conduct the Shapiro test using the function **shapiro.test()**. In return we get a P-value from this test. Depending on the value, we accept the Null Hypotheis that The data is Normal if P-value is greater than 0.05. And thus we can say that the data is Normally distributed.

#### 10. Checking The Homogeneity of Variance:
Homogeneity of Variances does not mean that all the values respect to each group must have same Variances. It means that the Variances of each group is significantly not different. Now we can find the respevtive Variances using the **with()** and **tapply()** function and using 'var' as an argument. But using this we can not conclude that the Variances we get are Significatly Statistically Differnet or not. For this we use a test called **Bartlett Test**. In R we can conduct this test using the **bartlett.test()** function. This test also gives P-value. If our calculated P-value is grater than 0.05,then we conclude that the Variances of groups are significantly statistically same. 

#### 11. Model Building for This Project:
Now to conduct and construct the test we build the model using the lm() function. Here we consider the len variable as continuous response variable and supp, dose and their interaction term as predictor variables. We name this model as fit_model.

#### 12. Making the ANOVA Table for Data Analysis:
To make the ANOVA table we use the Anova() functuion that comes under the car package. Here we consider the type-III ANOVA which considers the interaction effect. Then we print the summary of the model.

#### 13. Customizing the ANOVA Model:
Now sometimes it is seen that the variables that are significant (Having P-value less than 0.05) are marked by stars. Sometimes this becomes annoying. To delete the stars we can use the **options()** function.

#### 14. Comparison Between the Levels of doses and type of supplement used:
In this step we consider the model called fit_model and compare the model to the dose column , supp column and to theinteraction term. After that we perform Tukey's Test. This is used to find the means that are significantly different from each other. The means are differnet for total 4 samples that we consider in combined method.

