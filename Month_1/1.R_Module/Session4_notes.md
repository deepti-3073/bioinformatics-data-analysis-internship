# Module 1: R Programming

# Session 4: Data Manipulation, Data Visualisation and Statistical Analysis

## 1. Objectives

By the end of this session, we should be able to:

- Manipulate datasets using `dplyr`.
- Filter, select, transform and summarise data.
- Create visualisations using `ggplot2`.
- Calculate descriptive statistics.
- Perform hypothesis testing.
- Understand and perform a two-sample t-test.
- Build simple linear regression models.
- Interpret statistical outputs.

## 2. Topics Covered

1. Data types in R
2. Accessing function documentation
3. Tidyverse
4. Data manipulation using dplyr
5. Pipe operator `%>%`
6. Data visualisation using ggplot2
7. Descriptive statistics
8. Hypothesis testing
9. Two-sample t-test
10. Linear regression

---

# PART A: INTRODUCTION TO DATA TYPES AND TIDYVERSE

## 3. Common Data Types in R

R supports different data types to represent different kinds of information.

| Data type | Description | Example |
|---|---|---|
| Numeric | Represents numerical values, including decimal numbers | `10.5`, `25` |
| Integer | Represents whole numbers | `10L`, `25L` |
| Character | Represents text or strings | `"GeneA"` |
| Logical | Represents TRUE or FALSE | `TRUE`, `FALSE` |
| Factor | Represents categorical variables | `"Control"`, `"Drug A"` |
| Complex | Represents complex numbers | `2 + 3i` |

### Example

```r
a <- 10.5
b <- 10L
c <- "BRCA1"
d <- TRUE
e <- factor("Control")

class(a)
class(b)
class(c)
class(d)
class(e)
```

**Important:**

- Numeric values are used for measurements and calculations.
- Character values are used for names and text.
- Logical values are used for conditions.
- Factors are used to represent categories or groups.

---

## 4. Accessing Function Documentation in R

R provides built-in documentation for functions.

It explains:
- What the function does.
- Its syntax and arguments.
- How to use it.
- Examples of its usage.
- The output it produces.

### Method 1: Using the Question Mark (`?`)

```r
?mean
```

Displays the documentation for the `mean()` function.

### Method 2: Using help()

```r
help(mean)
```

This also opens the documentation for the `mean()` function.

### Method 3: Searching Documentation

```r
help.search("regression")
```

Searches the installed documentation for topics related to regression.

### Where to use

- When learning a new R function.
- When unsure about function arguments.
- When troubleshooting code.
- When exploring packages and their functions.

---

# PART B: TIDYVERSE AND DATA MANIPULATION

## 5. Tidyverse

### Definition

- Tidyverse is a collection of R packages used for data manipulation, visualisation and analysis.
- It provides a consistent and readable approach to working with datasets.
- It is widely used for data cleaning, transformation and visualisation.

### Important Tidyverse Packages

| Package | Purpose |
|---|---|
| dplyr | Data manipulation |
| ggplot2 | Data visualisation |
| tidyr | Data cleaning and reshaping |
| readr | Reading rectangular data files |
| tibble | Working with modern data frames |
| stringr | String manipulation |
| forcats | Working with categorical variables (factors) |

### Installing Tidyverse

Installation is required only once for a given R library.

```r
install.packages("tidyverse")
```

### Loading Tidyverse

```r
library(tidyverse)
```

This makes the core tidyverse packages available in the current R session.

**Important difference:**

- `install.packages()` installs a package.
- `library()` loads an installed package for use.

---

## 6. Data Manipulation Using dplyr

### Definition

- `dplyr` is a package in the tidyverse used for data manipulation.
- It provides functions to clean, filter, select, transform and summarise datasets.
- It makes data manipulation more readable and efficient.

### Main Functions in dplyr

| Function | Purpose |
|---|---|
| `filter()` | Selects rows based on conditions |
| `select()` | Selects specific columns |
| `mutate()` | Creates or modifies columns |
| `arrange()` | Sorts rows |
| `group_by()` | Groups data based on categories |
| `summarise()` | Calculates summary statistics |
| `rename()` | Renames columns |
| `distinct()` | Removes duplicate rows or values |
| `count()` | Counts observations in groups |

### Example Dataset

We will use a gene expression dataset throughout this section.

```r
gene_data <- data.frame(
  Gene = c("Gene1", "Gene2", "Gene3", "Gene4", "Gene5", "Gene6"),
  Treatment = c("Control", "Control", "Drug A", "Drug A", "Drug B", "Drug B"),
  Expression_level = c(10, 22, 24, 22, 45, 17)
)

gene_data$Treatment <- as.factor(gene_data$Treatment)

print(gene_data)
```

**Output:**

```text
   Gene Treatment Expression_level
1 Gene1   Control               10
2 Gene2   Control               22
3 Gene3    Drug A               24
4 Gene4    Drug A               22
5 Gene5    Drug B               45
6 Gene6    Drug B               17
```

This dataset contains:
- Gene: Gene identification.
- Treatment: Experimental treatment group.
- Expression_level: Gene expression measurement.

---

## 7. Pipe Operator (`%>%`)

### Definition

- The pipe operator `%>%` passes the result of one operation into the next operation.
- It allows multiple data manipulation steps to be written in sequence.
- It improves readability by creating a step-by-step workflow.

### Syntax

```r
data %>%
  function1() %>%
  function2() %>%
  function3()
```

### Example 1: Without Pipe Operator

```r
select(
  filter(gene_data, Treatment == "Control"),
  Expression_level
)
```

### Example 2: With Pipe Operator

```r
gene_data %>%
  filter(Treatment == "Control") %>%
  select(Expression_level)
```

**Output:**

```text
  Expression_level
1               10
2               22
```

### Explanation

1. Start with `gene_data`.
2. `filter()` selects only the Control treatment rows.
3. `select()` keeps only the Expression_level column.
4. The final result is displayed.

### Advantages

- Makes code easier to read.
- Allows multiple operations to be connected.
- Reduces deeply nested function calls.
- Helps organise data analysis workflows.

**Important:** The pipe passes the result of one step to the next step. The order of operations matters.

---

# PART C: IMPORTANT dplyr FUNCTIONS

## 8. filter()

### Definition

- `filter()` selects rows based on one or more conditions.
- It is used to extract observations that satisfy specific criteria.
- It is particularly useful for data cleaning and targeted analysis.

### Syntax

```r
filter(data, condition)
```

### Example 1: Filtering by a Category

```r
gene_data %>%
  filter(Treatment == "Control")
```

Returns only the rows belonging to the Control group.

### Example 2: Filtering by a Numerical Condition

```r
gene_data %>%
  filter(Expression_level > 20)
```

Returns only rows where expression is greater than 20.

### Example 3: Filtering Using Multiple Conditions

```r
gene_data %>%
  filter(Treatment == "Drug A" & Expression_level > 20)
```

Returns Drug A observations with expression greater than 20.

### Example 4: Filtering Using OR

```r
gene_data %>%
  filter(Treatment == "Control" | Treatment == "Drug A")
```

Returns observations belonging to either Control or Drug A.

### Example 5: Filtering Using %in%

```r
gene_data %>%
  filter(Treatment %in% c("Control", "Drug A"))
```

`%in%` checks whether values belong to a specified collection.

This is useful when filtering multiple categories.

### Where to use

- Selecting specific treatment groups.
- Identifying samples with high gene expression.
- Removing unwanted observations.
- Extracting specific experimental conditions.
- Selecting samples for statistical testing.

---

## 9. select()

### Definition

- `select()` is used to choose specific columns from a dataset.
- It displays only the selected variables.
- It improves clarity and can reduce the amount of data carried through subsequent steps.

### Syntax

```r
select(data, column_names)
```

### Example 1: Selecting One Column

```r
gene_data %>%
  select(Expression_level)
```

Displays only the Expression_level column.

### Example 2: Selecting Multiple Columns

```r
gene_data %>%
  select(Gene, Expression_level)
```

Displays Gene and Expression_level.

### Example 3: Excluding a Column

```r
gene_data %>%
  select(-Gene)
```

Displays all columns except Gene.

### Example 4: Selecting Columns by Position

```r
gene_data %>%
  select(1, 3)
```

Selects the first and third columns.

### Where to use

- Selecting only relevant variables for analysis.
- Extracting gene expression measurements.
- Preparing data for plotting.
- Simplifying large datasets.

---

## 10. mutate()

### Definition

- `mutate()` is used to create new columns or modify existing columns in a data frame.
- It is commonly used for mathematical transformations.
- It is useful for generating derived variables.

### Syntax

```r
mutate(data, new_column = expression)
```

### Example 1: Creating a New Column

```r
gene_data %>%
  mutate(Log_Expression = log(Expression_level))
```

Creates a new column containing the natural logarithm of the expression values.

### Example 2: Calculating Squared Values

```r
gene_data %>%
  mutate(Squared_Expression = Expression_level^2)
```

Creates a column containing squared expression values.

### Example 3: Classifying Gene Expression

```r
gene_data %>%
  mutate(Expression_Status =
    ifelse(Expression_level >= 20, "High", "Low"))
```

Creates a new column classifying expression as High or Low.

### Example 4: Modifying an Existing Column

```r
gene_data %>%
  mutate(Expression_level = Expression_level * 2)
```

Multiplies all expression values by two in the returned data frame.

### Where to use

- Log transformation of expression values.
- Normalisation and mathematical transformations.
- Creating new variables.
- Categorising biological measurements.
- Preparing datasets for statistical analysis.

**Important:** `mutate()` returns a modified data frame. To save the changes permanently, assign the result to an object.

```r
gene_data <- gene_data %>%
  mutate(Log_Expression = log(Expression_level))
```

---

## 11. arrange()

### Definition

- `arrange()` sorts rows according to one or more columns.
- By default, it sorts in ascending order.

### Example 1: Ascending Order

```r
gene_data %>%
  arrange(Expression_level)
```

Sorts samples from the lowest to highest expression.

### Example 2: Descending Order

```r
gene_data %>%
  arrange(desc(Expression_level))
```

Sorts samples from the highest to lowest expression.

### Where to use

- Identifying samples with the highest expression.
- Ranking genes based on measurements.
- Organising numerical datasets.

---

## 12. group_by() and summarise()

These two functions are frequently used together to compare groups.

### group_by()

**Definition:**

- `group_by()` groups observations based on one or more categorical variables.
- It allows calculations to be performed separately for each group.
- It is useful for comparing experimental conditions.

### summarise()

**Definition:**

- `summarise()` calculates summary statistics.
- It reduces each group to one or more summary values.
- It can calculate mean, median, standard deviation, count and other statistics.

### Syntax

```r
data %>%
  group_by(category) %>%
  summarise(summary_name = function(variable))
```

### Example: Calculating Mean Gene Expression by Treatment

```r
gene_data %>%
  group_by(Treatment) %>%
  summarise(
    Mean_Expression = mean(Expression_level)
  )
```

**Output:**

```text
  Treatment Mean_Expression
1    Control             16
2     Drug A             23
3     Drug B             31
```

### Explanation

1. `group_by(Treatment)` separates observations into Control, Drug A and Drug B groups.
2. `summarise()` calculates the mean expression for each group.
3. The final result contains one mean value for each treatment.

### Example 2: Calculating Mean and Standard Deviation

```r
gene_data %>%
  group_by(Treatment) %>%
  summarise(
    Mean_Expression = mean(Expression_level),
    SD_Expression = sd(Expression_level),
    Sample_Count = n()
  )
```

### Example 3: Counting Observations

```r
gene_data %>%
  group_by(Treatment) %>%
  summarise(
    Total_Samples = n()
  )
```

### Interpretation

The mean expression values are:

| Treatment | Mean expression |
|---|---:|
| Control | 16 |
| Drug A | 23 |
| Drug B | 31 |

- Drug B has the highest mean expression.
- Drug A has a higher mean than Control.
- This suggests possible differences between treatment groups.
- Statistical testing is required to determine whether the observed differences are statistically significant.

### Where to use

- Comparing gene expression across treatments.
- Comparing bacterial growth across experimental conditions.
- Calculating average measurements per group.
- Summarising clinical or laboratory datasets.

**Important:** A difference in group means does not automatically mean that the difference is statistically significant.

---

# PART D: DATA VISUALISATION USING ggplot2

## 13. ggplot2

### Definition

- `ggplot2` is a data visualisation package in R.
- The name gg refers to Grammar of Graphics.
- It creates graphs by combining different graphical components.
- It follows a layer-by-layer approach to constructing plots.

### Main Components of ggplot2

A basic ggplot is constructed using:

```r
ggplot(data, aes()) + geom_function()
```

### Understanding the Structure

| Component | Purpose |
|---|---|
| `ggplot()` | Initialises the plot |
| `data` | Specifies the dataset |
| `aes()` | Defines aesthetic mappings |
| `geom_*()` | Defines the type of graph |
| `labs()` | Adds labels and titles |
| `theme()` | Changes plot appearance |

### What is aes()?

`aes()` stands for aesthetics.

It specifies how variables in the dataset are mapped to visual properties such as:

- X-axis.
- Y-axis.
- Colour.
- Shape.
- Size.

### Example

```r
ggplot(mtcars, aes(x = mpg, y = hp))
```

This specifies:
- X-axis: mpg.
- Y-axis: hp.
- Dataset: mtcars.

A geometry layer is then added to display the actual graph.

---

## 14. Scatter Plot

### Definition

- A scatter plot displays the relationship between two continuous numerical variables.
- Each point represents an observation.
- It helps identify trends, relationships and correlation patterns.
- It is useful for regression analysis.

### Syntax

```r
ggplot(data, aes(x = variable1, y = variable2)) +
  geom_point()
```

### Example: Relationship Between Mileage and Horsepower

```r
ggplot(mtcars, aes(x = mpg, y = hp)) +
  geom_point()
```

### Explanation

- `mtcars` is the dataset.
- `aes(x = mpg, y = hp)` maps mileage to the X-axis and horsepower to the Y-axis.
- `geom_point()` displays individual observations as points.

### Example 2: Gene Expression Across Two Measurements

```r
ggplot(gene_data, aes(x = Expression_level, y = Expression_level)) +
  geom_point()
```

This example simply plots expression against itself. It is not useful for studying a biological relationship, but demonstrates the syntax.

For a meaningful relationship, use two different continuous variables, for example:

```r
experiment_data <- data.frame(
  Concentration = c(1, 2, 3, 4, 5),
  Expression = c(5, 8, 12, 15, 20)
)

ggplot(experiment_data,
       aes(x = Concentration, y = Expression)) +
  geom_point()
```

### Where to use

- Studying relationships between gene expression and concentration.
- Analysing bacterial growth against time.
- Studying relationships between two numerical measurements.
- Exploring trends before regression analysis.

---

## 15. Bar Plot

### Definition

- A bar plot compares values across different categories.
- It displays differences in magnitude between groups.
- It is useful for comparing group-level measurements.

### Syntax

```r
ggplot(data, aes(x = category, y = value)) +
  geom_col()
```

### Example: Comparing Mean Expression Across Treatments

First, calculate the group means.

```r
mean_data <- gene_data %>%
  group_by(Treatment) %>%
  summarise(
    Mean_Expression = mean(Expression_level)
  )
```

Then create the bar plot.

```r
ggplot(mean_data,
       aes(x = Treatment, y = Mean_Expression)) +
  geom_col()
```

### Explanation

- `Treatment` is mapped to the X-axis.
- `Mean_Expression` is mapped to the Y-axis.
- `geom_col()` displays the supplied mean values as bar heights.

### Difference Between geom_bar() and geom_col()

| Function | Purpose |
|---|---|
| `geom_bar()` | Counts observations by default |
| `geom_col()` | Uses values already present in the dataset |

The following is also valid when using `geom_bar()` with pre-calculated values:

```r
ggplot(mean_data,
       aes(x = Treatment, y = Mean_Expression)) +
  geom_bar(stat = "identity")
```

`stat = "identity"` tells ggplot2 to use the supplied Y values instead of counting observations.

### Where to use

- Comparing mean gene expression across treatment groups.
- Comparing average bacterial growth.
- Comparing sample counts.
- Comparing measurements across categories.

---

## 16. Box Plot

### Definition

- A box plot displays the distribution of numerical data across groups.
- It shows the median, quartiles, spread and potential outliers.
- It is useful for comparing distributions between experimental conditions.
- It is often used before hypothesis testing.

### Syntax

```r
ggplot(data, aes(x = category, y = value)) +
  geom_boxplot()
```

### Example: Comparing Gene Expression Across Treatments

```r
ggplot(gene_data,
       aes(x = Treatment, y = Expression_level)) +
  geom_boxplot()
```

### Components of a Box Plot

A standard box plot contains:

1. Median (Q2): The middle value of the dataset.
2. First quartile (Q1): The 25th percentile.
3. Third quartile (Q3): The 75th percentile.
4. Interquartile range (IQR): The difference between Q3 and Q1.
5. Whiskers: Extend to the most extreme observations within the usual 1.5 × IQR rule.
6. Outliers: Individual observations beyond the whisker limits.

### Understanding the Box Plot

- The line inside the box represents the median.
- The bottom of the box represents Q1.
- The top of the box represents Q3.
- The box represents the middle 50% of the observations.
- Points outside the whiskers are potential outliers.

### Where to use

- Comparing expression distributions across treatments.
- Identifying variation between groups.
- Detecting potential outliers.
- Examining distributions before statistical testing.

**Important:** A box plot helps visualise differences but does not independently establish statistical significance.

---

## 17. Other Useful ggplot2 Components

### Adding a Title and Axis Labels

The `labs()` function adds labels and titles.

```r
ggplot(gene_data,
       aes(x = Treatment, y = Expression_level)) +
  geom_boxplot() +
  labs(
    title = "Gene Expression Across Treatments",
    x = "Treatment Group",
    y = "Expression Level"
  )
```

### Changing the Plot Theme

```r
ggplot(gene_data,
       aes(x = Treatment, y = Expression_level)) +
  geom_boxplot() +
  theme_minimal()
```

Other useful themes include:

- `theme_classic()`
- `theme_bw()`
- `theme_light()`
- `theme_dark()`

### Adding Colour

```r
ggplot(gene_data,
       aes(x = Treatment,
           y = Expression_level,
           fill = Treatment)) +
  geom_boxplot()
```

This assigns a fill colour according to the treatment group.

---

# PART E: DESCRIPTIVE STATISTICS

## 18. Descriptive Statistics

### Definition

- Descriptive statistics are used to summarise and describe the characteristics of a dataset.
- They help understand the central tendency and variability of the data.
- They are commonly calculated before performing inferential statistical tests.

Two important measures covered in this session are:

1. Mean.
2. Standard deviation.

---

## 19. Mean

### Definition

- Mean is the average value of a dataset.
- It is a measure of central tendency.
- It is calculated by adding all observations and dividing by the number of observations.

### Formula

\[
\text{Mean} = \frac{\sum x_i}{n}
\]

Where:

- \(x_i\) = Individual observations.
- \(n\) = Total number of observations.

### Example

```r
expression <- c(10, 20, 30, 40, 50)

mean(expression)
```

**Output:**

```text
[1] 30
```

### Calculating Mean from a Data Frame

```r
mean(gene_data$Expression_level)
```

### Calculating Mean by Treatment

```r
gene_data %>%
  group_by(Treatment) %>%
  summarise(
    Mean_Expression = mean(Expression_level)
  )
```

### Where to use

- Calculating average gene expression.
- Calculating average bacterial growth.
- Comparing average experimental measurements.
- Summarising numerical observations.

---

## 20. Standard Deviation (SD)

### Definition

- Standard deviation measures the variability or spread of data around the mean.
- It indicates how much individual observations differ from the average.
- A smaller standard deviation indicates that values are closer to the mean.
- A larger standard deviation indicates greater variation.

### Example 1

```r
expression <- c(10, 10, 10, 10, 10)

sd(expression)
```

**Output:**

```text
[1] 0
```

All values are identical, so there is no variation.

### Example 2

```r
expression <- c(5, 10, 15, 20, 25)

sd(expression)
```

This produces a larger standard deviation because the values are more spread out.

### Calculating SD from a Data Frame

```r
sd(gene_data$Expression_level)
```

### Calculating SD for Each Treatment

```r
gene_data %>%
  group_by(Treatment) %>%
  summarise(
    SD_Expression = sd(Expression_level)
  )
```

### Important Points

- Mean describes central tendency.
- Standard deviation describes variability.
- Both are commonly reported together.
- R's `sd()` calculates the sample standard deviation using \(n-1\) in the denominator.

### Handling Missing Values

If the dataset contains `NA`, use:

```r
mean(gene_data$Expression_level, na.rm = TRUE)
```

```r
sd(gene_data$Expression_level, na.rm = TRUE)
```

`na.rm = TRUE` tells R to remove missing values before calculating the result.

---

# PART F: HYPOTHESIS TESTING

## 21. Hypothesis Testing

### Definition

- Hypothesis testing is a statistical method used to determine whether there is sufficient evidence to support a claim about a population.
- It is used to evaluate whether observed differences or relationships are likely to reflect more than random sampling variation.
- It is commonly used in biological experiments to compare treatment groups.

### Example

Suppose we want to determine whether Drug A changes gene expression compared with a Control group.

We collect expression measurements from both groups and compare their means.

We formulate two hypotheses.

### Null Hypothesis (H0)

- States that there is no difference or effect.
- In a two-group comparison, it usually states that the population means are equal.

\[
H_0: \mu_1 = \mu_2
\]

### Alternative Hypothesis (H1)

- States that there is a difference or effect.
- For a two-sided test, it states that the population means are not equal.

\[
H_1: \mu_1 \neq \mu_2
\]

### Understanding the Two Hypotheses

| Hypothesis | Meaning |
|---|---|
| H0 | No difference between the population means |
| H1 | A difference exists between the population means |

### Why Hypothesis Testing Is Needed

Suppose:

- Control mean expression = 16.
- Drug A mean expression = 23.

Drug A has a higher observed mean.

However, this does not automatically prove that Drug A causes a significant increase in gene expression.

Statistical testing is required to assess whether the observed difference provides sufficient evidence against the null hypothesis.

---

## 22. Two-Sample t-Test

### Definition

- A two-sample t-test compares the means of two groups.
- It determines whether there is sufficient evidence of a difference between the population means.
- It is commonly used when comparing two experimental conditions.

### Example

We want to compare gene expression between:

- Control.
- Drug A.

### Hypotheses

\[
H_0: \mu_{\text{Control}} = \mu_{\text{Drug A}}
\]

\[
H_1: \mu_{\text{Control}} \neq \mu_{\text{Drug A}}
\]

### Assumptions of a Two-Sample t-Test

1. The observations are independent between groups.
2. The data are approximately normally distributed within each group, particularly important for small samples.
3. The outcome variable is numerical.
4. The groups are independent for an independent two-sample t-test.

**Additional note:**

R's default `t.test()` uses Welch's two-sample t-test. It does not assume equal population variances.

A classical Student's two-sample t-test assumes equal variances.

### Step 1: Create a Subset of the Data

```r
subset_data <- subset(
  gene_data,
  Treatment %in% c("Control", "Drug A")
)
```

**Explanation:**

- `subset()` selects observations from a dataset.
- `gene_data` is the original dataset.
- `Treatment %in% c("Control", "Drug A")` selects observations belonging to either Control or Drug A.
- The selected observations are stored in `subset_data`.

### Step 2: Perform the t-Test

```r
t.test(
  Expression_level ~ Treatment,
  data = subset_data
)
```

### Understanding the Formula

```r
Expression_level ~ Treatment
```

- `Expression_level` is the numerical response variable.
- `Treatment` is the grouping variable.
- `data = subset_data` specifies the dataset used for the test.

The `~` symbol separates the response variable from the grouping variable in this formula.

### Step 3: Understand the Output

The t-test output commonly contains:

| Output | Meaning |
|---|---|
| t-value | Test statistic calculated by the t-test |
| df | Degrees of freedom |
| p-value | Probability of obtaining a result at least as extreme as the observed result under H0 |
| Confidence interval | Estimated range for the difference in population means |
| Mean of each group | Sample means for the compared groups |

### Understanding the p-Value

The p-value helps determine whether the observed data provide sufficient evidence against the null hypothesis.

A commonly used significance level is:

\[
\alpha = 0.05
\]

| p-value | Interpretation |
|---|---|
| p < 0.05 | Statistically significant evidence against H0 |
| p >= 0.05 | Insufficient evidence to reject H0 |

### Example Interpretation

If the t-test produces:

```text
p-value = 0.03
```

Since:

\[
0.03 < 0.05
\]

We reject the null hypothesis at the 5% significance level.

There is statistically significant evidence of a difference in mean expression between the two groups.

If the p-value is 0.10:

\[
0.10 > 0.05
\]

We fail to reject the null hypothesis.

This does not prove that the groups are identical. It means there is insufficient evidence to establish a difference at the chosen significance level.

**Important:**

- A p-value is not the probability that the null hypothesis is true.
- Statistical significance does not necessarily mean biological importance.
- A statistically significant difference does not establish causation by itself.

---

## 23. Difference Between t-Test and ANOVA

### t-Test

- Used to compare the means of two groups.
- Example: Control versus Drug A.

### ANOVA

- Used to compare the means of three or more groups.
- Example: Control, Drug A and Drug B.

### Comparison

| Feature | t-Test | ANOVA |
|---|---|---|
| Main purpose | Compare two group means | Compare three or more group means |
| Example | Control vs Drug A | Control vs Drug A vs Drug B |
| R function | `t.test()` | `aov()` |
| Main result | t-statistic and p-value | F-statistic and p-value |

### Example: One-Way ANOVA

```r
model <- aov(
  Expression_level ~ Treatment,
  data = gene_data
)

summary(model)
```

ANOVA tests whether there is evidence that at least one group mean differs from the others.

If the ANOVA result is significant, further post-hoc comparisons may be required to identify which groups differ.

**Note:** ANOVA was mentioned in the lecture as a method for comparing more than two groups and will be covered in more detail later.

---

# PART G: LINEAR REGRESSION

## 24. Linear Regression

### Definition

- Linear regression is a statistical method used to model the relationship between a predictor variable and a response variable.
- It estimates how changes in one variable are associated with changes in another variable.
- It is used to understand and predict relationships between numerical variables.

### Important Variables

**Independent variable / Predictor (X):**

- The variable used to explain or predict changes in another variable.

**Dependent variable / Response (Y):**

- The variable whose value is being explained or predicted.

### Example

Suppose we want to investigate whether engine horsepower affects fuel efficiency.

- Horsepower (hp) = Predictor variable.
- Miles per gallon (mpg) = Response variable.

### Linear Regression Equation

\[
Y = \beta_0 + \beta_1X + \epsilon
\]

Where:

- \(Y\) = Response variable.
- \(X\) = Predictor variable.
- \(\beta_0\) = Intercept.
- \(\beta_1\) = Regression coefficient or slope.
- \(\epsilon\) = Error term.

### Understanding the Coefficient

The regression coefficient indicates the direction and magnitude of the estimated relationship.

**Positive coefficient:**

- As X increases, the predicted value of Y increases.

**Negative coefficient:**

- As X increases, the predicted value of Y decreases.

**Zero coefficient:**

- The fitted linear relationship has no slope.

---

## 25. Building a Linear Regression Model in R

R uses the `lm()` function to build linear regression models.

### Syntax

```r
model <- lm(response_variable ~ predictor_variable, data = dataset)
```

### Example: mtcars Dataset

R includes a built-in dataset called `mtcars`.

It contains information about different car models.

Some important columns include:

| Variable | Meaning |
|---|---|
| mpg | Miles per gallon |
| hp | Horsepower |
| wt | Weight |
| cyl | Number of cylinders |
| disp | Engine displacement |

### Step 1: Explore the Dataset

```r
data(mtcars)

head(mtcars)
str(mtcars)
```

### Step 2: Create a Linear Regression Model

```r
model <- lm(mpg ~ hp, data = mtcars)
```

### Explanation

- `model` stores the fitted regression model.
- `lm()` stands for linear model.
- `mpg` is the response variable.
- `hp` is the predictor variable.
- `data = mtcars` specifies the dataset.

The model investigates the relationship between horsepower and fuel efficiency.

### Step 3: Display the Model Summary

```r
summary(model)
```

The summary provides information about the fitted model, including:

- Residuals.
- Regression coefficients.
- Standard errors.
- t-values.
- p-values.
- F-statistic.
- R-squared.
- Adjusted R-squared.

---

## 26. Understanding Linear Regression Output

### 1. Residuals

- Residuals are the differences between observed values and values predicted by the model.
- They represent the prediction errors for individual observations.

\[
Residual = Observed\ Value - Predicted\ Value
\]

The summary displays a five-number summary of the residuals:

| Value | Meaning |
|---|---|
| Min | Minimum residual |
| 1Q | First quartile |
| Median | Median residual |
| 3Q | Third quartile |
| Max | Maximum residual |

### 2. Regression Coefficient

The coefficient indicates how much the predicted response changes for a one-unit increase in the predictor.

In the model:

```r
model <- lm(mpg ~ hp, data = mtcars)
```

The coefficient of `hp` represents the estimated change in mpg for each additional unit of horsepower.

**Interpretation:**

- Positive coefficient: Predicted mpg increases as horsepower increases.
- Negative coefficient: Predicted mpg decreases as horsepower increases.

### 3. Standard Error

- Standard error measures the uncertainty in an estimated regression coefficient.
- Smaller standard errors indicate more precise coefficient estimates, all else being equal.

### 4. t-Value

- The t-value is calculated by dividing the estimated coefficient by its standard error.
- It is used to test whether the coefficient differs from zero.

### 5. p-Value

- The p-value evaluates the evidence against the null hypothesis that the regression coefficient is zero.
- A p-value below 0.05 is commonly considered statistically significant.

For example:

\[
p < 0.05
\]

This indicates statistically significant evidence of a non-zero linear association between the predictor and response, under the model assumptions.

### 6. F-Statistic

- The F-statistic evaluates whether the regression model provides explanatory power compared with a model containing only an intercept.
- In simple linear regression with one predictor, this test is equivalent to the squared t-test for the slope.

### 7. R-Squared (R²)

### Definition

- R-squared measures the proportion of variation in the response variable explained by the fitted regression model.
- It ranges from 0 to 1 in the usual regression setting with an intercept.

### Example

Suppose:

\[
R^2 = 0.60
\]

This means that approximately 60% of the observed variation in the response variable is explained by the fitted model.

The remaining variation is not explained by the model.

**Important:** R-squared does not prove causation or establish that the model is appropriate.

### 8. Adjusted R-Squared

- Adjusted R-squared modifies R-squared by accounting for the number of predictor variables in the model.
- It penalises adding predictors that do not meaningfully improve model fit.
- It is particularly useful when comparing models with different numbers of predictors.

---

## 27. Visualising Linear Regression

A regression line can be added to a scatter plot using `geom_smooth()`.

### Example

```r
ggplot(mtcars, aes(x = hp, y = mpg)) +
  geom_point() +
  geom_smooth(method = "lm", se = TRUE)
```

### Explanation

- `geom_point()` displays the observations.
- `geom_smooth(method = "lm")` adds a fitted linear regression line.
- `se = TRUE` displays the confidence band around the fitted line.

### Where to use Linear Regression

- Studying the relationship between gene expression and concentration.
- Analysing bacterial growth in relation to incubation time.
- Studying relationships between biological measurements.
- Predicting numerical outcomes using predictor variables.
- Investigating associations between experimental variables.

**Important:** Linear regression describes an association. A causal interpretation requires an appropriate experimental design and additional justification.

---

# PART H: QUICK REVISION

## 28. Important Functions to Remember

| Function | Purpose |
|---|---|
| `install.packages()` | Installs an R package |
| `library()` | Loads an installed package |
| `?function_name` | Opens function documentation |
| `help()` | Opens function documentation |
| `%>%` | Passes output to the next operation |
| `filter()` | Filters rows |
| `select()` | Selects columns |
| `mutate()` | Creates or modifies columns |
| `arrange()` | Sorts rows |
| `group_by()` | Groups observations |
| `summarise()` | Calculates summary statistics |
| `mean()` | Calculates mean |
| `sd()` | Calculates standard deviation |
| `ggplot()` | Initialises a plot |
| `aes()` | Maps variables to visual properties |
| `geom_point()` | Creates a scatter plot |
| `geom_col()` | Creates bars using supplied values |
| `geom_bar()` | Creates bars using counts by default |
| `geom_boxplot()` | Creates a box plot |
| `labs()` | Adds titles and labels |
| `t.test()` | Performs a t-test |
| `aov()` | Performs analysis of variance |
| `lm()` | Fits a linear regression model |
| `summary()` | Summarises an object or statistical model |

---

## 29. Difference Between Descriptive and Inferential Statistics

| Descriptive Statistics | Inferential Statistics |
|---|---|
| Summarises the available data | Uses sample data to draw conclusions about a population |
| Describes central tendency and spread | Tests hypotheses and estimates population relationships |
| Examples: Mean, median, SD | Examples: t-test, ANOVA, regression |

---

## 30. Important Concepts to Explain in an Exam or Interview

1. What is Tidyverse?
2. What is dplyr and why is it used?
3. What is the purpose of the pipe operator `%>%`?
4. What is the difference between `filter()` and `select()`?
5. What is the purpose of `mutate()`?
6. What is the difference between `group_by()` and `summarise()`?
7. What is ggplot2?
8. What is the Grammar of Graphics?
9. What is the purpose of `aes()`?
10. What is the difference between scatter plots, bar plots and box plots?
11. What is the difference between `geom_bar()` and `geom_col()`?
12. What are descriptive statistics?
13. What is the difference between mean and standard deviation?
14. What is hypothesis testing?
15. What is the difference between H0 and H1?
16. What is a two-sample t-test?
17. What is a p-value?
18. What is the difference between a t-test and ANOVA?
19. What is linear regression?
20. What are predictor and response variables?
21. What is the purpose of the `lm()` function?
22. What do regression coefficients represent?
23. What is R-squared?
24. What is adjusted R-squared?
25. What is the difference between descriptive and inferential statistics?

---

## 31. Session 4 Completion Checklist

### Data Manipulation

- [ ] Understand Tidyverse.
- [ ] Install and load packages.
- [ ] Access R documentation.
- [ ] Understand the pipe operator `%>%`.
- [ ] Use `filter()`.
- [ ] Use `select()`.
- [ ] Use `mutate()`.
- [ ] Use `arrange()`.
- [ ] Use `group_by()`.
- [ ] Use `summarise()`.

### Data Visualisation

- [ ] Understand ggplot2.
- [ ] Understand `ggplot()` and `aes()`.
- [ ] Create scatter plots.
- [ ] Create bar plots.
- [ ] Create box plots.
- [ ] Add titles, labels and themes.

### Statistics

- [ ] Understand descriptive statistics.
- [ ] Calculate mean.
- [ ] Calculate standard deviation.
- [ ] Understand hypothesis testing.
- [ ] Understand null and alternative hypotheses.
- [ ] Perform a two-sample t-test.
- [ ] Interpret p-values.
- [ ] Understand when ANOVA is required.

### Linear Regression

- [ ] Understand predictor and response variables.
- [ ] Understand the linear regression equation.
- [ ] Build a model using `lm()`.
- [ ] Interpret regression coefficients.
- [ ] Understand standard error and t-value.
- [ ] Interpret p-values.
- [ ] Understand F-statistic.
- [ ] Interpret R-squared and adjusted R-squared.
- [ ] Visualise a regression line.

---

**End of Session 4: Data Manipulation, Data Visualisation and Statistical Analysis**