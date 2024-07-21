# Exploring Student Data Analysis

### Project Overview
---

This project aims to provide insightful analysis of student performance, parental occupations, and attendance patterns within a local school district. By utilizing collected data, we aim to address key questions such as how students are performing in their math classes, what students’ parents do for work, and how often students are absent from school.

<img src="Screenshot_20-7-2024_234117_www.codecademy.com.jpeg" width="230" /> <img src="Screenshot_20-7-2024_234148_www.codecademy.com.jpeg" width="230" /> <img src="Screenshot_20-7-2024_23418_www.codecademy.com.jpeg" width="230" /> <img src="Screenshot_20-7-2024_23423_www.codecademy.com.jpeg" width="230" />

#### Data Schema

- address: the location of the student’s home ('U' for urban and 'R' for rural)
- absences: the number of times the student was absent during the school year
- Mjob: the student’s mother’s job industry
- Fjob: the student’s father’s job industry
- math_grade: the student’s final grade in math, ranging from 0 to 20


### Data Sources

Student.csv: The primary dataset utilized for the analysis is the "Student.csv" file, which contains student information, including address, absences, mother's job, father's job, and math grade.

### Tools

- Dataset - [Student.csv](students.csv)

- Python - programing insights by implemeting and utalizing python libraries such as matplotlib and seaborn

### Analysis process

In the data cleaning process phase, we performed tasks such as:
1. Loading necessary libraries and importing the data from a CSV file
2. Printing the first few rows of the data for an initial inspection
3. Printing summary statistics for all columns to understand the data distribution
4. Calculating key statistics for the ‘math_grade’ column: Mean, Median, Mode, Range, Standard deviation, Mean Absolute Deviation (MAD)
5. Creating visualizations to explore the data
6. Analyzing categorical data

### Exploratory Data Analysis

##### Questions

- How are students performing in their math classes?

- What do students’ parents do for work?

- How often are students absent from school?

### Data Analysis

```python
# Load libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Import data
students = pd.read_csv('students.csv')

# Print first few rows of data
print(students.head())
# Print summary statistics for all columns
print(students.describe(include='all'))
# Calculate mean
print(students.math_grade.mean())
# Calculate median
print(students.math_grade.median())
# Calculate mode
print(students.math_grade.mode()[0])
# Calculate range
print(students.math_grade.max() - students.math_grade.min())
# Calculate standard deviation
print(students.math_grade.std())
# Calculate MAD
print(students.math_grade.mad())
# Create a histogram of math grades

sns.histplot(x='math_grade',data=students)
plt.show()
plt.clf()

# Create a box plot of math grades

sns.boxplot(x='math_grade',data=students)
plt.show()
plt.clf()

# Calculate number of students with mothers in each job category
print(students.Mjob.value_counts())
# Calculate proportion of students with mothers in each job category
print(students.Mjob.value_counts(normalize=True))
# Create bar chart of Mjob

sns.countplot(x='Mjob',data=students)
plt.show()
plt.clf()

# Create pie chart of Mjob

students.Mjob.value_counts().plot.pie()
plt.show()
plt.clf()

#Extra
students.address.value_counts().plot.pie()
plt.show()
plt.clf()

sns.histplot(x='absences',data=students)
plt.show()
plt.clf()

sns.countplot(x='Fjob',data=students)
plt.show()
plt.clf()
```

### Results

My findings are summarized as follows:
1. Using the data and visuals provided, the overall math grades were not the best of thier acedemic performance, Due to the 25% and 75% quartile of the grade of our boxplot results hovering around a little over 50%.
3. Analyzing father and mother occupations for students, ive concluded mohters and fathers occupations falled into the "other" category.
4. While overlooking student absence data, the overwhelming majority of students have 0 absencse and the amount proceeding that decreases at a significant rate.
### Recommendations

Based on the results formulated from the analysis:

The counties of King, Snohomish, and Pierce have the highest chance of electric vehicle-related engagement.
Focusing on those areas will increase the likelihood of engagement, as EVs are exponentially more prevalent in these regions.

### Limitations
Unfortunately, some rows have missing values that could not be accounted for in certain calculations. Though the number of NULL values wasn't large, there is still data missing from our overall findings. 

### References

Dua, D. and Graff, C. (2019). UCI Machine Learning Repository [http://archive.ics.uci.edu/ml]. 

Irvine, CA: University of California, School of Information and Computer Science. [http://archive.ics.uci.edu/ml/datasets/Student+Performance]

Paulo Cortez, University of Minho, Guimarães, Portugal, [http://www3.dsi.uminho.pt/pcortez]

