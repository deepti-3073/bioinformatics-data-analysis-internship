# Module 2: Control Flow and Logical Structures

## Session 2: Control Flow and Logical Structures

## 1. Objectives

- Understand conditional statements.
- Apply logical operators.
- Implement loops.
- Translate problem statements into structured logic.

---

## 2. Control Flow

### Definition

- Control flow determines how a program makes decisions and repeats actions.
- It controls the order in which instructions are executed.
- It allows a program to execute different blocks of code depending on conditions.
- It also allows repetitive tasks to be performed automatically using loops.

### Main Components of Control Flow

1. Conditional statements – `if`, `else`, `elif`.
2. Logical operators – `and`, `or`, `not`.
3. Loops – Used to repeat tasks automatically.

### Basic Working

```text
       Start
         |
         v
     Condition?
       /    \
     Yes     No
      |       |
      v       v
   Action   Alternative
      |
      v
      End
```

### Example

A program can check whether a person's age is above 18.

- If the condition is true, it displays "Adult".
- If the condition is false, it can display an alternative message.

Control flow is useful when a program needs to make decisions or repeat operations based on specific requirements.

---

# PART A: CONDITIONAL STATEMENTS

## 3. Conditional Statements

### Definition

- Conditional statements allow a program to make decisions.
- They execute a particular block of code depending on whether a condition is true or false.
- Python uses `if`, `elif` and `else` for conditional execution.

---

## 4. if Statement

### Definition

- The `if` statement is used when there is one condition to check.
- The code inside the `if` block executes only when the condition is true.
- If the condition is false, the block is skipped.

### Syntax

```python
if condition:
    statement
```

### Example: Checking Age

```python
age = 21

if age > 18:
    print("Adult")
```

**Output:**

```text
Adult
```

### Explanation

1. `age = 21` assigns 21 to the variable.
2. `age > 18` checks whether the age is greater than 18.
3. The condition is true because 21 is greater than 18.
4. Therefore, Python executes the `print()` statement.

**Important:** If the condition is false, nothing is printed because there is no alternative block in this example.

### Example: Condition Is False

```python
age = 16

if age > 18:
    print("Adult")
```

**Output:**

```text
```

No output is produced because the condition is false.

---

## 5. Interactive Writing and Script Mode

Python code can be written and executed in different ways.

### Interactive Mode

- You write a command and immediately see its result.
- Each command can be executed individually.
- It is useful for testing small pieces of code.

Example:

```python
age = 21
print(age)
```

Output:

```text
21
```

### Script Mode

- You write multiple lines of Python code in a script file.
- The file is saved with the `.py` extension.
- The entire script can be executed to obtain the output.

Example:

```python
age = 21

if age > 18:
    print("Adult")
```

### Examples of Environments

- Visual Studio Code.
- Jupyter Notebook.
- Google Colab.

These environments allow you to write and execute Python code. Their execution interfaces differ, but the underlying Python syntax remains the same.

---

## 6. if-else Statement

### Definition

- The `if-else` statement is used when there are two possible outcomes.
- If the condition is true, the `if` block executes.
- If the condition is false, the `else` block executes.
- Only one of these two blocks is executed.

### Syntax

```python
if condition:
    statement_if_true
else:
    statement_if_false
```

### Example: Checking Age

```python
age = 21

if age > 18:
    print("Adult")
else:
    print("Minor")
```

**Output:**

```text
Adult
```

### Example: Condition Is False

```python
age = 16

if age > 18:
    print("Adult")
else:
    print("Minor")
```

**Output:**

```text
Minor
```

### Explanation

- Python first evaluates the condition `age > 18`.
- If it is true, "Adult" is printed.
- Otherwise, "Minor" is printed.

### Where to Use

- Checking age eligibility.
- Checking whether a value meets a requirement.
- Classifying a result into two possible categories.
- Checking whether a condition is satisfied.

---

## 7. if-elif-else Statement

### Definition

- The `if-elif-else` statement is used when there are multiple conditions to evaluate.
- `if` checks the first condition.
- `elif` checks additional conditions if the previous conditions were false.
- `else` acts as the default case when none of the previous conditions are true.

### Syntax

```python
if condition1:
    statement1

elif condition2:
    statement2

elif condition3:
    statement3

else:
    default_statement
```

### Important Points

- There can be multiple `elif` conditions.
- Python evaluates the conditions from top to bottom.
- Once a true condition is found, its corresponding block executes.
- The remaining conditions are skipped.
- The `else` block is optional.

### Example: Grade Classification

```python
marks = 86

if marks >= 90:
    print("Grade A")

elif marks >= 75:
    print("Grade B")

else:
    print("Grade C")
```

**Output:**

```text
Grade B
```

### Explanation

1. `marks = 86` assigns 86 to the variable.
2. Python checks whether marks are greater than or equal to 90.
3. The condition is false.
4. Python moves to the `elif` condition.
5. It checks whether marks are greater than or equal to 75.
6. This condition is true.
7. Therefore, "Grade B" is printed.
8. The `else` block is skipped.

### Example: Different Marks

| Marks | Output |
|---:|---|
| 95 | Grade A |
| 86 | Grade B |
| 75 | Grade B |
| 65 | Grade C |

### Where to Use

- Grade classification.
- Classifying experimental results.
- Categorising numerical measurements.
- Assigning labels based on multiple conditions.

---

# PART B: LOGICAL OPERATORS

## 8. Logical Operators

### Definition

- Logical operators are used to combine or modify conditions.
- They help evaluate multiple conditions in a single expression.
- Python has three main logical operators: `and`, `or` and `not`.

### 1. AND Operator (`and`)

**Definition:**

- The `and` operator returns `True` only when all the conditions are true.
- If even one condition is false, the overall result is false.

### Example

```python
x = 10
y = 5

print(x > 5 and y > 3)
```

**Output:**

```text
True
```

**Explanation:**

- `x > 5` is true because 10 is greater than 5.
- `y > 3` is true because 5 is greater than 3.
- Both conditions are true.
- Therefore, the result is `True`.

### Example: One Condition Is False

```python
x = 10
y = 2

print(x > 5 and y > 3)
```

**Output:**

```text
False
```

The second condition is false, so the overall result is false.

### 2. OR Operator (`or`)

**Definition:**

- The `or` operator returns `True` when at least one condition is true.
- It returns `False` only when all conditions are false.

### Example

```python
x = 10
y = 5

print(x > 5 or y > 10)
```

**Output:**

```text
True
```

**Explanation:**

- `x > 5` is true.
- `y > 10` is false.
- At least one condition is true.
- Therefore, the result is `True`.

### Example: Both Conditions Are False

```python
x = 3
y = 2

print(x > 5 or y > 10)
```

**Output:**

```text
False
```

### 3. NOT Operator (`not`)

**Definition:**

- The `not` operator reverses a logical value.
- True becomes False.
- False becomes True.
- It gives the complement of a condition.

### Example

```python
x = 10

print(not (x > 5))
```

**Output:**

```text
False
```

**Explanation:**

- `x > 5` is true.
- `not` reverses the result.
- Therefore, the output is false.

### Example: Reversing a False Condition

```python
x = 3

print(not (x > 5))
```

**Output:**

```text
True
```

### Summary of Logical Operators

| Operator | Meaning | Result |
|---|---|---|
| `and` | All conditions must be true | True only if all are true |
| `or` | At least one condition must be true | True if one or more are true |
| `not` | Reverses the condition | True becomes False and vice versa |

### Truth Table

| A | B | A and B | A or B |
|---|---|---|---|
| True | True | True | True |
| True | False | False | True |
| False | True | False | True |
| False | False | False | False |

For the `not` operator:

| A | not A |
|---|---|
| True | False |
| False | True |

### Where to Use Logical Operators

- Checking multiple eligibility requirements.
- Evaluating experimental conditions.
- Combining multiple filtering conditions.
- Determining whether a sample meets specified criteria.

**Important:** Python uses the words `and`, `or` and `not` for logical operations. It does not use `&&`, `||` and `!` as logical operators.

---

# PART C: LOOPS

## 9. Loops

### Definition

- Loops are used to repeat a block of code automatically.
- They reduce the need to write the same instructions repeatedly.
- Python provides different types of loops, including `for` and `while`.

### Types of Loops Covered

1. For loop.
2. While loop.

---

## 10. For Loop

### Definition

- A `for` loop is used to iterate over a sequence or range of values.
- It is commonly used when the number of iterations or the collection of values to process is known.
- The loop executes once for each value in the specified sequence.

### Syntax

```python
for variable in sequence:
    statement
```

### Using range()

The `range()` function generates a sequence of numbers.

### Example

```python
for i in range(5):
    print(i)
```

**Output:**

```text
0
1
2
3
4
```

### Explanation

- `range(5)` generates the numbers 0, 1, 2, 3 and 4.
- The variable `i` takes each value one at a time.
- `print(i)` displays the current value.
- The loop runs five times.

**Important:** `range(5)` starts from 0 and stops before 5.

Therefore, it generates five values:

```text
0, 1, 2, 3, 4
```

### Example: Specifying a Starting Value

```python
for i in range(1, 6):
    print(i)
```

**Output:**

```text
1
2
3
4
5
```

Here:

- The first argument specifies the starting value.
- The second argument specifies the stopping value, which is excluded.

### Where to Use

- Repeating a task a fixed number of times.
- Processing multiple samples.
- Performing calculations for a series of values.
- Repeating the same operation across multiple biological measurements.

---

## 11. While Loop

### Definition

- A `while` loop executes a block of code as long as a specified condition remains true.
- The condition is checked before each iteration.
- When the condition becomes false, the loop stops.

### Syntax

```python
while condition:
    statement
```

### Example

```python
count = 0

while count < 5:
    print(count)
    count += 1
```

**Output:**

```text
0
1
2
3
4
```

### Explanation

1. `count = 0` assigns the initial value.
2. Python checks whether `count < 5`.
3. If the condition is true, the loop body executes.
4. `print(count)` displays the current value.
5. `count += 1` increases the value by one.
6. The condition is checked again.
7. When `count` becomes 5, the condition is false.
8. The loop stops.

### Alternative Way to Update the Variable

Instead of:

```python
count += 1
```

We can write:

```python
count = count + 1
```

Both statements increase the value of `count` by one.

### Important Points

- An initial value must be assigned before the loop if the condition depends on that variable.
- The variable must be updated appropriately.
- If the condition never becomes false, the loop may continue indefinitely. This is called an infinite loop.

### Difference Between for and while Loops

| For Loop | While Loop |
|---|---|
| Iterates over a sequence or range | Executes while a condition remains true |
| Commonly used when the iterations or sequence are known | Commonly used when repetition depends on a condition |
| Example: `for i in range(5)` | Example: `while count < 5` |

---

# PART D: BREAK AND CONTINUE

## 12. Break and Continue in Loops

Python provides `break` and `continue` statements to control how loops execute.

### 1. break Statement

**Definition:**

- The `break` statement terminates the entire loop immediately.
- Once `break` is executed, the loop stops.
- The remaining iterations are not performed.

### Example

```python
for i in range(6):
    if i == 4:
        break

    print(i)
```

**Output:**

```text
0
1
2
3
```

### Explanation

1. The loop starts with `i = 0`.
2. It prints 0, 1, 2 and 3.
3. When `i` becomes 4, the condition `i == 4` becomes true.
4. The `break` statement executes.
5. The entire loop terminates.
6. Values 4 and 5 are not printed.

### 2. continue Statement

**Definition:**

- The `continue` statement skips the remaining statements in the current iteration.
- It moves directly to the next iteration of the loop.
- The entire loop does not stop.

### Example

```python
for i in range(6):
    if i == 3:
        continue

    print(i)
```

**Output:**

```text
0
1
2
4
5
```

### Explanation

1. The loop starts with `i = 0`.
2. Values 0, 1 and 2 are printed.
3. When `i` becomes 3, the condition is true.
4. The `continue` statement skips the `print(i)` statement for that iteration.
5. The loop proceeds to the next value, 4.
6. Values 4 and 5 are printed.

### Difference Between break and continue

| break | continue |
|---|---|
| Terminates the entire loop | Skips only the current iteration |
| No further iterations are executed | The next iteration begins |
| Used to stop a loop when a condition is met | Used to skip selected iterations |

---

## 13. Quick Revision: Important Keywords and Functions

| Keyword / Function | Purpose |
|---|---|
| `if` | Checks a condition |
| `elif` | Checks an additional condition |
| `else` | Executes the default block |
| `and` | Requires all conditions to be true |
| `or` | Requires at least one condition to be true |
| `not` | Reverses a logical result |
| `for` | Repeats code over a sequence |
| `while` | Repeats code while a condition is true |
| `range()` | Generates a sequence of numbers |
| `break` | Terminates a loop |
| `continue` | Skips the current iteration |

---

## 14. Important Concepts to Remember

1. What is control flow?
2. What are conditional statements?
3. What is the difference between `if` and `if-else`?
4. When is `if-elif-else` used?
5. What is the purpose of logical operators?
6. What is the difference between `and`, `or` and `not`?
7. What is a loop?
8. What is the purpose of a `for` loop?
9. What is the purpose of `range()`?
10. What is the difference between a `for` loop and a `while` loop?
11. Why is it necessary to update the variable in a `while` loop?
12. What is an infinite loop?
13. What is the purpose of `break`?
14. What is the purpose of `continue`?
15. What is the difference between `break` and `continue`?

---

## 15. Session 2 Completion Checklist

### Conditional Statements

- [ ] Understand control flow.
- [ ] Use `if` statements.
- [ ] Use `if-else` statements.
- [ ] Use `if-elif-else` statements.
- [ ] Understand interactive and script-based execution.

### Logical Operators

- [ ] Understand the `and` operator.
- [ ] Understand the `or` operator.
- [ ] Understand the `not` operator.
- [ ] Evaluate multiple conditions.

### Loops

- [ ] Understand loops.
- [ ] Use `for` loops.
- [ ] Understand the `range()` function.
- [ ] Use `while` loops.
- [ ] Understand loop conditions and variable updates.

### Loop Control

- [ ] Understand the `break` statement.
- [ ] Understand the `continue` statement.
- [ ] Identify the difference between `break` and `continue`.

---

**End of Session 2: Control Flow and Logical Structures**