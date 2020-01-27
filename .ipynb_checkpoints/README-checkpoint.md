# NYC Department of Education Quality Reviews and Surveys

Based on a school's demographics and results on the Quality Reviews and Surveys, predict a school's overall student achievement rating (1-4) and the percentage of students receiving a Level 3 or 4 on the ELA and Math Assessments.

| Features | | | |
|-|-|-|-|
|Enrollment|Supportive Environment Rating|Interesting and challenging curriculum|Effective teaching and learning|
|Effective school assessment|Clear communication - high expectations|Teacher collaboration|Safety, inclusivity, social-emotional growth|
|Resource allocation and management|Identifying, tracking, and meeting goals|Thoughtful teacher development and evaluation|School decision evaluation and adjustment|
|% English Language Learners|% Students with Disabilities|% Self-Contained|Economic Need Index|
|% in Temp Housing|% HRA Eligible|% Asian|% Black|
|% Hispanic|% White|Principal experience at this school|% of teachers with 3+ years of experience|
|Student Attendance Rate|% of Students Chronically Absent|Teacher Attendance Rate|Collaborative Teachers Score|
|Effective School Leadership Score|Rigorous Instruction Score|Strong Family-Community Ties Score|Trust Score|
|Borough|District|

## Question 1: How does a school's environment affect its overall student achievement rating?

I applied machine learning classification algorithms (Random Forest, LightGBM, Logistic Regression, KNN, SVM) using the above features to predict a school's overall student achievement rating into one of the following 4 classes:

1. Does not meet target
2. Approaching target
3. Met target
4. Exceeded target

#### Distribution of students' achivement rating

<img src='Images/student_achiev_dist.png'>

### Findings

|Model|Train Score - F1|Test Score - F1|
|-|-|-|
|Random Forest|0.530|0.598|
|LightGBM|0.525|0.570|
|Logistic Regression|0.508|0.613|
|KNN|0.508|0.547|
|<b>SVM</b>|<b>0.523</b>|<b>0.621</b>|

#### Feature importance in predicting students' achievement rating

<img src='Images/rating_feat_imp.png'>

#### Summary

After running all of the models, SVM Classifier (SVC) resulted with the best score, an F1-score of 0.621. $$F1 = 2 * \frac{Precision * Recall}{Precision + Recall}$$

The following list shows the top 10 features in predicting a school's Student Achievement Rating (1-4). Based on the coefficients from SVM, the features marked with <font color='red'>(-)</font> has a negative relationship with the students' achievement rating: lower values result in a higher rating. Those marked with <font color='blue'>(+)</font> has a positive correlation with the students' achievement rating: higher values result in a higher rating.

1. Student Attendance Rate <font color='blue'>(+)</font>
2. % of Students Chronically Absent <font color='red'>(-)</font>
3. % HRA Eligible <font color='red'>(-)</font>
4. % Hispanic <font color='red'>(-)</font>
5. Economic Need Index <font color='red'>(-)</font>
6. % White <font color='blue'>(+)</font>
7. % Black <font color='red'>(-)</font>
8. Identifying, tracking, and meeting goals <font color='red'>(-)</font>
9. Enrollment <font color='red'>(-)</font>
10. Teacher Collaboration Score <font color='red'>(-)</font>

## Question 2: How does a school's environment affect its students' ELA Assessment scores?

I applied machine learning regression algorithms (Multiple Linear Regression - scikit learn and statsmodels, Ridge Regression, Random Forest, SVM) using the above features to predict a school's percentage of students receiving a Level 3 or 4 on the ELA Assessment.

#### Distribution of the percentage of students receiving Level 3 or 4 on the ELA Assessment

<img src='Images/3+_ela.png'>

### Findings

|Model|Train Score - $R^2$|Test Score - $R^2$|
|-|-|-|
|Multiple Linear Regression|0.832|0.823|
|Ridge Regression|0.831|0.829|
|SVM|0.815|0.811|
|<b>Random Forest</b>|<b>0.803</b>|<b>0.824</b>|

#### Feature importance in predicting ELA assessment scores

<img src='Images/ELA_feat_imp.png'>

#### Summary

After running all of the models, Random Forest Regressor resulted with the best score, an $R^2$ of 82.4%. $$R^2 = \frac{Model Variance}{Total Variance}$$

The following list shows the top 10 features in predicting a school's percentage of students receiving Level 3 or 4 on the ELA assessment. Those marked with <font color='red'>(-)</font> has a negative correlation with the percentage of students receiving Level 3 or 4: lower values of the following result in a higher percentage of Level 3 or 4 students. Those marked with <font color='blue'>(+)</font> has a positive correlation with the percentage of students receiving Level 3 or 4: higher values of the following result in a higher percentage of Level 3 or 4 students.

1. % HRA Eligible <font color='red'>(-)</font>
2. Economic Need Index <font color='red'>(-)</font>
3. % in Temp Housing <font color='red'>(-)</font>
4. Student Attendance Rate <font color='blue'>(+)</font>
5. % of Students Chronically Absent <font color='red'>(-)</font>
6. % White <font color='blue'>(+)</font>
7. % Asian <font color='blue'>(+)</font>
8. % Self-Contained <font color='red'>(-)</font>
9. % Black <font color='red'>(-)</font>
10. % Students with Disabilities <font color='red'>(-)</font>

## Question 3: How does a school's environment affect its students' Math Assessment scores?

I applied machine learning regression algorithms (Multiple Linear Regression - scikit learn and statsmodels, Ridge Regression, Random Forest, SVM) using the above features to predict a school's percentage of students receiving a Level 3 or 4 on the Math Assessment.

#### Distribution of the percentage of students receiving Level 3 or 4 on the Math Assessment

<img src='Images/3+_math.png'>

### Findings

|Model|Train Score - $R^2$|Test Score - $R^2$|
|-|-|-|
|Multiple Linear Regression|0.818|0.793|
|Ridge Regression|0.816|0.800|
|<b>SVM</b>|<b>0.799</b>|<b>0.798</b>|
|Random Forest|0.801|0.786|

#### Feature importance in predicting Math assessment scores

<img src='Images/math_feat_imp.png'>

#### Summary

After running all of the models, Random Forest Regressor resulted with the best score, an $R^2$ of 82.4%.

The following list shows the top 10 features in predicting a school's percentage of students receiving Level 3 or 4 on the Math assessment. Those marked with <font color='red'>(-)</font> has a negative correlation with the percentage of students receiving Level 3 or 4: lower values of the following result in a higher percentage of Level 3 or 4 students. Those marked with <font color='blue'>(+)</font> has a positive correlation with the percentage of students receiving Level 3 or 4: higher values of the following result in a higher percentage of Level 3 or 4 students.

1. % Asian <font color='red'>(-)</font>
2. % Tested <font color='blue'>(+)</font>
3. % Black <font color='red'>(-)</font>
4. Economic Need Index <font color='blue'>(+)</font>
5. % Students with Disabilities <font color='red'>(-)</font>
6. % English Language Learners <font color='red'>(-)</font>
7. Student Attendance Rate <font color='red'>(-)</font>
8. District <font color='red'>(-)</font>
9. Rigorous Instruction Score <font color='red'>(-)</font>
10. % HRA Eligible <font color='blue'>(+)</font>