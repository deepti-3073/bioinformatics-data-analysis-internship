# Module 5: File Handling and Error Management

## Session 5: File Handling and Error Management

## 1. Objectives

- Read data from files.
- Write data to files.
- Use context managers (`with`).
- Handle runtime errors using exceptions.
- Debug code.
- Build robust programs.

---

# PART A: FILE HANDLING

## 2. File Handling

### Definition

- File handling allows Python programs to interact with files stored on a computer.
- It enables programs to read existing data, write new data and store information permanently.
- It is important when working with external datasets and organising files.

### Why Is File Handling Important?

File handling allows programs to:

1. **Store persistent data:** Data can be saved in files and accessed later, even after the program has stopped running.
2. **Read external datasets:** Programs can retrieve information stored in files.
3. **Generate reports:** Results obtained through data processing can be written into files.
4. **Process real-world inputs:** Programs can work with data stored outside the Python script.

### Basic File Handling Workflow

```text
Read data from file
        |
        v
Process the data
        |
        v
Write results to a new file
```

### Example

Consider a program that analyses gene expression data.

1. The program reads the expression values from a file.
2. It processes the values and calculates the required results.
3. It writes the results into an output file.

Python provides built-in support for file operations.

---

## 3. Current Working Directory

### Definition

- The current working directory is the folder from which Python is currently working.
- When a file is opened using only its filename, Python generally looks for it in the current working directory.
- Similarly, files created using a relative filename are saved in the current working directory.

### Using the os Library

Python provides the `os` library to interact with the operating system.

The `os` library can be used to find the current working directory and list the files present in it.

### Example 1: Finding the Current Working Directory

```python
import os

print(os.getcwd())
```

**Example Output:**

```text
C:\Users\Deepti\OneDrive\Documents
```

### Explanation

- `import os` imports the operating system library.
- `os.getcwd()` retrieves the current working directory.
- `print()` displays the directory path.

### Example 2: Listing Files in the Current Directory

```python
import os

print(os.listdir())
```

**Output:**

The output displays a list of files and folders present in the current working directory.

### Explanation

- `os.listdir()` retrieves the names of files and directories.
- It is useful for checking which files are available in the current working directory.

**Important:** If a file is not in the current working directory, Python may not be able to find it using only its filename. In that case, the correct file path must be provided.

---

## 4. Opening and Closing Files

### open() Function

**Definition:**

- The `open()` function is used to open a file in Python.
- It returns a file object that can be used to read or write data.
- The file must be opened in the appropriate mode depending on the operation.

### Syntax

```python
file = open("filename.txt", "mode")
```

Where:

- `file` is the variable used to store the file object.
- `filename.txt` is the name of the file.
- `mode` specifies how the file should be opened.

### Example: Opening a File in Read Mode

```python
file = open("data.txt", "r")

print(file.read())

file.close()
```

**Explanation:**

1. `open("data.txt", "r")` opens the file in read mode.
2. The file object is stored in the variable `file`.
3. `file.read()` retrieves the contents of the file.
4. `print()` displays the contents.
5. `file.close()` closes the file after use.

### close() Function

**Definition:**

- `close()` closes an opened file.
- It releases the resources associated with the file.
- It is important to close files after completing file operations.

### Syntax

```python
file.close()
```

### Important Rules

- A file must exist when opening it in read mode (`r`).
- Files should be closed after completing operations when using the regular `open()` method.
- The `with open()` statement can manage file closing automatically.

---

## 5. File Opening Modes

The mode determines what operations can be performed on a file.

| Mode | Meaning | Purpose |
|---|---|---|
| `r` | Read | Reads an existing file |
| `w` | Write | Writes data and overwrites existing content |
| `a` | Append | Adds content to the end of a file |
| `r+` | Read and write | Allows both reading and writing |

### 1. Read Mode (`r`)

- Opens a file for reading.
- The file must already exist.
- It does not overwrite the file contents.

Example:

```python
file = open("data.txt", "r")

print(file.read())

file.close()
```

### 2. Write Mode (`w`)

- Opens a file for writing.
- If the file already exists, its previous contents are overwritten.
- If the file does not exist, Python creates a new file.

Example:

```python
file = open("output.txt", "w")

file.write("Python File Handling Example")

file.close()
```

### 3. Append Mode (`a`)

- Opens a file for adding content.
- New content is added to the end of the existing file.
- Previous contents are preserved.
- If the file does not exist, Python creates it.

Example:

```python
file = open("output.txt", "a")

file.write("\nNew line added")

file.close()
```

### 4. Read and Write Mode (`r+`)

- Opens an existing file for both reading and writing.
- The file must already exist.
- It does not automatically erase the existing contents.

Example:

```python
file = open("data.txt", "r+")

print(file.read())

file.close()
```

### Important Difference Between File Modes

| Mode | Reads | Writes | Creates file if missing | Overwrites existing contents |
|---|---|---|---|---|
| `r` | Yes | No | No | No |
| `w` | No | Yes | Yes | Yes |
| `a` | No | Yes | Yes | No |
| `r+` | Yes | Yes | No | No |

---

# PART B: READING DATA FROM FILES

## 6. Reading from a File

Python provides different methods to read the contents of a file.

The three methods covered in this session are:

1. `read()`
2. `readline()`
3. `readlines()`

### 1. read()

**Definition:**

- `read()` reads the entire contents of a file.
- It returns the contents as a single string.
- It is useful when the complete file content needs to be retrieved at once.

### Syntax

```python
file.read()
```

### Example

```python
file = open("data.txt", "r")

content = file.read()

print(content)

file.close()
```

**Output:**

Displays the entire content of `data.txt`.

### Explanation

- `file.read()` retrieves all the contents.
- The retrieved content is stored in the variable `content`.
- `print(content)` displays the complete file content.
- `file.close()` closes the file.

### 2. readline()

**Definition:**

- `readline()` reads one line from a file at a time.
- Each time it is called, it reads the next line.
- It is useful when processing a file line by line.

### Syntax

```python
file.readline()
```

### Example

```python
file = open("data.txt", "r")

print(file.readline())

file.close()
```

**Output:**

Displays the first line of the file.

### Explanation

- `readline()` retrieves one line.
- In this example, the first line is read because it is the first call.
- If `readline()` is called again on the same open file, it reads the next line.

### Example: Reading Multiple Lines

```python
file = open("data.txt", "r")

print(file.readline())
print(file.readline())

file.close()
```

This displays the first two lines of the file.

### 3. readlines()

**Definition:**

- `readlines()` reads all the lines in a file.
- It returns the lines as a list of strings.
- Each line is stored as an individual element in the list.

### Syntax

```python
file.readlines()
```

### Example

```python
file = open("data.txt", "r")

lines = file.readlines()

print(lines)

file.close()
```

**Example Output:**

```python
['First line\n', 'Second line\n', 'Third line\n']
```

### Explanation

- `readlines()` reads all the lines.
- Each line becomes an element in a list.
- The variable `lines` stores the list.
- `print()` displays the list.

The `\n` represents a newline character, which indicates the end of a line.

### Difference Between read(), readline() and readlines()

| Method | What it reads | Return type |
|---|---|---|
| `read()` | Entire file content | String |
| `readline()` | One line at a time | String |
| `readlines()` | All lines | List of strings |

### Important Point

After reading from a file, Python maintains the current reading position.

For example:

- The first call to `readline()` reads the first line.
- The next call reads the second line.
- Once the file has been completely read, another read operation may return an empty string or an empty list.

---

# PART C: WRITING DATA TO FILES

## 7. Writing to a File

Python allows us to write data into files using the `write()` method.

There are two writing modes covered in this session:

1. Write mode (`w`).
2. Append mode (`a`).

### 1. Write Mode (Overwriting a File)

**Definition:**

- Write mode is used to write new content into a file.
- If the file already contains data, the previous content is erased.
- If the file does not exist, Python creates it.

### Example

```python
with open("output.txt", "w") as file:
    file.write("Python File Handling Example")
```

**Explanation:**

- `open("output.txt", "w")` opens the file in write mode.
- `as file` stores the file object in the variable `file`.
- `file.write()` writes the specified text into the file.
- The previous content is overwritten if the file already exists.

### 2. Append Mode (Adding Content)

**Definition:**

- Append mode adds new content to the end of an existing file.
- It preserves the previous content.
- It is useful when new information needs to be added without deleting existing data.

### Example

```python
with open("output.txt", "a") as file:
    file.write("\nNew line added")
```

**Explanation:**

- The file is opened in append mode.
- The new text is added at the end.
- `\n` moves the new content to a new line.

### Difference Between Write and Append Modes

| Write Mode (`w`) | Append Mode (`a`) |
|---|---|
| Writes new content | Adds new content |
| Overwrites existing content | Preserves existing content |
| Creates the file if missing | Creates the file if missing |
| Useful for creating a fresh output file | Useful for adding new records or results |

---

## 8. Context Manager: with open()

### Definition

- A context manager manages resources automatically.
- In file handling, `with open()` is used to open and manage a file.
- The file is automatically closed when the `with` block finishes, even if an error occurs inside the block.

### Syntax

```python
with open("filename.txt", "mode") as file:
    statement
```

### Example

```python
with open("output.txt", "w") as file:
    file.write("Python File Handling Example")
```

### Explanation

1. `with` begins the context manager.
2. `open()` opens the specified file.
3. `as file` assigns the file object to the variable `file`.
4. The indented code performs the file operation.
5. When the block ends, Python automatically closes the file.

### Benefits of Using with open()

- Cleaner and more readable code.
- Automatic resource management.
- Prevents files from being left open accidentally.
- Reduces the possibility of file-related resource leaks.

### Difference Between Regular open() and with open()

| Regular `open()` | `with open()` |
|---|---|
| File is opened manually | File is opened within a context manager |
| Requires `file.close()` | Closes the file automatically |
| The programmer must remember to close the file | Automatic resource management |
| More manual handling | Cleaner and safer file handling |

**Important:** The `with` block automatically closes the file when execution leaves the block. The file should not be used outside the block.

---

# PART D: EXCEPTION HANDLING

## 9. Exceptions

### Definition

- An exception is an error that occurs during program execution.
- Exceptions interrupt the normal flow of a program unless they are handled.
- Exception handling allows a program to respond to errors instead of terminating unexpectedly.

### Why Is Exception Handling Important?

- It helps identify what error has occurred.
- It prevents unexpected errors from interrupting normal program execution.
- It allows the program to display meaningful error messages.
- It helps build robust programs.

### Examples of Errors

1. **FileNotFoundError:** Occurs when a program tries to open a file that does not exist.
2. **ZeroDivisionError:** Occurs when a number is divided by zero.
3. **Invalid input:** Occurs when the input cannot be converted into the required data type, such as entering text where an integer is expected.

---

## 10. try-except Block

### Definition

- The `try-except` block is used to handle exceptions.
- The code that may produce an error is placed inside the `try` block.
- The `except` block contains the code that executes if an exception occurs.

### Syntax

```python
try:
    risky_code

except:
    error_handling_code
```

### Explanation

- `try` contains the statements that may cause an exception.
- `except` handles the exception if one occurs.
- If no exception occurs, the `except` block is skipped.

### Example: Division by Zero

```python
try:
    num = int(input("Enter number: "))
    print(10 / num)

except:
    print("Error occurred")
```

### Example Output 1: Valid Input

```text
Enter number: 45
0.2222222222222222
```

### Example Output 2: Input Is Zero

```text
Enter number: 0
Error occurred
```

### Explanation

1. The program asks the user to enter a number.
2. `int()` converts the input into an integer.
3. The program attempts to divide 10 by the entered number.
4. If the input is 45, the division succeeds.
5. If the input is 0, Python raises a `ZeroDivisionError`.
6. The `except` block handles the error and displays the message.

**Important:** A general `except` block catches many types of exceptions. Using specific exception types makes error handling more precise.

---

## 11. Handling Specific Exceptions

### Definition

- Python allows us to handle different types of exceptions separately.
- This makes it possible to display different messages depending on the error.
- Specific exceptions help us understand what went wrong.

### Example

```python
try:
    num = int(input("Enter number: "))
    print(10 / num)

except ZeroDivisionError:
    print("Cannot divide by zero")

except ValueError:
    print("Invalid input")
```

### Example Output 1: Valid Input

```text
Enter number: 45
0.2222222222222222
```

### Example Output 2: Input Is Zero

```text
Enter number: 0
Cannot divide by zero
```

### Example Output 3: Invalid Input

```text
Enter number: z
Invalid input
```

### Explanation

**ZeroDivisionError:**

- Occurs when the denominator is zero.
- Python cannot perform division by zero.
- The corresponding `except` block displays the message.

**ValueError:**

- Occurs when a value cannot be converted into the required type.
- In this example, `int("z")` raises a `ValueError`.
- The corresponding `except` block displays "Invalid input".

### Why Use Specific Exceptions?

- Different errors can be identified separately.
- More meaningful error messages can be displayed.
- It becomes easier to understand and debug the program.

---

## 12. Debugging Errors

### Definition

- Debugging is the process of identifying and correcting errors in a program.
- It helps locate problems in code and ensures that the program behaves as expected.

### Steps to Debug Errors

1. **Read the error message carefully:** Understand what type of error has occurred.
2. **Check the line number:** Identify the location mentioned in the error message.
3. **Verify variable names and indentation:** Check for spelling mistakes and incorrect indentation.
4. **Print intermediate values:** Use `print()` to check values at different stages of execution.
5. **Use try-except:** Handle errors that may occur during program execution.

### Importance of Debugging

- Helps identify mistakes.
- Makes programs more reliable.
- Helps understand why a program is not working as expected.
- Improves the accuracy of program execution.

---

# PART E: FINALLY BLOCK

## 13. finally Block with try-except

### Definition

- The `finally` block is used with exception handling.
- It contains code that executes whether an exception occurs or not.
- It is commonly used for operations that should happen regardless of whether the program succeeds or encounters an error.

### Syntax

```python
try:
    risky_code

except:
    error_handling_code

finally:
    code_that_always_executes
```

### Example: Reading a File

```python
try:
    file = open("data.txt", "r")
    print(file.read())

except FileNotFoundError:
    print("File not found")

finally:
    print("Execution completed")
```

### Example Output 1: File Exists

```text
Contents of data.txt

Execution completed
```

### Example Output 2: File Does Not Exist

```text
File not found
Execution completed
```

### Explanation

1. Python enters the `try` block.
2. It attempts to open `data.txt`.
3. If the file exists, Python reads and displays its contents.
4. If the file does not exist, a `FileNotFoundError` occurs.
5. The `except` block handles the error and displays "File not found".
6. The `finally` block executes in either case.
7. Therefore, "Execution completed" is displayed regardless of whether an exception occurred.

**Important:** The `finally` block executes whether an exception occurs or not, making it useful for cleanup operations.

For file handling, `with open()` is generally preferred because it automatically closes the file.

---

# PART F: CUSTOM EXCEPTIONS

## 14. raise Statement

### Definition

- The `raise` statement is used to deliberately generate an exception.
- It allows the programmer to define conditions under which the program should report an error.
- It is useful when a value is technically valid as a data type but is not acceptable for the program.

### Example: Age Validation

```python
age = int(input("Enter age: "))

if age < 0:
    raise ValueError("Age cannot be negative")
```

### Example Input

```text
Enter age: -21
```

### Output

```text
ValueError: Age cannot be negative
```

### Explanation

1. The program asks the user to enter an age.
2. `int()` converts the input into an integer.
3. The `if` statement checks whether the age is less than zero.
4. If the condition is true, `raise` generates a `ValueError`.
5. The custom error message explains why the value is unacceptable.

### Why Use raise?

- To validate input values.
- To prevent invalid data from being processed.
- To generate meaningful error messages.
- To make error handling more specific.

**Important:** In this example, a negative age can be converted into an integer, but it is not a valid age for the program. The `raise` statement allows us to reject it explicitly.

---

## 15. Quick Revision: Important Functions, Modes and Keywords

### File Handling Functions and Methods

| Function / Method | Purpose |
|---|---|
| `open()` | Opens a file |
| `close()` | Closes an opened file |
| `read()` | Reads the entire file |
| `readline()` | Reads one line |
| `readlines()` | Reads all lines into a list |
| `write()` | Writes content into a file |
| `os.getcwd()` | Returns the current working directory |
| `os.listdir()` | Lists files and directories in the current directory |

### File Modes

| Mode | Purpose |
|---|---|
| `r` | Read |
| `w` | Write and overwrite |
| `a` | Append |
| `r+` | Read and write |

### Exception Handling Keywords

| Keyword | Purpose |
|---|---|
| `try` | Contains code that may produce an exception |
| `except` | Handles an exception |
| `finally` | Executes regardless of whether an exception occurs |
| `raise` | Deliberately generates an exception |

### Common Exceptions Covered

| Exception | Meaning |
|---|---|
| `FileNotFoundError` | The specified file does not exist |
| `ZeroDivisionError` | Division by zero |
| `ValueError` | An inappropriate value was supplied for an operation |

---

## 16. Important Concepts to Remember

1. What is file handling?
2. Why is file handling important?
3. What is the current working directory?
4. What is the purpose of the `os` library?
5. What is the purpose of `os.getcwd()`?
6. What is the purpose of `os.listdir()`?
7. What is the purpose of `open()`?
8. What is the purpose of `close()`?
9. What are the different file opening modes?
10. What is the difference between `r`, `w`, `a` and `r+`?
11. What is the purpose of `read()`?
12. What is the difference between `read()`, `readline()` and `readlines()`?
13. What is the purpose of `write()`?
14. What is the difference between write mode and append mode?
15. What is a context manager?
16. What is the purpose of `with open()`?
17. What is an exception?
18. Why is exception handling important?
19. What is the purpose of the `try-except` block?
20. What is the difference between a general exception and a specific exception?
21. What is debugging?
22. What are the steps involved in debugging?
23. What is the purpose of the `finally` block?
24. What is the purpose of the `raise` statement?
25. How can invalid input values be handled?

---

## 17. Session 5 Completion Checklist

### File Handling

- [ ] Understand file handling.
- [ ] Understand the current working directory.
- [ ] Use the `os` library.
- [ ] Find the current working directory using `os.getcwd()`.
- [ ] List files using `os.listdir()`.
- [ ] Open files using `open()`.
- [ ] Understand file opening modes.
- [ ] Close files using `close()`.

### Reading and Writing Files

- [ ] Read entire file contents using `read()`.
- [ ] Read individual lines using `readline()`.
- [ ] Read all lines using `readlines()`.
- [ ] Write data using write mode (`w`).
- [ ] Add data using append mode (`a`).
- [ ] Understand the difference between write and append modes.
- [ ] Use `with open()`.

### Exception Handling

- [ ] Understand exceptions.
- [ ] Use `try-except`.
- [ ] Handle `ZeroDivisionError`.
- [ ] Handle `ValueError`.
- [ ] Handle `FileNotFoundError`.
- [ ] Understand debugging.
- [ ] Use the `finally` block.
- [ ] Use the `raise` statement.

---

**End of Session 5: File Handling and Error Management**

**End of Python Module**