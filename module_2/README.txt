Goals and objectives of the project

The essence of one of the projects of UNICEF (the international division of the United Nations) is to track the impact of living conditions of students aged 15 to 22 on their academic performance in mathematics in order to identify students at an early stage at risk.
This can be done using the ML model, which would predict the results of the state exam in mathematics for each student in the school.

The aim of this training project is to conduct exploratory data analysis as a preparatory step for the creation of an ML model.

To achieve this goal, you must complete the following tasks:
- Conduct primary analysis and data cleaning.
- Conduct a correlation analysis of numerical data.
- Conduct an analysis of nominative variables.
- Based on the results of the analysis, draw conclusions and prepare a dataset for further use.

Dataset description
Let's look at the variables that the dataset contains:
1 school is the abbreviation for the student's school
2 sex - gender of the student ('F' - female, 'M' - male)
3 age - student's age (from 15 to 22)
4 address - student's address type ('U' - city, 'R' - outside the city)
5 famsize - family size ('LE3' <= 3, 'GT3'> 3)
6 Pstatus - status of joint housing of parents ('T' - live together 'A' - separate)
7 Medu - mother's education (0 - no, 1 - 4 grades, 2 - 5-9 grades, 3 - specialized secondary or 11 grades, 4 - higher)
8 Fedu - father's education (0 - no, 1 - 4 grades, 2 - 5-9 grades, 3 - specialized secondary or 11 grades, 4 - higher)
9 Mjob - mother's work ('teacher' - teacher, 'health' - health sector, 'services' - state service, 'at_home' - not working, 'other' - other)
10 Fjob - father's work ('teacher' - teacher, 'health' - health sector, 'services' - state service, 'at_home' - not working, 'other' - other)
11 reason - reason for choosing a school ('home' - proximity to home, 'reputation' - school reputation, 'course' - educational program, 'other' - other)
12 guardian - guardian ('mother' - mother, 'father' - father, 'other' - other)
13 traveltime - travel time to school (1 - <15 minutes, 2 - 15-30 minutes, 3 - 30-60 minutes, 4 -> 60 minutes)
14 studytime - study time outside of school per week (1 - <2 hours, 2 - 2-5 hours, 3 - 5-10 hours, 4 -> 10 hours)
15 failures - the number of extracurricular failures (n, if 1 <= n <= 3, otherwise 0)
16 schoolsup - additional educational support (yes or no)
17 famsup - family educational support (yes or no)
18 paid - additional paid lessons in mathematics (yes or no)
19 activities - extra extracurricular activities (yes or no)
20 nursery - attended kindergarten (yes or no)
21 higher - wants to get higher education (yes or no)
22 internet - the presence of the Internet at home (yes or no)
23 romantic - in a romantic relationship (yes or no)
24 famrel - family relationships (from 1 - very bad to 5 - very good)
25 freetime - free time after school (from 1 - very little to 5 - a lot)
26 goout - spending time with friends (from 1 - very little to 5 - a lot)
27 health - current state of health (from 1 - very bad to 5 - very good)
28 absences - the number of missed classes
29 score - points on the state exam in mathematics

Stages of work

Import of libraries required for reading and primary analysis
Loading dataset 'stud_math.csv' into stud_math dataframe
Examining data in general
Primary analysis of data in columns
Correlation analysis
Analysis of nominative variables using boxplots
Analysis of nominative variables by Student's test
Selection of variables for the future model
Create stud_for_model dataframe with selected variables
conclusions