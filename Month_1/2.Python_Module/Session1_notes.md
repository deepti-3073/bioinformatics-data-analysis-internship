# Module 1: Introduction to Python

## Session 1: Introduction to Python

## 1. Objectives

- Install the Python environment.
- Understand the execution flow of Python.
- Work with variables and data types.
- Perform basic input and output operations.

---

## 2. Why is Python Important?

Python is a high-level, general-purpose programming language widely used in data analysis, automation, research and software development.

### Importance of Python

- **Easy and simple to understand:** Python has a readable syntax that makes it beginner-friendly.
- **Powerful libraries:** Python provides libraries for data analysis, visualisation, machine learning and scientific computing.
- **Used in industry and research:** It is widely used in scientific research, biotechnology, bioinformatics and data science.
- **Versatile:** It can be used for automation, data processing, application development and many other tasks.

### Applications in Biotechnology and Bioinformatics

Python can be used for:

- Analysing biological datasets.
- Processing DNA and protein sequences.
- Performing statistical analysis.
- Automating repetitive laboratory data-processing tasks.
- Analysing genomic and transcriptomic data.

---

## 3. Downloading and Installing Python

Python can be downloaded from its official website:

[https://www.python.org/](https://www.python.org/)

### Installation

1. Visit the official Python website.
2. Download the required Python version.
3. Run the installer.
4. During installation, enable the **Add Python to PATH** option.
5. Complete the installation.

### What is PATH?

- PATH is an environment variable maintained by the operating system.
- It contains locations of executable programs.
- Adding Python to PATH allows Python to be accessed from the Command Prompt without specifying its complete installation location.

### Checking Python Installation

Open Command Prompt and enter:

```bash
python --version
```

This displays the installed Python version.

Example output:

```text
Python 3.14.7
```

The displayed version depends on the installed Python release.

---

## 4. General Process of Running Python in Command Prompt

Python programs can be executed using the Command Prompt (CMD).

### Execution Steps

1. Open Command Prompt.
2. Navigate to the location where Python or your Python script is available, if necessary.
3. Enter the Python command to open the interpreter or execute a script.
4. Press Enter.
5. Python executes the instructions and displays the output or an error message.

### Opening the Python Interpreter

```bash
python
```

This opens the interactive Python interpreter.

You can directly enter Python statements:

```python
print("Hello World")
```

Output:

```text
Hello World
```

### Running a Python Script

Suppose the file is named `program.py`.

Navigate to the folder containing the file and execute:

```bash
python program.py
```

Python executes the script and displays the output in Command Prompt.

### Output and Exit

- The output is displayed in the Command Prompt.
- Output can also be redirected or saved into another file.
- The `exit()` command closes the interactive Python interpreter.

```python
exit()
```

**Important distinction:**

- `exit()` closes the Python interpreter.
- It does not close the Command Prompt window itself.

---

## 5. IDE for Python

### Visual Studio Code (VS Code)

Visual Studio Code is a code editor that supports Python and several other programming languages.

It can be downloaded from:

[https://code.visualstudio.com/](https://code.visualstudio.com/)

### Features

- Supports multiple programming languages.
- Provides an environment for writing and editing code.
- Supports running and debugging programs.
- Provides extensions for additional programming language support.

**Important:** VS Code is a code editor, not the Python interpreter itself. Python must be installed separately to execute Python programs.

---

## 6. How is Python Code Executed?

Python code is executed by the Python interpreter.

### Important Characteristics

1. **Line-by-line execution:** Python executes instructions in sequence, following the program's control flow.
2. **Case-sensitive:** Uppercase and lowercase letters are treated differently.
3. **Indentation defines code blocks:** Indentation determines which statements belong to a block of code.
4. **Syntax errors stop execution:** Invalid syntax prevents the affected program from executing successfully.

### Example: Case Sensitivity

```python
name = "Deepti"

print(name)
```

Output:

```text
Deepti
```

However:

```python
print(Name)
```

Produces an error because `Name` and `name` are different identifiers.

### Basic Execution Flow

```text
Python Code
     |
     v
Python Interpreter
     |
     v
Execution of Instructions
     |
     v
Output or Error
```

**Explanation:**

- Python code is supplied to the interpreter.
- The interpreter processes the instructions.
- If the code is valid, the program executes.
- The result is displayed as output.
- If an error occurs, Python reports it.

---

# PART B: VARIABLES AND DATA TYPES

## 7. Variables in Python

### Definition

- A variable is a named reference used to store or refer to a data value.
- Variables allow information to be stored and reused during program execution.
- Python uses dynamic typing, meaning the type of a variable is determined at runtime.

### Creating Variables

Python uses the assignment operator `=` to assign values to variables.

```python
x = 3
```

Here:

- `x` is the variable name.
- `3` is the assigned value.
- `=` is the assignment operator.

### Example: Reassigning a Variable

```python
x = 3
x = 4

print(x)
```

Output:

```text
4
```

**Explanation:**

- Initially, `x` refers to the value 3.
- Later, `x` is reassigned to 4.
- Therefore, printing `x` displays 4.

This demonstrates Python's dynamic typing and reassignment.

---

## 8. Naming Rules of Variables

Python follows certain rules when naming variables.

### Rules

1. A variable name must start with a letter or an underscore (`_`).
2. A variable name cannot start with a number.
3. Variable names cannot be Python keywords.
4. Variable names are case-sensitive.
5. Spaces are not allowed in variable names.

### Valid Variable Names

```python
name = "Deepti"
age = 23
_gene = "BRCA1"
sample_id = "S1"
```

### Invalid Variable Names

```python
2name = "Deepti"
```

Cannot start with a number.

```python
sample id = "S1"
```

Cannot contain spaces.

```python
class = "Biotechnology"
```

`class` is a reserved Python keyword.

### Case Sensitivity

```python
age = 21
Age = 25

print(age)
print(Age)
```

Output:

```text
21
25
```

Python treats `age` and `Age` as two different variables.

---

## 9. Data Types in Python

### Definition

A data type determines the kind of value stored or represented by a variable.

Python has several built-in data types.

### 1. Numeric Data Types

Numeric data types represent numbers.

There are three main numeric types:

#### a. Integer (`int`)

- Represents whole numbers.
- Does not contain a decimal component.

Example:

```python
age = 21
print(age)
print(type(age))
```

Output:

```text
21
<class 'int'>
```

#### b. Float (`float`)

- Represents decimal or floating-point numbers.

Example:

```python
temperature = 37.5

print(temperature)
print(type(temperature))
```

Output:

```text
37.5
<class 'float'>
```

#### c. Complex (`complex`)

- Represents complex numbers.
- Contains a real component and an imaginary component.
- Python uses `j` to represent the imaginary part.

Example:

```python
x = 2 + 3j

print(x)
print(type(x))
```

Output:

```text
(2+3j)
<class 'complex'>
```

### 2. Boolean (`bool`)

- Represents logical values.
- Has only two possible values: `True` and `False`.
- Used in conditions and logical operations.

Example:

```python
result = True

print(result)
print(type(result))
```

Output:

```text
True
<class 'bool'>
```

**Important:** Python uses `True` and `False` with uppercase first letters.

### 3. Sequence Types

Sequence types store ordered collections of elements.

The sequence types covered here are:

#### a. String (`str`)

- Stores text.
- Represents a sequence of characters.
- Strings are immutable, meaning their individual characters cannot be directly modified after creation.

Example:

```python
name = "Deepti"

print(name)
print(type(name))
```

Output:

```text
Deepti
<class 'str'>
```

#### b. List (`list`)

- Stores multiple elements in an ordered collection.
- Can contain different data types.
- Lists are mutable, meaning their contents can be modified.

Example:

```python
my_list = [10, "GeneA", True]

print(my_list)
print(type(my_list))
```

Output:

```text
[10, 'GeneA', True]
<class 'list'>
```

#### c. Tuple (`tuple`)

- Stores multiple elements in an ordered collection.
- Can contain different data types.
- Tuples are immutable, meaning their elements cannot be modified after creation.

Example:

```python
my_tuple = (10, "GeneA", True)

print(my_tuple)
print(type(my_tuple))
```

Output:

```text
(10, 'GeneA', True)
<class 'tuple'>
```

### 4. Set (`set`)

- Stores unique elements.
- Duplicate values are automatically removed.
- Sets are unordered collections and do not support positional indexing.

Example:

```python
my_set = {1, 2, 2, 3, 4}

print(my_set)
print(type(my_set))
```

Output:

```text
{1, 2, 3, 4}
<class 'set'>
```

The order of displayed elements is not guaranteed.

### 5. Dictionary (`dict`)

- Stores information in key-value pairs.
- Each key is associated with a corresponding value.
- Keys must be unique.

Example:

```python
student = {
    "name": "Deepti",
    "age": 23,
    "course": "Biotechnology"
}

print(student)
print(type(student))
```

Output:

```text
{'name': 'Deepti', 'age': 23, 'course': 'Biotechnology'}
<class 'dict'>
```

### Summary of Python Data Types

| Category | Data type | Example |
|---|---|---|
| Numeric | Integer | `10` |
| Numeric | Float | `10.5` |
| Numeric | Complex | `2 + 3j` |
| Boolean | Boolean | `True` |
| Sequence | String | `"Hello"` |
| Sequence | List | `[1, 2, 3]` |
| Sequence | Tuple | `(1, 2, 3)` |
| Set | Set | `{1, 2, 3}` |
| Mapping | Dictionary | `{"name": "Deepti"}` |

---

## 10. Checking Data Types

The `type()` function is used to identify the data type of a value or variable.

### Syntax

```python
type(variable_name)
```

### Example

```python
age = 21

print(type(age))
```

Output:

```text
<class 'int'>
```

### More Examples

```python
name = "Deepti"
temperature = 37.5
result = True

print(type(name))
print(type(temperature))
print(type(result))
```

Output:

```text
<class 'str'>
<class 'float'>
<class 'bool'>
```

**Where to use:**

- Checking the type of a variable.
- Understanding the structure of stored data.
- Identifying unexpected data types during data processing.

---

# PART C: INPUT, OUTPUT AND BASIC OPERATIONS

## 11. Basic Input in Python

### Definition

- Input allows a program to receive information from the user.
- Python uses the `input()` function to accept user input.
- The entered information is returned as a string.

### Syntax

```python
variable = input("Message")
```

### Example

```python
name = input("Name: ")

print(name)
```

Example interaction:

```text
Name: Deepti
Deepti
```

**Explanation:**

- `input()` displays the message `Name:`.
- The user enters a value.
- The entered value is stored in the variable `name`.
- `print()` displays the stored value.

**Important:** Even if a user enters a number, `input()` initially returns it as a string.

For example:

```python
age = input("Enter age: ")

print(type(age))
```

Output after entering `21`:

```text
<class 'str'>
```

---

## 12. Basic Output in Python

### Definition

- Output displays the result of a program.
- Python uses the `print()` function to display information.

### Syntax

```python
print(value)
```

### Example

```python
name = "Deepti"

print("Hello", name)
```

Output:

```text
Hello Deepti
```

### Printing Multiple Values

```python
a = 10
b = 5

print(a, b)
```

Output:

```text
10 5
```

The `print()` function can display text, variables and calculated values.

---

## 13. Basic Operations in Python

Python supports arithmetic and comparison operations.

### Example

```python
a = 10
b = 5

print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a > b)
```

### Output

```text
15
5
50
2.0
True
```

### Explanation of Operators

| Operator | Operation | Example | Result |
|---|---|---|---|
| `+` | Addition | `10 + 5` | `15` |
| `-` | Subtraction | `10 - 5` | `5` |
| `*` | Multiplication | `10 * 5` | `50` |
| `/` | Division | `10 / 5` | `2.0` |
| `>` | Greater than | `10 > 5` | `True` |

**Important:** The `/` operator performs division and returns a floating-point result, even when the result is a whole number.

---

# PART D: STRINGS IN PYTHON

## 14. Strings

### Definition

- A string is an immutable sequence of Unicode characters.
- It is used to represent textual data.
- Strings can contain letters, numbers, spaces and symbols.
- Python supports Unicode by default, allowing strings to represent characters from different languages and symbol systems.

### Creating Strings

Strings can be created using:

1. Single quotes.
2. Double quotes.
3. Triple quotes.

### Example

```python
text1 = 'Hello'
text2 = "Hello"
text3 = """Hello"""
```

All three examples create string values.

### Triple-Quoted Strings

Triple quotes can also be used for multiline strings.

```python
message = """Hello
Welcome to Python
Programming"""

print(message)
```

Output:

```text
Hello
Welcome to Python
Programming
```

---

## 15. Indexing in Strings

### Definition

- Indexing is used to access individual characters in a string.
- Python uses zero-based indexing.
- This means indexing starts from `0`, not `1`.
- Every character is assigned a position.

### Example

```python
text = "Python"
```

| Character | P | y | t | h | o | n |
|---|---:|---:|---:|---:|---:|---:|
| Positive index | 0 | 1 | 2 | 3 | 4 | 5 |
| Negative index | -6 | -5 | -4 | -3 | -2 | -1 |

### Accessing the First Character

```python
print(text[0])
```

Output:

```text
P
```

### Accessing the Last Character

```python
print(text[-1])
```

Output:

```text
n
```

**Explanation:**

- Positive indexing starts from the beginning.
- Negative indexing starts from the end.
- `-1` refers to the last character.

---

## 16. Slicing Strings

### Definition

- Slicing is used to extract a portion of a string.
- It allows multiple characters to be accessed at once.
- Slicing uses the `[start:end]` syntax.

### Syntax

```python
string[start:end]
```

- `start` specifies the starting index.
- `end` specifies the stopping index.
- The character at the ending index is not included.

### Example 1: Extracting the First Four Characters

```python
text = "Python"

print(text[0:4])
```

Output:

```text
Pyth
```

**Explanation:**

- Starts at index 0.
- Stops before index 4.
- Extracts characters at positions 0, 1, 2 and 3.

### Example 2: Extracting Characters from the Third Position

```python
text = "Python"

print(text[2:])
```

Output:

```text
thon
```

**Explanation:**

- Starts at index 2.
- No ending index is specified.
- Therefore, Python extracts characters from index 2 until the end of the string.

### Important Difference Between Indexing and Slicing

| Indexing | Slicing |
|---|---|
| Accesses an individual character | Extracts a portion of a string |
| Uses one index | Uses a start and end position |
| Example: `text[0]` | Example: `text[0:4]` |

---

## 17. Common String Methods

Python provides built-in string methods to modify or process text.

**Important:** String methods return a new string. They do not directly modify the original string because strings are immutable.

### 1. upper()

Converts all characters in a string to uppercase.

```python
text = "python"

print(text.upper())
```

Output:

```text
PYTHON
```

### 2. lower()

Converts all characters in a string to lowercase.

```python
text = "PYTHON"

print(text.lower())
```

Output:

```text
python
```

### 3. replace()

Replaces a specified part of a string with another value.

### Syntax

```python
string.replace(old_value, new_value)
```

### Example

```python
sentence = "I like Sril"

print(sentence.replace("Sril", "Journis"))
```

Output:

```text
I like Journis
```

**Explanation:**

- `"Sril"` is the text to be replaced.
- `"Journis"` is the replacement text.
- The method returns the updated string.

### 4. len()

Returns the number of characters in a string.

### Syntax

```python
len(string)
```

### Example

```python
password = "deepti123"

print(len(password))
```

Output:

```text
9
```

### Example: Checking String Length

```python
password = "deepti123"

if len(password) < 8:
    print("Password too short")
```

Output:

```text
Password too short
```

**Explanation:**

- `len(password)` calculates the number of characters.
- `< 8` checks whether the length is less than 8.
- If the condition is true, the message is displayed.

**Note:** This is a basic demonstration of checking string length, not a complete password validation method.

### 5. strip()

Removes leading and trailing whitespace from a string.

```python
text = "   Hello World   "

print(text.strip())
```

Output:

```text
Hello World
```

**Explanation:**

- Leading spaces are spaces before the text.
- Trailing spaces are spaces after the text.
- `strip()` removes these spaces.

### 6. title()

Converts the first character of each word to uppercase.

```python
text = "hello world"

print(text.title())
```

Output:

```text
Hello World
```

### Combining strip() and title()

```python
text = input("Enter your text: ")

print(text.strip().title())
```

Example interaction:

```text
Enter your text:    hello world

Hello World
```

**Explanation:**

1. `input()` accepts text from the user.
2. `strip()` removes extra spaces at the beginning and end.
3. `title()` capitalises the first character of each word.
4. `print()` displays the final result.

---

# PART E: COMMON SYNTAX MISTAKES

## 18. Common Python Syntax Mistakes

### 1. Indentation

Python uses indentation to define code blocks.

Incorrect:

```python
if age > 18:
print("Adult")
```

Correct:

```python
if age > 18:
    print("Adult")
```

The statement inside the `if` block must be indented.

### 2. Case Sensitivity

Python is case-sensitive.

Incorrect:

```python
Name = "Deepti"

print(name)
```

Correct:

```python
name = "Deepti"

print(name)
```

`Name` and `name` are different variables.

### 3. Incorrect Quotation Marks

Strings must be enclosed in valid matching quotation marks.

Correct:

```python
print("Hello")
print('Hello')
print("""Hello""")
```

Incorrect:

```python
print("Hello')
```

The opening and closing quotation marks do not match.

### 4. Incorrect Punctuation

Python syntax depends on correctly placed brackets, quotation marks, commas and colons.

Correct:

```python
print("Hello")
```

Incorrect:

```python
print("Hello"
```

The closing parenthesis is missing.

---

## 19. Quick Revision: Important Functions and Methods

| Function / Method | Purpose | Example |
|---|---|---|
| `print()` | Displays output | `print("Hello")` |
| `input()` | Accepts user input | `input("Name: ")` |
| `type()` | Identifies data type | `type(age)` |
| `exit()` | Exits the interactive interpreter | `exit()` |
| `upper()` | Converts text to uppercase | `text.upper()` |
| `lower()` | Converts text to lowercase | `text.lower()` |
| `replace()` | Replaces specified text | `text.replace("A", "B")` |
| `len()` | Returns the length | `len(text)` |
| `strip()` | Removes leading and trailing whitespace | `text.strip()` |
| `title()` | Capitalises the first character of each word | `text.title()` |

---

## 20. Important Concepts to Remember

1. Why is Python used in research and data analysis?
2. What is the purpose of Python PATH?
3. What is the difference between the Python interpreter and VS Code?
4. How is Python code executed?
5. Why is Python called a case-sensitive language?
6. What is indentation?
7. What is a variable?
8. What is dynamic typing?
9. What are the variable naming rules?
10. What are the different built-in Python data types covered in this session?
11. What is the purpose of the `type()` function?
12. What is the difference between input and output?
13. What is the purpose of `input()` and `print()`?
14. What are the basic arithmetic operators?
15. What is a string?
16. Why are strings called immutable?
17. What is the difference between indexing and slicing?
18. What is zero-based indexing?
19. What is the purpose of `upper()` and `lower()`?
20. What is the purpose of `replace()`?
21. What does `len()` return?
22. What is the purpose of `strip()` and `title()`?

---

## 21. Session 1 Completion Checklist

- [ ] Understand why Python is important.
- [ ] Understand Python installation and PATH.
- [ ] Understand how to run Python through CMD.
- [ ] Understand the role of VS Code.
- [ ] Understand Python execution flow.
- [ ] Understand variables and dynamic typing.
- [ ] Follow variable naming rules.
- [ ] Identify Python data types.
- [ ] Use `type()` to check data types.
- [ ] Perform basic input and output operations.
- [ ] Perform basic arithmetic operations.
- [ ] Understand strings and string creation.
- [ ] Understand indexing and slicing.
- [ ] Use common string methods.
- [ ] Identify common syntax mistakes.

---

**End of Session 1: Introduction to Python**