# Student Performance Visualization

This project provides a comprehensive analysis and visualization of students' performance in exams using a dataset that includes scores in math, reading, and writing along with demographic information.

## Dataset

The dataset used in this project is `StudentsPerformance.csv`, which contains the following columns:
- `gender`
- `race/ethnicity`
- `parental level of education`
- `lunch`
- `test preparation course`
- `math score`
- `reading score`
- `writing score`

## Analysis and Visualization

The main focus of this project is to analyze and visualize the data to gain insights into students' performance. The key steps and visualizations include:

1. **Data Loading and Overview:**
    - Loaded the dataset using pandas.
    - Displayed the first few rows of the dataset to understand its structure.

2. **Math Score Distribution:**
    - Created a count plot of math scores to visualize the distribution using Seaborn.

3. **Math Pass/Fail Status:**
    - Added a new column `MathPassStatus` to categorize students as "Pass" or "Fail" based on their math scores.
    - Displayed the count of students who passed and failed.

4. **Race/Ethnicity Distribution:**
    - Visualized the distribution of students' race/ethnicity using a pie chart.

5. **Gender Comparison in Math Scores:**
    - Created a count plot to compare math scores between male and female students.

## Code

### Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

### Data Loading

```python
df = pd.read_csv('/kaggle/input/students-performance-in-exams/StudentsPerformance.csv')
df.head()
```

### Math Score Distribution

```python
plt.figure(figsize=(20,10))
sns.countplot(df["math score"])
plt.title("Countplot of Math Score")
plt.show()
```

### Math Pass/Fail Status

```python
df['MathPassStatus'] = np.where(df['math score'] < 40, "Fail", "Pass")
df.MathPassStatus.value_counts()
```

### Race/Ethnicity Distribution

```python
value = df["race/ethnicity"].value_counts().rename_axis('type').reset_index(name='counts')
plt.figure(figsize=(10,10))
plt.pie(value['counts'], labels=value['type'], autopct='%1.2f%%')
plt.show()
```

### Gender Comparison in Math Scores

```python
plt.figure(figsize=(20,10))
sns.countplot(data=df, x=df["math score"], hue=df['gender'])
plt.title("Male and Female Comparison of Marks")
plt.show()
```

## Results

- The distribution of math scores among students.
- The pass/fail status based on math scores.
- The distribution of students across different race/ethnicity groups.
- The comparison of math scores between male and female students.

## Conclusion

This analysis provides valuable insights into the performance of students in exams, highlighting the differences in scores based on gender and race/ethnicity. 
These visualizations can help educators and policymakers make informed decisions to improve educational outcomes.

## License

This project is licensed under the MIT License.
