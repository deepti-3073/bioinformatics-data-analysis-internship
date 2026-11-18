# Module 1: R Programming

# Session 3: Core Data Structures in R

## 1. Objectives

- Create and manipulate vectors.
- Work with data frames.
- Use lists.
- Understand factors.
- Understand different data structures in R.
- Select appropriate data structures for biological data analysis.

---

# PART A: VECTORS

## 2. Vectors

### Definition

- A vector is one of the most basic data structures in R.
- It stores multiple elements of the same data type.
- Vectors are ordered, meaning every element has a specific position or index.
- Vectors are homogeneous because all elements have the same underlying data type.

### Characteristics of Vectors

1. Ordered: Elements have a specific position.
2. Homogeneous: All elements have the same data type.
3. One-dimensional: Elements are arranged in a single sequence.
4. Indexed: Each element can be accessed using its position.

### Creating a Vector

The `c()` function is used to combine values into a vector.

**Syntax:**

```r
variable_name <- c(value1, value2, value3)
```

### Example 1: Numeric Vector

```r
num <- c(1, 2, 3)

print(num)
```

**Output:**

```text
[1] 1 2 3
```

### Example 2: Character Vector

```r
genes <- c("BRCA1", "TP53", "EGFR")

print(genes)
```

**Output:**

```text
[1] "BRCA1" "TP53" "EGFR"
```

### Example 3: Logical Vector

```r
results <- c(TRUE, FALSE, TRUE)

print(results)
```

**Output:**

```text
[1] TRUE FALSE TRUE
```

### Example 4: Checking the Data Type

The `class()` function identifies the class of an object.

```r
num <- c(1, 2, 3)

class(num)
```

**Output:**

```text
[1] "numeric"
```

Other examples:

```r
class(c("A", "B", "C"))
class(c(TRUE, FALSE, TRUE))
```

Outputs:

```text
[1] "character"
[1] "logical"
```

---

## 3. Accessing Elements in a Vector

- Elements in a vector are accessed using square brackets `[ ]`.
- R uses 1-based indexing, meaning the first element is at position 1, not 0.

### Example

```r
num <- c(10, 20, 30, 40, 50)

print(num[1])
print(num[3])
```

**Output:**

```text
[1] 10
[1] 30
```

### Accessing Multiple Elements

```r
num <- c(10, 20, 30, 40, 50)

print(num[c(1, 3, 5)])
```

**Output:**

```text
[1] 10 30 50
```

### Excluding an Element

A negative index excludes an element.

```r
num <- c(10, 20, 30, 40, 50)

print(num[-2])
```

**Output:**

```text
[1] 10 30 40 50
```

### Accessing Elements Using Conditions

```r
num <- c(10, 20, 30, 40, 50)

print(num[num > 25])
```

**Output:**

```text
[1] 30 40 50
```

**Explanation:**

- `num > 25` checks every element.
- It produces TRUE or FALSE values.
- Only elements satisfying the condition are returned.

---

## 4. Modifying Vectors

### Changing an Element

```r
num <- c(10, 20, 30)

num[2] <- 50

print(num)
```

**Output:**

```text
[1] 10 50 30
```

### Adding Elements

```r
num <- c(10, 20, 30)

num <- c(num, 40)

print(num)
```

**Output:**

```text
[1] 10 20 30 40
```

### Removing Elements

```r
num <- c(10, 20, 30, 40)

num <- num[-2]

print(num)
```

**Output:**

```text
[1] 10 30 40
```

---

## 5. Useful Vector Functions

| Function | Purpose | Example |
|---|---|---|
| `length()` | Returns number of elements | `length(num)` |
| `class()` | Returns object class | `class(num)` |
| `typeof()` | Returns underlying storage type | `typeof(num)` |
| `sort()` | Sorts values | `sort(num)` |
| `rev()` | Reverses order | `rev(num)` |
| `unique()` | Returns unique values | `unique(num)` |
| `sum()` | Calculates total | `sum(num)` |
| `mean()` | Calculates average | `mean(num)` |
| `min()` | Returns minimum | `min(num)` |
| `max()` | Returns maximum | `max(num)` |
| `which()` | Returns positions satisfying a condition | `which(num > 20)` |

### Example

```r
expression <- c(5, 10, 15, 20, 25)

length(expression)
mean(expression)
sum(expression)
min(expression)
max(expression)
```

**Output:**

```text
[1] 5
[1] 15
[1] 75
[1] 5
[1] 25
```

### Biological Application

```r
gene_expression <- c(5.2, 8.4, 6.1, 10.5, 7.8)

mean(gene_expression)
max(gene_expression)
min(gene_expression)
```

**Where to use vectors:**

- Storing gene expression values.
- Storing sample IDs or gene names.
- Storing DNA sequences as character strings.
- Performing statistical calculations.
- Filtering and selecting observations.

---

## 6. Important Concept: Type Coercion in Vectors

### Definition

- A vector can store only one underlying data type.
- If different data types are combined, R automatically converts them into a common compatible type.
- This is called type coercion.

### Example 1: Combining Numbers and Characters

```r
x <- c(10, 20, "GeneA")

print(x)
class(x)
```

**Output:**

```text
[1] "10" "20" "GeneA"
[1] "character"
```

**Explanation:**

- The vector contains numbers and a character string.
- R converts the numeric values into characters.
- The entire vector becomes a character vector.

### Example 2: Combining Numbers and Logical Values

```r
x <- c(10, TRUE, 20)

print(x)
```

**Output:**

```text
[1] 10 1 20
```

**Explanation:**

- In this combination, TRUE is converted to 1.
- FALSE would be converted to 0.
- The resulting vector is numeric.

**Important:** Avoid mixing data types in a vector unless the automatic conversion is intentional.

---

# PART B: LISTS

## 7. Lists

### Definition

- A list is a data structure that can store elements of different data types.
- Lists are heterogeneous.
- They can contain vectors, data frames, matrices, other lists and individual values.
- Each element can have a different structure and length.

### Characteristics of Lists

1. Heterogeneous: Different data types can be stored together.
2. Flexible: Can contain different R objects.
3. Can be nested: A list can contain another list.
4. Elements can be named.
5. Elements can be accessed using different indexing methods.

### Creating a List

The `list()` function is used to create a list.

**Syntax:**

```r
variable_name <- list(element1, element2, element3)
```

### Example 1: Basic List

```r
my_list <- list(1, "A", TRUE)

print(my_list)
```

**Output:**

```text
[[1]]
[1] 1

[[2]]
[1] "A"

[[3]]
[1] TRUE
```

**Explanation:**

- First element: Numeric
- Second element: Character
- Third element: Logical

Unlike vectors, the elements retain their individual data types.

### Example 2: List Containing Different Objects

```r
my_list <- list(
  age = 23,
  gene = "BRCA1",
  result = TRUE,
  expression = c(5, 10, 15)
)

print(my_list)
```

**Explanation:**

This list contains:

- A numeric value.
- A character value.
- A logical value.
- A numeric vector.

### Example 3: List Containing a Data Frame

```r
gene_data <- data.frame(
  gene = c("BRCA1", "TP53"),
  expression = c(10, 20)
)

my_list <- list(
  study = "Gene Expression Study",
  data = gene_data
)

print(my_list)
```

This demonstrates how a list can store a complete data frame along with other information.

---

## 8. Accessing Elements in a List

There are three commonly used methods.

### Method 1: Single Square Brackets `[ ]`

- Returns a sublist.
- The result is still a list.

```r
my_list <- list(10, "GeneA", TRUE)

print(my_list[1])
```

**Output:**

```text
[[1]]
[1] 10
```

### Method 2: Double Square Brackets `[[ ]]`

- Extracts the actual element from the list.
- The returned object is the element itself, not a sublist.

```r
my_list <- list(10, "GeneA", TRUE)

print(my_list[[1]])
```

**Output:**

```text
[1] 10
```

### Method 3: Dollar Sign `$`

- Used to access an element by its name.

```r
my_list <- list(
  gene = "BRCA1",
  expression = 10
)

print(my_list$gene)
```

**Output:**

```text
[1] "BRCA1"
```

### Difference Between `[ ]`, `[[ ]]` and `$`

| Method | Function |
|---|---|
| `[ ]` | Returns a sublist |
| `[[ ]]` | Extracts a single element |
| `$` | Extracts an element by name |

---

## 9. Modifying Lists

### Adding an Element

```r
my_list <- list(gene = "BRCA1", expression = 10)

my_list$treatment <- "Drug A"

print(my_list)
```

### Changing an Element

```r
my_list$expression <- 15

print(my_list$expression)
```

### Removing an Element

```r
my_list$treatment <- NULL

print(my_list)
```

### Biological Application

A list can store different results from a bioinformatics analysis.

```r
analysis_result <- list(
  sample_id = "S1",
  gene = "TP53",
  expression = c(5.2, 8.1, 9.5),
  significant = TRUE
)
```

**Where to use lists:**

- Storing different types of experimental results.
- Storing analysis outputs.
- Combining metadata and numerical results.
- Storing model results and parameters.
- Organising multiple biological datasets.

---

# PART C: FACTORS

## 10. Factors

### Definition

- A factor is a data structure used to represent categorical variables.
- Categorical variables represent groups or categories rather than continuous numerical measurements.
- Factors store categories as levels.
- They are particularly useful in statistical analysis and data visualisation.

### What Are Categorical Variables?

Categorical variables describe groups or classifications.

Examples:

- Treatment: Control, Drug A, Drug B.
- Gender categories: Female, Male.
- Sample type: Blood, Tissue, Saliva.
- Disease status: Healthy, Diseased.
- Bacterial species: Species A, Species B, Species C.

### Example Dataset: Gene Expression

| Gene | Treatment | Expression |
|---|---|---:|
| Gene1 | Control | 10 |
| Gene2 | Control | 22 |
| Gene3 | Drug A | 24 |
| Gene4 | Drug A | 22 |
| Gene5 | Drug B | 45 |
| Gene6 | Drug B | 17 |

Here:

- `Gene` is a character variable.
- `Treatment` is a categorical variable.
- `Expression` is a numeric variable.
- The Treatment variable has three categories: Control, Drug A and Drug B.

These categories are represented as factor levels when the column is converted into a factor.

---

## 11. Creating Factors

### Step 1: Create the Dataset

```r
gene_data <- data.frame(
  gene = c("Gene1", "Gene2", "Gene3", "Gene4", "Gene5", "Gene6"),
  treatment = c("control", "control", "drug A", "drug A", "drug B", "drug B"),
  expression = c(10, 22, 24, 22, 45, 17)
)
```

### Step 2: Convert the Treatment Column into a Factor

```r
gene_data$treatment <- as.factor(gene_data$treatment)
```

**Explanation:**

- `gene_data` is the data frame.
- `$treatment` selects the treatment column.
- `as.factor()` converts the column into a factor.
- `<-` assigns the converted column back to the data frame.

### Step 3: Check the Class

```r
class(gene_data$treatment)
```

**Output:**

```text
[1] "factor"
```

### Step 4: Display Factor Levels

```r
levels(gene_data$treatment)
```

**Output:**

```text
[1] "control" "drug A" "drug B"
```

### Step 5: Check the Structure of the Dataset

```r
str(gene_data)
```

**Output (simplified):**

```text
'data.frame': 6 obs. of 3 variables:
 $ gene      : chr  "Gene1" "Gene2" "Gene3" ...
 $ treatment : Factor w/ 3 levels "control","drug A",..: 1 1 2 2 3 3
 $ expression: num  10 22 24 22 45 17
```

**Explanation:**

- `chr` means character.
- `num` means numeric.
- `Factor w/ 3 levels` means the column is a factor with three categories.
- `obs.` means observations.
- `variables` refers to columns.

---

## 12. Understanding Factor Levels

### Definition

- Factor levels are the distinct categories that a factor variable can contain.
- R stores the available categories as levels.
- Each observation is associated with one of those levels.

### Example

```r
treatment <- factor(
  c("control", "drug A", "drug B", "control")
)

levels(treatment)
```

**Output:**

```text
[1] "control" "drug A" "drug B"
```

### Counting Observations in Each Level

The `table()` function counts how many times each category appears.

```r
table(treatment)
```

**Output:**

```text
treatment
control drug A drug B
      2      1      1
```

### Checking the Number of Levels

```r
nlevels(treatment)
```

**Output:**

```text
[1] 3
```

---

## 13. Temporary Conversion vs Permanent Assignment

### Temporary Conversion

```r
as.factor(gene_data$treatment)
```

This converts the column and displays the result, but does not permanently replace the original column in the data frame.

### Assigning the Conversion Back

```r
gene_data$treatment <- as.factor(gene_data$treatment)
```

This replaces the original column with the factor column.

**Important:** In R, the conversion is not permanent unless the result is assigned to an object or back to the original column.

---

## 14. Ordered and Unordered Factors

### Unordered Factors

- Used when categories have no natural ranking.
- Example: Blood group, treatment type, species.

```r
blood_group <- factor(
  c("A", "B", "AB", "O")
)
```

### Ordered Factors

- Used when categories have a meaningful order or ranking.
- Example: Low, Medium, High.

```r
expression_level <- factor(
  c("Low", "High", "Medium", "Low"),
  levels = c("Low", "Medium", "High"),
  ordered = TRUE
)

print(expression_level)
```

**Explanation:**

The levels are explicitly arranged in the intended order:

1. Low
2. Medium
3. High

This allows R to recognise their ordering.

### Example: Disease Severity

```r
severity <- factor(
  c("Mild", "Severe", "Moderate"),
  levels = c("Mild", "Moderate", "Severe"),
  ordered = TRUE
)
```

**Where to use factors:**

- Representing treatment groups.
- Classifying biological samples.
- Representing disease categories.
- Comparing groups in statistical analysis.
- Performing grouped data analysis.
- Creating plots with categorical axes.

---

## 15. Changing Factor Levels

### Example: Renaming Categories

The `levels()` function can be used to rename factor levels.

```r
treatment <- factor(
  c("control", "drug A", "drug B")
)

levels(treatment) <- c(
  "Control",
  "Drug A",
  "Drug B"
)

print(treatment)
```

### Example: Setting the Order of Levels

```r
treatment <- factor(
  c("drug B", "control", "drug A"),
  levels = c("control", "drug A", "drug B")
)

levels(treatment)
```

**Important:** The order of factor levels can influence how categories are displayed in plots and some statistical analyses.

---

# PART D: DATA FRAMES

## 16. Data Frames

### Definition

- A data frame is a two-dimensional data structure used to store tabular data.
- It consists of rows and columns.
- Each column can contain a different data type.
- Each column must have the same number of rows.

### Characteristics

1. Two-dimensional: Contains rows and columns.
2. Heterogeneous across columns: Different columns can have different data types.
3. Each column is a vector.
4. All columns must have equal lengths.
5. Rows generally represent observations.
6. Columns generally represent variables.

### Example Dataset

| Sample_ID | Treatment | Expression |
|---|---|---:|
| S1 | Control | 10 |
| S2 | Control | 22 |
| S3 | Drug A | 24 |
| S4 | Drug A | 22 |
| S5 | Drug B | 45 |

### Creating a Data Frame

The `data.frame()` function is used to create a data frame.

```r
gene_data <- data.frame(
  Sample_ID = c("S1", "S2", "S3", "S4", "S5"),
  Treatment = c("Control", "Control", "Drug A", "Drug A", "Drug B"),
  Expression = c(10, 22, 24, 22, 45)
)

print(gene_data)
```

### Understanding Rows and Columns

- Rows represent observations or samples.
- Columns represent variables or characteristics.

In the above dataset:

- There are 5 observations.
- There are 3 variables.

### Useful Data Frame Functions

| Function | Purpose |
|---|---|
| `head()` | Displays the first six rows by default |
| `tail()` | Displays the last six rows by default |
| `str()` | Displays the structure |
| `dim()` | Returns number of rows and columns |
| `nrow()` | Returns number of rows |
| `ncol()` | Returns number of columns |
| `names()` | Returns column names |
| `colnames()` | Returns column names |
| `summary()` | Provides a summary of columns |
| `View()` | Opens a spreadsheet-like viewer in RStudio |

### Example

```r
head(gene_data)
tail(gene_data)
str(gene_data)
dim(gene_data)
nrow(gene_data)
ncol(gene_data)
names(gene_data)
summary(gene_data)
```

### Accessing Data Frame Columns

#### Method 1: Using `$`

```r
gene_data$Expression
```

Returns the Expression column.

#### Method 2: Using Column Index

```r
gene_data[, 3]
```

Returns the third column.

#### Method 3: Using Column Name

```r
gene_data[, "Treatment"]
```

Returns the Treatment column.

### Accessing Rows

```r
gene_data[1, ]
```

Returns the first row.

```r
gene_data[2, ]
```

Returns the second row.

### Accessing Specific Rows and Columns

```r
gene_data[1, 2]
```

Returns the value in the first row and second column.

```r
gene_data[1:3, 1:2]
```

Returns the first three rows and first two columns.

### Filtering Rows Using Conditions

```r
gene_data[gene_data$Expression > 20, ]
```

Returns only rows where expression is greater than 20.

### Selecting Specific Columns

```r
gene_data[, c("Sample_ID", "Expression")]
```

Returns only the Sample_ID and Expression columns.

### Adding a New Column

```r
gene_data$Status <- c(
  "Low", "High", "High", "High", "High"
)

print(gene_data)
```

### Modifying an Existing Column

```r
gene_data$Expression[1] <- 15
```

Changes the expression value in the first row to 15.

### Removing a Column

```r
gene_data$Status <- NULL
```

Removes the Status column.

### Handling Missing Values

Data frames can contain missing values represented by `NA`.

```r
gene_data <- data.frame(
  gene = c("BRCA1", "TP53", "EGFR"),
  expression = c(10, NA, 25)
)

print(gene_data)
```

To check for missing values:

```r
is.na(gene_data$expression)
```

To count missing values:

```r
sum(is.na(gene_data$expression))
```

**Where to use data frames:**

- Storing gene expression datasets.
- Storing sample metadata.
- Recording experimental observations.
- Analysing clinical or laboratory data.
- Storing results from sequencing experiments.

---

# PART E: OTHER IMPORTANT DATA STRUCTURES

## 17. Matrices

### Definition

- A matrix is a two-dimensional data structure.
- It contains rows and columns.
- All elements must have the same underlying data type.
- It is homogeneous.

### Creating a Matrix

The `matrix()` function is used to create a matrix.

```r
my_matrix <- matrix(
  c(1, 2, 3, 4, 5, 6),
  nrow = 2,
  ncol = 3
)

print(my_matrix)
```

**Output:**

```text
     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6
```

By default, R fills matrices column by column.

### Accessing Matrix Elements

```r
my_matrix[1, 2]
```

Returns the element in the first row and second column.

```r
my_matrix[2, ]
```

Returns all elements in the second row.

```r
my_matrix[, 1]
```

Returns all elements in the first column.

### Biological Application

A gene expression matrix may contain:

- Rows: Genes.
- Columns: Samples.
- Values: Expression measurements.

**Where to use matrices:**

- Numerical data analysis.
- Gene expression measurements.
- Mathematical calculations.
- Linear algebra operations.

---

## 18. Arrays

### Definition

- An array is a data structure that can store data in more than two dimensions.
- All elements must have the same underlying data type.
- It is homogeneous.

### Creating an Array

```r
my_array <- array(
  1:12,
  dim = c(2, 3, 2)
)

print(my_array)
```

This creates an array with:

- 2 rows.
- 3 columns.
- 2 layers.

### Biological Application

Arrays can be used for multidimensional biological datasets, such as measurements across:

- Genes.
- Samples.
- Experimental conditions.

---

# PART F: COMPARISON OF DATA STRUCTURES

## 19. Differences Between Vectors, Lists, Factors, Data Frames, Matrices and Arrays

| Data structure | Dimensions | Data type | Main purpose |
|---|---|---|---|
| Vector | One-dimensional | Homogeneous | Store a sequence of values |
| List | Flexible/nested | Heterogeneous | Store different R objects |
| Factor | One-dimensional | Categorical | Store group/category information |
| Data frame | Two-dimensional | Different types across columns | Store tabular data |
| Matrix | Two-dimensional | Homogeneous | Store numerical or other same-type data |
| Array | Multiple dimensions | Homogeneous | Store multidimensional data |

### Quick Selection Guide

- Need to store a sequence of numbers? Use a vector.
- Need to store different data types together? Use a list.
- Need to store categorical groups? Use a factor.
- Need a table with different types of columns? Use a data frame.
- Need a two-dimensional structure with one data type? Use a matrix.
- Need more than two dimensions? Use an array.

---

# PART G: BIOINFORMATICS APPLICATIONS

## 20. Choosing Data Structures for Biological Data

### Example 1: Storing Gene Names

```r
genes <- c("BRCA1", "TP53", "EGFR", "MYC")
```

**Structure:** Vector

**Reason:** All elements are character values.

### Example 2: Storing Treatment Groups

```r
treatment <- factor(
  c("Control", "Drug A", "Drug B")
)
```

**Structure:** Factor

**Reason:** Treatment represents categorical groups.

### Example 3: Storing Gene Expression Values

```r
expression <- c(10.5, 15.2, 20.1, 12.4)
```

**Structure:** Vector

**Reason:** All elements are numerical measurements.

### Example 4: Storing Experimental Information

```r
experiment <- list(
  gene = "TP53",
  treatment = "Drug A",
  expression = c(10, 15, 20),
  significant = TRUE
)
```

**Structure:** List

**Reason:** Different types of information are stored together.

### Example 5: Storing Sample Information

```r
sample_data <- data.frame(
  Sample_ID = c("S1", "S2", "S3"),
  Treatment = c("Control", "Drug A", "Drug B"),
  Expression = c(10, 20, 30)
)

sample_data$Treatment <- as.factor(sample_data$Treatment)
```

**Structure:** Data frame containing a factor column.

**Reason:** It contains multiple observations and different variables.

---

# PART H: COMMON MISTAKES AND IMPORTANT POINTS

## 21. Common Errors

### 1. Mixing Data Types in Vectors

```r
x <- c(10, 20, "A")
```

R converts all elements to character.

### 2. Confusing List Indexing

```r
my_list[1]
```

Returns a sublist.

```r
my_list[[1]]
```

Returns the actual first element.

### 3. Forgetting to Assign Factor Conversion

```r
as.factor(gene_data$treatment)
```

This does not replace the original column.

Correct:

```r
gene_data$treatment <- as.factor(gene_data$treatment)
```

### 4. Different Column Lengths in Data Frames

All columns in a data frame must have compatible lengths. R cannot create an ordinary data frame from columns with unrelated lengths.

### 5. Confusing Rows and Columns

For a data frame:

```r
data[row, column]
```

Example:

```r
gene_data[1, 2]
```

Means first row, second column.

### 6. Confusing class() and typeof()

```r
x <- 10

class(x)
typeof(x)
```

Output:

```text
[1] "numeric"
[1] "double"
```

- `class()` tells you the object's class.
- `typeof()` tells you its underlying storage type.

---

# PART I: QUICK REVISION

## 22. Important Functions to Remember

| Function | Purpose |
|---|---|
| `c()` | Creates a vector |
| `list()` | Creates a list |
| `data.frame()` | Creates a data frame |
| `factor()` | Creates a factor |
| `as.factor()` | Converts an object into a factor |
| `levels()` | Displays or changes factor levels |
| `nlevels()` | Counts factor levels |
| `table()` | Counts category frequencies |
| `matrix()` | Creates a matrix |
| `array()` | Creates an array |
| `class()` | Displays object class |
| `typeof()` | Displays underlying storage type |
| `length()` | Returns number of elements |
| `str()` | Displays object structure |
| `dim()` | Returns dimensions |
| `head()` | Displays first rows |
| `tail()` | Displays last rows |
| `summary()` | Provides summary statistics |

## 23. Key Concepts to Explain in an Exam or Interview

1. What is a vector in R?
2. What is the difference between homogeneous and heterogeneous data structures?
3. How do you create and access vector elements?
4. What is type coercion?
5. What is a list? How is it different from a vector?
6. What is the difference between `[ ]` and `[[ ]]` in lists?
7. What is a factor in R?
8. What are factor levels?
9. What is the difference between ordered and unordered factors?
10. How do you convert a character column into a factor?
11. What is a data frame?
12. How do you access rows and columns in a data frame?
13. What is the difference between a data frame and a matrix?
14. What is the difference between `class()` and `typeof()`?
15. Which data structure would you use to store gene expression data?

---

## 24. Session 3 Completion Checklist

- [ ] Understand vectors.
- [ ] Create numeric, character and logical vectors.
- [ ] Access vector elements using indexing.
- [ ] Modify vectors.
- [ ] Understand vector functions.
- [ ] Understand type coercion.
- [ ] Create and manipulate lists.
- [ ] Understand list indexing.
- [ ] Understand factors and categorical variables.
- [ ] Convert columns into factors.
- [ ] Understand factor levels.
- [ ] Create and manipulate data frames.
- [ ] Access rows and columns.
- [ ] Filter data frames using conditions.
- [ ] Understand matrices and arrays.
- [ ] Choose appropriate data structures for biological datasets.

---

**End of Session 3: Core Data Structures in R**