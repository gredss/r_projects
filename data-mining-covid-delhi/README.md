# Time Management, Health, and Well-Being Among Students During the COVID-19 Pandemic

## Overview

This project explores the relationship between time management, health concerns, and social connections among students during the COVID-19 pandemic. It involves statistical and correlation analysis of survey data to identify patterns in student behavior, health, and well-being under lockdown conditions.

## Key Findings

* **Family Connections:** Students who effectively managed their time reported stronger relationships with family, suggesting time management contributes to emotional well-being.
* **Time Management Challenges:** Over half of the respondents (51.44%) struggled with managing their schedules effectively during online learning.
* **Health Issues:** 13.62% of students reported health concerns, underlining the mental and physical toll of the pandemic.
* **Physical Activity:** Exercise was ranked the least favored activity, raising concerns about long-term health implications.
* **Stress Management:** Listening to music and playing online games emerged as common stress-relief methods.
* **No Direct Link Between Activities and Health:** A weak correlation was found between activity duration and reported health issues, indicating multiple influencing factors such as mental health, nutrition, and pre-existing conditions.

## Data Analysis

### 1. Normality Testing

* **Method:** Shapiro-Wilk Test
* **Result:** All numerical variables failed the normality test (p < 0.05), rendering the data unsuitable for Pearson correlation.

```r
shapiro.test(df[[i]])$p.value
```

### 2. Correlation Analysis

* Numerical variables were converted and preprocessed.
* Correlation matrices were computed using `cor()` and visualized using `corrplot`.

#### Key Observations:

* Weak negative correlation between online class duration and health issues.
* Slight positive correlation between total productive time and time utilization.
* Minimal relationship between number of meals and weight change.

```r
cor(num_df[, c("TotalP", "TotalN", "Time_Utilized")])
```

### 3. Categorical Variables Analysis

* **Method:** Chi-Square Test for Independence
* **Purpose:** To examine the association between categorical variables.
* **Significance Level:** 0.05

```r
chisq.test(df[[cat_cols[i]]], df[[cat_cols[j]]])$p.value
```

#### Notable Associations:

* Strong dependency between *Stress Busters* and *Most Missed Things* (p < 0.001).
* Association between *Online Class Rating* and *Time Utilized*.
* Significant correlation between *Time Utilized* and *Connectedness with Family/Friends*.

### 4. Association Metrics

* Contingency tables were used to compute:

  * Chi-square statistics
  * Cramér’s V
  * Percentage distribution for categorical variables

Example:

```r
table(df$OnlineClass_Rating, df$Time_Utilized)
```

## Visualizations

* **Correlation Plots:** Display relationships between quantitative variables.
* **Scatter Plots:** Show trends in weight change vs. number of meals, time utilization vs. productive time.
* **Bar Charts:** (Recommended for categorical frequency comparison; may be included in future enhancements.)

## Conclusion

The analysis reveals the significant impact of time management on students' personal and social lives during the pandemic. Despite limited physical activity and prevalent health concerns, students who structured their schedules efficiently were better able to sustain familial bonds and manage stress. These insights call for targeted support in improving students’ time management skills and promoting physical health.
