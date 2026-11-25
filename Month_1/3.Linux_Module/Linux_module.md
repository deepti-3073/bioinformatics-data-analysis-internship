# Linux Foundations for Bioinformatics

# Module 1: Linux Foundations

## 1. Learning Objectives

- Navigate the Linux filesystem confidently.
- Understand the Linux directory structure.
- Understand file permissions.
- Use core command-line tools.
- Process a real FASTA dataset manually.
- Combine commands using pipes.

---

## 2. Introduction to Linux

### What is Linux?

- Linux is an open-source, Unix-like operating system.
- It is widely used in scientific computing, programming, servers and bioinformatics.
- Linux provides a command-line interface (CLI) that allows users to interact with the operating system through commands.

### Why is Linux Important for Bioinformatics?

Linux is commonly used in bioinformatics because:

1. **Compatibility:** Most bioinformatics tools support Linux.
2. **High-performance computing:** HPC clusters commonly use Linux to process large datasets.
3. **Command-line tools:** Many bioinformatics applications are designed to run through the terminal.
4. **Automation:** Repetitive analyses can be automated using shell scripts.
5. **Pipeline execution:** Multiple commands can be combined to process large datasets efficiently.

### What is a Terminal?

- A terminal is an interface through which users communicate with the operating system using text-based commands.
- Instead of using a graphical interface to open folders, copy files or run programs, users can perform these operations through commands.

### What is a Shell?

- A shell is a program that interprets commands entered by the user and communicates with the operating system.
- Bash (Bourne Again SHell) is one of the most commonly used shells in Linux.

**Difference:**

| Terminal | Shell |
|---|---|
| Provides the interface where commands are entered | Interprets and executes commands |
| Acts as the communication window | Processes the commands |
| Example: Terminal application | Example: Bash |

---

## 3. Linux Directory Structure

Linux uses a hierarchical filesystem structure.

- The top-level directory is called the root directory.
- It is represented by `/`.
- All files and directories are organised under the root directory.

### Important Linux Directories

| Directory | Purpose |
|---|---|
| `/` | Root directory; the starting point of the filesystem |
| `/home` | Contains users' personal directories and files |
| `/bin` | Contains essential command binaries on traditional Linux layouts |
| `/usr` | Contains user applications, libraries and shared resources |
| `/etc` | Contains system-wide configuration files |
| `/tmp` | Stores temporary files |
| `/var` | Stores variable data such as logs and caches |

### Example Directory Structure

```text
/
├── home/
│   └── user/
│       ├── Documents/
│       ├── Downloads/
│       └── Projects/
├── bin/
├── usr/
├── etc/
├── tmp/
└── var/
```

### What is a Path?

- A path is the address or location of a file or directory in the filesystem.
- It tells the operating system where a particular file or directory is located.

Example:

```text
/home/user/Documents/notes.txt
```

This path indicates that `notes.txt` is located inside the Documents directory of the user directory.

---

## 4. Absolute Path vs Relative Path

### 1. Absolute Path

**Definition:**

- An absolute path specifies the complete location of a file or directory.
- It starts from the root directory `/`.
- It does not depend on the current working directory.

Example:

```text
/home/user/Documents/notes.txt
```

Even if the current working directory changes, this path continues to identify the same location.

### 2. Relative Path

**Definition:**

- A relative path specifies the location of a file or directory in relation to the current working directory.
- It does not begin from the root directory.
- Its meaning depends on the current working directory.

Example:

```text
data/raw/file.fasta
```

If the current working directory is `/home/user/Projects`, this relative path refers to:

```text
/home/user/Projects/data/raw/file.fasta
```

### Difference Between Absolute and Relative Paths

| Absolute Path | Relative Path |
|---|---|
| Starts from `/` | Starts from the current working directory |
| Specifies the complete location | Specifies a location relative to the current directory |
| Independent of the current directory | Depends on the current directory |
| Example: `/home/user/data/file.fasta` | Example: `data/file.fasta` |

---

# PART A: BASIC LINUX NAVIGATION

## 5. Current Working Directory: pwd

### Definition

- `pwd` stands for Print Working Directory.
- It displays the current directory in which the terminal is working.

### Syntax

```bash
pwd
```

### Example Output

```text
/home/user
```

This means the terminal is currently working inside the user's home directory.

**When to use:**

- To check your current location.
- Before running file operations.
- When you are unsure which directory you are working in.

---

## 6. Listing Files and Directories: ls

### Definition

- `ls` lists files and directories present in the specified location.
- If no path is provided, it displays the contents of the current working directory.

### Basic Syntax

```bash
ls
```

### Common Variations

**1. List files in a specific directory**

```bash
ls /home/user/Documents
```

**2. Long listing format**

```bash
ls -l
```

Displays additional information such as permissions, ownership, file size and modification date.

**3. Human-readable file sizes**

```bash
ls -lh
```

Displays file sizes in readable units such as KB, MB and GB.

**4. Display hidden files**

```bash
ls -a
```

Hidden files in Linux generally have names beginning with a dot (`.`).

**5. Combine options**

```bash
ls -lah
```

Displays hidden files, detailed information and human-readable file sizes.

### When to use ls

- To check which files are present in a directory.
- To verify whether a file has been created.
- To inspect file sizes and modification dates.
- To identify hidden files.

---

## 7. Changing Directories: cd

### Definition

- `cd` stands for Change Directory.
- It is used to move from one directory to another.

### Basic Syntax

```bash
cd directory_name
```

### Common cd Commands

**1. Enter a directory**

```bash
cd Documents
```

Moves into the Documents directory, if it is present inside the current directory.

**2. Move to the parent directory**

```bash
cd ..
```

Moves one level up from the current directory.

**3. Stay in the current directory**

```bash
cd .
```

The dot (`.`) represents the current directory.

Therefore, `cd .` keeps you in the same location.

**4. Move to the home directory**

```bash
cd ~
```

The tilde (`~`) represents the user's home directory.

**5. Return to the previous working directory**

```bash
cd -
```

Switches to the previous working directory.

**6. Move to the root directory**

```bash
cd /
```

Moves to the root directory.

**7. Move using an absolute path**

```bash
cd /home/user/Documents
```

Moves directly to the specified location.

### Understanding . and ..

| Symbol | Meaning |
|---|---|
| `.` | Current directory |
| `..` | Parent directory |
| `~` | User's home directory |
| `/` | Root directory |
| `-` | Previous working directory |

### Example Navigation

Assume the current directory is:

```text
/home/user/Projects
```

Command:

```bash
cd ..
```

New location:

```text
/home/user
```

Command:

```bash
cd .
```

Location remains:

```text
/home/user/Projects
```

---

## 8. Displaying Directory Structure: tree

### Definition

- `tree` displays files and directories in a hierarchical, tree-like structure.
- It helps users understand how folders are organised.

### Syntax

```bash
tree
```

### Example

```text
Projects/
├── R/
│   └── analysis.R
├── Python/
│   └── script.py
└── Data/
    └── sample.fasta
```

### Display a Specific Directory

```bash
tree Projects/
```

### Important

The `tree` command may not be installed by default on every Linux distribution.

---

## 9. Checking Directory Size: du

### Definition

- `du` stands for Disk Usage.
- It displays the amount of disk space used by files and directories.

### Common Commands

**1. Display directory size**

```bash
du directory_name
```

**2. Display human-readable sizes**

```bash
du -h directory_name
```

**3. Display the total size of a directory**

```bash
du -sh directory_name
```

### Example

```bash
du -sh data/
```

Example output:

```text
250M    data/
```

This indicates that the directory uses approximately 250 MB of disk space.

**When to use:**

- To check how much storage a dataset occupies.
- To identify large directories.
- To monitor storage usage when working with genomic datasets.

---

# PART B: CREATING AND MANAGING FILES

## 10. Creating Directories: mkdir

### Definition

- `mkdir` stands for Make Directory.
- It creates a new directory.

### Syntax

```bash
mkdir directory_name
```

### Example

```bash
mkdir Projects
```

Creates a directory called `Projects` in the current working directory.

### Creating Multiple Directories

```bash
mkdir R Python Linux
```

Creates three directories.

### Creating Nested Directories

```bash
mkdir -p Projects/Bioinformatics/Data/Raw
```

- The `-p` option creates parent directories when necessary.
- It is useful when creating multiple levels of directories at once.

### When to use mkdir

- To organise project files.
- To separate raw data, processed data and results.
- To create folders for scripts and documentation.

---

## 11. Creating Files: touch

### Definition

- `touch` creates an empty file if the file does not already exist.
- If the file already exists, it updates its modification timestamp.

### Syntax

```bash
touch filename
```

### Examples

**1. Create a text file**

```bash
touch notes.txt
```

**2. Create a Python file**

```bash
touch analysis.py
```

**3. Create an R script**

```bash
touch analysis.R
```

**4. Create a shell script**

```bash
touch script.sh
```

**5. Create multiple files**

```bash
touch file1.txt file2.txt file3.txt
```

### When to use touch

- To create an empty file.
- To prepare a script before writing code.
- To create placeholder files in a project directory.

---

## 12. Displaying Text: echo

### Definition

- `echo` displays text or variable values in the terminal.
- It is also commonly used when writing simple text into files.

### Syntax

```bash
echo "text"
```

### Examples

**1. Display a message**

```bash
echo "Hello Linux"
```

Output:

```text
Hello Linux
```

**2. Display a number**

```bash
echo 25
```

Output:

```text
25
```

**3. Display a variable**

```bash
name="Deepti"

echo "$name"
```

Output:

```text
Deepti
```

**4. Display the current working directory**

```bash
echo "$PWD"
```

The `$PWD` variable contains the current working directory.

**5. Display a message on a new line**

```bash
echo -e "Hello\nLinux"
```

Output:

```text
Hello
Linux
```

The `-e` option enables interpretation of escape sequences such as `\n` in shells that support this behaviour.

### When to use echo

- To display messages.
- To print variable values.
- To display progress messages in scripts.
- To write simple text into files.

---

## 13. Viewing File Contents: cat

### Definition

- `cat` is used to display the contents of files.
- It can also combine multiple files and display their contents.

### Syntax

```bash
cat filename
```

### Examples

**1. Display a file**

```bash
cat notes.txt
```

Displays the complete contents of `notes.txt`.

**2. Display multiple files**

```bash
cat file1.txt file2.txt
```

Displays the contents of both files.

**3. Combine files into another file**

```bash
cat file1.txt file2.txt > combined.txt
```

Combines the contents of both files and stores the result in `combined.txt`.

**Important:** `cat` displays the entire file, so it may not be suitable for very large files.

---

## 14. Copying Files: cp

### Definition

- `cp` copies files or directories from one location to another.
- The original file remains unchanged.

### Syntax

```bash
cp source destination
```

### Examples

**1. Copy a file**

```bash
cp file1.txt file2.txt
```

Creates a copy of `file1.txt` named `file2.txt`.

**2. Copy a file into another directory**

```bash
cp file1.txt Documents/
```

Copies `file1.txt` into the Documents directory.

**3. Copy a directory recursively**

```bash
cp -r folder1 folder2
```

Copies a directory and its contents.

### When to use cp

- To create backups.
- To copy raw datasets into project directories.
- To duplicate scripts before modifying them.

---

## 15. Moving and Renaming Files: mv

### Definition

- `mv` moves files or directories from one location to another.
- It can also rename files and directories.

### Syntax

```bash
mv source destination
```

### Examples

**1. Rename a file**

```bash
mv old.txt new.txt
```

Renames `old.txt` to `new.txt`.

**2. Move a file into a directory**

```bash
mv sample.fasta Data/
```

Moves `sample.fasta` into the Data directory.

**3. Move and rename a file**

```bash
mv sample.fasta Data/reference.fasta
```

Moves the file into Data and changes its name to `reference.fasta`.

### Difference Between cp and mv

| cp | mv |
|---|---|
| Copies a file | Moves a file |
| Original remains in its location | Original is moved from its previous location |
| Used for duplication and backup | Used for relocation and renaming |

---

## 16. Deleting Files and Directories: rm

### Definition

- `rm` removes files and directories.
- It should be used carefully because deleted files may not be recoverable through a simple undo operation.

### Examples

**1. Delete a file**

```bash
rm notes.txt
```

**2. Delete multiple files**

```bash
rm file1.txt file2.txt
```

**3. Delete a directory and its contents recursively**

```bash
rm -r folder_name
```

**4. Force deletion without interactive confirmation**

```bash
rm -f filename
```

**5. Recursively force-delete a directory**

```bash
rm -rf folder_name
```

### Important Safety Notes

- Always verify the file or directory before deleting it.
- Use `pwd` and `ls` before running deletion commands.
- Avoid using `rm -rf` unless you are absolutely certain of the target.
- Never run destructive commands with an uncertain or empty path.

---

# PART C: FILE PERMISSIONS

## 17. Understanding File Permissions

### Definition

- Linux uses file permissions to control who can read, modify or execute a file.
- Permissions help protect files and control access to system resources.

### Three Basic Permissions

| Permission | Symbol | Meaning |
|---|---|---|
| Read | `r` | Allows viewing file contents |
| Write | `w` | Allows modifying file contents |
| Execute | `x` | Allows executing a file or accessing a directory |

### Three Permission Groups

Permissions are assigned to three categories:

1. **User (u):** The owner of the file.
2. **Group (g):** Users belonging to the file's group.
3. **Others (o):** Everyone else.

### Example of File Permissions

```text
-rwxr-xr--
```

Breakdown:

```text
-   rwx   r-x   r--
|    |     |     |
|   User  Group Others
|
File type
```

Explanation:

- `-` indicates a regular file.
- `rwx` means the owner can read, write and execute.
- `r-x` means the group can read and execute.
- `r--` means others can only read.

### Viewing Permissions

```bash
ls -l
```

Example output:

```text
-rw-r--r-- 1 user user 1200 Nov 25 10:00 notes.txt
```

The first section displays the file type and permissions.

---

## 18. Changing Permissions: chmod

### Definition

- `chmod` stands for Change Mode.
- It is used to modify file permissions.

### Example: Add Execute Permission

```bash
chmod +x script.sh
```

Adds execute permission to the file.

### Example: Remove Write Permission

```bash
chmod -w notes.txt
```

Removes write permission.

### Example: Set Permissions for Specific Groups

```bash
chmod u+x script.sh
```

Adds execute permission for the owner.

```bash
chmod g-w notes.txt
```

Removes write permission for the group.

```bash
chmod o-r notes.txt
```

Removes read permission for others.

### Numeric Permission System

Linux also represents permissions using numbers.

| Permission | Numeric Value |
|---|---|
| Read (`r`) | 4 |
| Write (`w`) | 2 |
| Execute (`x`) | 1 |

Values are added to create the permission for each group.

Examples:

| Permission | Calculation | Value |
|---|---|---|
| Read only | 4 | 4 |
| Write only | 2 | 2 |
| Execute only | 1 | 1 |
| Read + Write | 4 + 2 | 6 |
| Read + Execute | 4 + 1 | 5 |
| Read + Write + Execute | 4 + 2 + 1 | 7 |

### Example

```bash
chmod 755 script.sh
```

Meaning:

- Owner: 7 = read, write and execute.
- Group: 5 = read and execute.
- Others: 5 = read and execute.

```bash
chmod 644 notes.txt
```

Meaning:

- Owner: 6 = read and write.
- Group: 4 = read only.
- Others: 4 = read only.

### When to use chmod

- To make a Bash script executable.
- To control access to research files.
- To prevent unwanted modification of files.

---

# PART D: VIEWING AND PROCESSING TEXT FILES

## 19. Viewing FASTA Files

### What is a FASTA File?

- FASTA is a text-based format used to represent nucleotide or protein sequences.
- It is commonly used in bioinformatics.
- Each sequence record contains a header followed by its sequence.

### Basic FASTA Structure

```text
>Sequence_1
ATGCGTACGTAG
>Sequence_2
ATGCCCTAGCTA
>Sequence_3
ATGTTACCGGTA
```

### Components

- `>` indicates the beginning of a sequence header.
- The text following `>` identifies the sequence.
- The following lines contain the nucleotide or protein sequence.

### Commands for Viewing FASTA Files

**1. Display the complete file**

```bash
cat data.fasta
```

Displays all the contents of the FASTA file.

**2. View the file page by page**

```bash
less data.fasta
```

Allows the user to navigate through a large file without displaying everything at once.

Useful keys inside `less`:

| Key | Action |
|---|---|
| Space | Move forward one page |
| `b` | Move backward one page |
| Up / Down arrows | Move line by line |
| `/word` | Search for a word or pattern |
| `q` | Quit |

**3. Display the first few lines**

```bash
head data.fasta
```

Displays the first 10 lines by default.

**4. Display a specific number of lines**

```bash
head -n 5 data.fasta
```

Displays the first five lines.

**5. Display the last few lines**

```bash
tail data.fasta
```

Displays the last 10 lines by default.

**6. Display a specific number of lines from the end**

```bash
tail -n 5 data.fasta
```

Displays the last five lines.

### When to use these commands

| Command | Use |
|---|---|
| `cat` | View the entire file |
| `less` | Inspect large files interactively |
| `head` | Inspect the beginning of a file |
| `tail` | Inspect the end of a file |

---

## 20. Pattern Matching: grep

### Definition

- `grep` is used to search for text patterns in files.
- It displays lines that match the specified pattern.
- It is useful for finding sequence headers, gene IDs and specific text.

### Basic Syntax

```bash
grep "pattern" filename
```

### Example 1: Search for a Word

```bash
grep "gene" data.txt
```

Displays lines containing the word `gene`.

### Example 2: Extract FASTA Headers

```bash
grep "^>" data/raw/test-small.fasta
```

Displays all lines beginning with `>`.

### Explanation

- `grep` searches for a specified pattern.
- `^` represents the beginning of a line.
- `>` is the FASTA header symbol.
- Therefore, `^>` matches lines that begin with `>`.

### Example 3: Count FASTA Sequences

```bash
grep -c "^>" data/raw/test-small.fasta
```

Counts the number of lines that begin with `>`.

Since each FASTA record has one header line, this gives the number of sequence records in a standard FASTA file.

### Example 4: Case-Insensitive Search

```bash
grep -i "gene" data.txt
```

Searches for `gene` regardless of uppercase or lowercase letters.

### Example 5: Display Line Numbers

```bash
grep -n "^>" data/raw/test-small.fasta
```

Displays matching FASTA headers along with their line numbers.

### Important grep Symbols

| Symbol / Option | Meaning |
|---|---|
| `^` | Beginning of a line |
| `$` | End of a line |
| `-c` | Count matching lines |
| `-i` | Ignore case |
| `-n` | Display line numbers |
| `-v` | Display lines that do not match |

---

## 21. Counting Lines and Words: wc

### Definition

- `wc` stands for Word Count.
- It is used to count lines, words, bytes and characters in a file.

### Common Options

| Command | Purpose |
|---|---|
| `wc filename` | Displays line, word and byte counts |
| `wc -l filename` | Counts lines |
| `wc -w filename` | Counts words |
| `wc -c filename` | Counts bytes |
| `wc -m filename` | Counts characters |

### Example 1: Count FASTA File Lines

```bash
wc -l data/raw/test-small.fasta
```

Displays the total number of lines in the file.

### Example 2: Count FASTA Headers

```bash
grep "^>" data/raw/test-small.fasta | wc -l
```

Counts the number of FASTA headers.

### Important Difference

- `wc -l` counts all lines in a file.
- `grep "^>" ... | wc -l` counts only lines beginning with `>`.

These two commands provide different information.

---

## 22. Extracting Text: cut

### Definition

- `cut` extracts selected sections from each line of a file.
- It is commonly used to extract specific columns or fields from structured text.

### Syntax

```bash
cut -d "delimiter" -f field_number filename
```

Where:

- `-d` specifies the delimiter.
- `-f` specifies which field to extract.

### Example 1: Extract the First Column

Consider a tab-separated file:

```text
Gene_ID    Expression    Treatment
GENE01     10.5           Control
GENE02     15.2           Drug
GENE03     20.1           Control
```

Command:

```bash
cut -f 1 data.tsv
```

Output:

```text
Gene_ID
GENE01
GENE02
GENE03
```

### Example 2: Extract a Column Using a Delimiter

For a comma-separated file:

```text
Gene_ID,Expression,Treatment
GENE01,10.5,Control
GENE02,15.2,Drug
```

Command:

```bash
cut -d "," -f 2 data.csv
```

Output:

```text
Expression
10.5
15.2
```

### When to use cut

- To extract specific columns.
- To retrieve gene IDs from tabular files.
- To extract fields from delimited datasets.

**Important:** `cut` works best with clearly delimited text. For complex CSV files containing quoted commas, a CSV-aware tool is more appropriate.

---

## 23. Sorting Data: sort

### Definition

- `sort` arranges lines of text in a specified order.
- By default, it sorts lines alphabetically or lexicographically.

### Syntax

```bash
sort filename
```

### Example

Input:

```text
Banana
Apple
Mango
Orange
```

Command:

```bash
sort fruits.txt
```

Output:

```text
Apple
Banana
Mango
Orange
```

### Common Options

**1. Reverse sorting**

```bash
sort -r fruits.txt
```

Sorts in reverse order.

**2. Numeric sorting**

```bash
sort -n numbers.txt
```

Sorts numbers numerically rather than alphabetically.

**3. Remove duplicate lines**

```bash
sort -u fruits.txt
```

Sorts the lines and removes duplicates.

### When to use sort

- To organise gene IDs.
- To sort sample names.
- To organise numeric values.
- To prepare data for downstream text processing.

---

# PART E: PIPES AND COMMAND CHAINING

## 24. Pipes (Command Chaining)

### Definition

- A pipe is represented by the vertical line symbol `|`.
- It sends the output of one command as the input to another command.
- Pipes allow multiple commands to work together without saving intermediate results into separate files.

### Syntax

```bash
command1 | command2
```

### Example 1: Count FASTA Headers

```bash
grep "^>" data/raw/test-small.fasta | wc -l
```

### Explanation

1. `grep "^>"` extracts lines beginning with `>`.
2. The pipe `|` passes those lines to the next command.
3. `wc -l` counts the lines.
4. The final output represents the number of FASTA records.

### Example 2: Extract and Sort FASTA Headers

```bash
grep "^>" data/raw/test-small.fasta | sort
```

This extracts all FASTA headers and sorts them.

### Example 3: Extract, Sort and Count Headers

```bash
grep "^>" data/raw/test-small.fasta | sort | wc -l
```

This demonstrates how multiple commands can be chained.

### Why Use Pipes?

- Reduces the need for intermediate files.
- Combines simple commands to perform more complex tasks.
- Makes command-line processing efficient.
- Helps build bioinformatics workflows.

---

## 25. Output Redirection

### Definition

- Redirection sends command output to a file instead of displaying it directly in the terminal.
- It is useful for saving results, reports and error messages.

### 1. Standard Output Overwrite: >

The `>` operator sends output to a file.

If the file already exists, its contents are overwritten.

### Example

```bash
echo "Hello Linux" > output.txt
```

Creates `output.txt` and writes the text into it.

### Example: Save FASTA Headers

```bash
grep "^>" data/raw/test-small.fasta > headers.txt
```

Stores all FASTA headers in `headers.txt`.

### 2. Standard Output Append: >>

The `>>` operator adds output to the end of an existing file.

It does not erase the previous contents.

### Example

```bash
echo "New line added" >> output.txt
```

Adds the text to the end of `output.txt`.

### Difference Between > and >>

| Operator | Purpose |
|---|---|
| `>` | Overwrites the file |
| `>>` | Appends to the file |

### Important

Always check whether you want to replace the existing contents or add to them before using redirection.

---

## 26. Standard Output vs Standard Error

Linux programs commonly use three standard input/output streams.

| Stream | File Descriptor | Meaning |
|---|---:|---|
| Standard Input (`stdin`) | 0 | Input received by a command |
| Standard Output (`stdout`) | 1 | Normal output produced by a command |
| Standard Error (`stderr`) | 2 | Error messages produced by a command |

### Standard Output

- Contains normal program output.
- Can be displayed in the terminal or redirected to a file.

Example:

```bash
echo "Analysis completed" > output.txt
```

### Standard Error

- Contains error messages.
- Can be redirected separately from normal output.

Example:

```bash
some_command 2> errors.log
```

Saves error messages into `errors.log`.

### Redirect Both Output and Errors

```bash
some_command > output.log 2> errors.log
```

- Normal output is stored in `output.log`.
- Error messages are stored in `errors.log`.

### Append Error Messages

```bash
some_command 2>> errors.log
```

Adds error messages to the end of `errors.log`.

### Why Is This Important in Bioinformatics?

- Normal results can be saved separately.
- Errors can be recorded for troubleshooting.
- Long-running analyses can be monitored.
- Error logs help identify pipeline failures.

---

## 27. Common Linux Mistakes

Common mistakes to avoid when using the Linux command line:

1. **Using a GUI instead of the terminal:** This can make command-line workflows difficult to automate.
2. **Hardcoding full paths unnecessarily:** Relative paths can make project scripts more portable.
3. **Running `rm` carelessly:** Files may be permanently deleted.
4. **Not verifying output:** Always inspect the output after running a command.
5. **Ignoring error messages:** Error messages provide useful information about what went wrong.
6. **Working in the wrong directory:** Check the current location using `pwd`.
7. **Using incorrect file paths:** Check the spelling, directory and filename.
8. **Ignoring file permissions:** Some scripts require execute permission before they can run.

---

## 28. Real-World Applications in Research Laboratories

Linux command-line tools are useful in bioinformatics research.

Common applications include:

- Inspecting downloaded genome data.
- Validating sequence files.
- Extracting gene IDs.
- Counting sequences in FASTA files.
- Preparing data for BLAST searches.
- Preparing files for sequence alignment.
- Organising raw and processed datasets.
- Combining commands to automate repetitive tasks.

### Example: Inspecting a FASTA File

```bash
# Check current directory
pwd

# List available files
ls -lh

# Display FASTA headers
grep "^>" data/raw/test-small.fasta

# Count the number of sequences
grep -c "^>" data/raw/test-small.fasta

# Count the number of lines
wc -l data/raw/test-small.fasta

# Save headers into a separate file
grep "^>" data/raw/test-small.fasta > headers.txt
```

This example combines basic navigation, file inspection, pattern matching, counting and output redirection.

---

# Module 2: Bash Scripting

## 29. Learning Objectives

- Write Bash scripts.
- Use arguments and variables.
- Implement loops and conditions.
- Validate input files.
- Handle errors properly.
- Build an automated FASTA analyser.

---

## 30. Introduction to Bash Scripting

### What is Bash?

- Bash stands for Bourne Again SHell.
- It is a command-line shell commonly used in Linux.
- Bash also provides a scripting language that allows multiple commands to be written and executed together.

### What is a Shell Script?

- A shell script is a text file containing commands that can be executed by the shell.
- It allows repetitive tasks to be automated.
- Instead of manually entering commands one by one, the commands can be stored in a script.

### Why Use Bash Scripts?

Manual command execution has some limitations:

1. **Error-prone:** Repeated manual commands can introduce typing mistakes.
2. **Repetitive:** The same commands may need to be entered repeatedly.
3. **Not scalable:** Manual processing becomes slow when working with large datasets.
4. **Difficult to reproduce:** Manually repeating a workflow can lead to inconsistent results.

### Benefits of Automation

- Reproducibility.
- Portability.
- Efficiency.
- Reduced manual errors.
- Easier processing of multiple datasets.

---

## 31. Creating a Bash Script

### Step 1: Create a Script File

```bash
touch script.sh
```

The `.sh` extension is commonly used for shell script files.

### Step 2: Open the File in a Text Editor

```bash
nano script.sh
```

You can also use another text editor.

### Step 3: Write a Simple Bash Script

```bash
#!/bin/bash

echo "Hello Linux"
echo "My first Bash script"
```

### Understanding the Script

**Shebang:**

```bash
#!/bin/bash
```

- The shebang is the first line of the script.
- It tells the operating system which interpreter should execute the script.
- In this case, the script should be executed using Bash.

**echo:**

```bash
echo "Hello Linux"
```

Displays the message in the terminal.

### Step 4: Give Execute Permission

```bash
chmod +x script.sh
```

### Step 5: Execute the Script

```bash
./script.sh
```

Output:

```text
Hello Linux
My first Bash script
```

The `./` indicates that the script is located in the current working directory.

---

## 32. Variables in Bash

### Definition

- A variable is a named storage location used to hold a value.
- Variables allow information to be stored and reused within a script.

### Syntax

```bash
variable_name=value
```

### Example

```bash
name="Deepti"

echo "$name"
```

Output:

```text
Deepti
```

### Important Rules

- Do not include spaces around the `=` sign when assigning values.
- Variable names are case-sensitive.
- Use `$` before a variable name when retrieving its value.

Correct:

```bash
name="Deepti"
```

Incorrect:

```bash
name = "Deepti"
```

### Example: Multiple Variables

```bash
name="Deepti"
course="Biotechnology"
subject="Bioinformatics"

echo "$name"
echo "$course"
echo "$subject"
```

Output:

```text
Deepti
Biotechnology
Bioinformatics
```

---

## 33. Command-Line Arguments

### Definition

- Command-line arguments are values supplied to a script when it is executed.
- They allow a script to receive input without requiring the user to edit the script itself.

### Example

Consider a script named `greet.sh`:

```bash
#!/bin/bash

echo "Hello $1"
```

Run the script:

```bash
./greet.sh Deepti
```

Output:

```text
Hello Deepti
```

### Understanding $1 and $2

Bash uses special variables to access command-line arguments.

| Variable | Meaning |
|---|---|
| `$0` | Name or invocation path of the script |
| `$1` | First argument |
| `$2` | Second argument |
| `$3` | Third argument |
| `$#` | Number of positional arguments |
| `$@` | All positional arguments as separate words |
| `$*` | All positional arguments treated together |

### Example: Two Arguments

Script:

```bash
#!/bin/bash

echo "First argument: $1"
echo "Second argument: $2"
```

Execution:

```bash
./script.sh sample1.fasta sample2.fasta
```

Output:

```text
First argument: sample1.fasta
Second argument: sample2.fasta
```

### When to use command-line arguments

- To supply input filenames.
- To provide sample IDs.
- To specify output locations.
- To reuse one script with different datasets.

---

## 34. Exit Codes

### Definition

- An exit code is a number returned by a command or script when it finishes.
- It indicates whether the command completed successfully or encountered an error.

### Common Exit Codes

| Exit Code | Meaning |
|---|---|
| `0` | Success |
| Non-zero | Failure or another status |

A common example of a failure code is `1`, although different programs may use different non-zero values.

### Checking an Exit Code

```bash
echo $?
```

Displays the exit code of the most recently executed command.

### Example

```bash
ls
echo $?
```

If the `ls` command succeeds, the output is commonly:

```text
0
```

If a command fails, it usually returns a non-zero exit code.

### Why Are Exit Codes Important?

- To check whether a command succeeded.
- To detect errors in scripts.
- To decide whether the next step of a pipeline should execute.
- To automate error handling.

---

## 35. Conditional Statements: if-else

### Definition

- Conditional statements allow a Bash script to make decisions.
- A block of code is executed depending on whether a condition is true or false.

### Basic Syntax

```bash
if [ condition ]; then
    commands
else
    commands
fi
```

### Important Syntax Rules

- `if` begins the conditional statement.
- `[ ]` contains the condition.
- `then` begins the commands executed when the condition is true.
- `else` contains commands executed when the condition is false.
- `fi` ends the conditional statement.
- Spaces inside `[ ]` are important.

### Example: Checking a Number

```bash
#!/bin/bash

if [ "$1" -gt 100 ]; then
    echo "Large threshold"
else
    echo "Small threshold"
fi
```

Execution:

```bash
./script.sh 150
```

Output:

```text
Large threshold
```

Execution:

```bash
./script.sh 50
```

Output:

```text
Small threshold
```

### Explanation

- `$1` receives the first command-line argument.
- `-gt` means greater than.
- If the value is greater than 100, the first block executes.
- Otherwise, the `else` block executes.

### Common Numeric Comparison Operators

| Operator | Meaning |
|---|---|
| `-eq` | Equal to |
| `-ne` | Not equal to |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal to |
| `-le` | Less than or equal to |

### String Comparison

```bash
if [ "$name" = "Deepti" ]; then
    echo "Name matched"
else
    echo "Name not matched"
fi
```

Common string operators:

| Operator | Meaning |
|---|---|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | String is empty |
| `-n` | String is not empty |

### Important Difference

Bash conditions use operators such as `-gt`, `-lt` and `-eq` inside `[ ]`.

They do not use the same comparison syntax as Python or R.

---

## 36. Loops in Bash

### Definition

- Loops allow a set of commands to be executed repeatedly.
- They are useful when processing multiple files or repeating the same operation.

The two loops covered in this session are:

1. `for` loop.
2. `while` loop.

### 1. For Loop

**Definition:**

- A `for` loop repeats commands for each item in a specified list.
- It is useful when the files or items to process are already known.

### Syntax

```bash
for variable in list
do
    commands
done
```

### Example: Processing FASTA Files

```bash
for file in data/raw/*.fasta
do
    echo "$file"
done
```

### Explanation

1. `for` starts the loop.
2. `file` is the loop variable.
3. `data/raw/*.fasta` matches files ending in `.fasta` inside the specified directory.
4. `do` begins the loop body.
5. `echo "$file"` displays the current filename.
6. `done` marks the end of the loop.

The loop repeats for every matching file.

### 2. While Loop

**Definition:**

- A `while` loop repeatedly executes commands as long as a condition remains true.
- It is useful when the number of repetitions is not fixed in advance.

### Syntax

```bash
while condition
do
    commands
done
```

### Example: Reading a File Line by Line

```bash
while read -r line
do
    echo "$line"
done < data/raw/test-small.fasta
```

### Explanation

1. `while` begins the loop.
2. `read -r line` reads one line from the input.
3. The line is stored in the variable `line`.
4. `echo "$line"` displays the line.
5. The loop continues until there are no more lines to read.
6. `done` marks the end of the loop.
7. `< data/raw/test-small.fasta` supplies the file as input to the loop.

### Difference Between for and while Loops

| For Loop | While Loop |
|---|---|
| Iterates over a list of items | Repeats while a condition is true |
| Useful for processing multiple known files | Useful for reading lines or condition-based repetition |
| Example: Processing all FASTA files | Example: Reading a FASTA file line by line |

---

## 37. awk: Text Processing

### Definition

- `awk` is a command-line text-processing tool.
- It is useful for processing structured text.
- It can extract columns, search for patterns and perform calculations.

### Basic Syntax

```bash
awk 'pattern { action }' filename
```

### Example 1: Print a File

```bash
awk '{print}' data.txt
```

Displays every line in the file.

### Example 2: Extract a Column

Consider a tab-separated file:

```text
Gene_ID    Expression    Treatment
GENE01     10.5           Control
GENE02     15.2           Drug
GENE03     20.1           Control
```

Command:

```bash
awk '{print $1}' data.tsv
```

Output:

```text
Gene_ID
GENE01
GENE02
GENE03
```

### Understanding Column Variables

| Variable | Meaning |
|---|---|
| `$0` | Entire line |
| `$1` | First field |
| `$2` | Second field |
| `$3` | Third field |
| `NF` | Number of fields in the current line |
| `NR` | Current record or line number |

### Example 3: Extract FASTA Headers

```bash
awk '/^>/ {print}' data/raw/test-small.fasta
```

Displays all FASTA header lines.

### Example 4: Count FASTA Sequences

```bash
awk '/^>/ {count++} END {print count}' data/raw/test-small.fasta
```

Counts the number of FASTA headers.

### Explanation

- `/^>/` searches for lines beginning with `>`.
- `count++` increases the counter for every matching line.
- `END` runs the final action after the file has been processed.
- `print count` displays the total number of matching lines.

### Example 5: Calculate Average FASTA Sequence Length

FASTA files can contain sequences spanning multiple lines. The following example combines sequence lines belonging to each record before calculating the average.

```bash
awk '
/^>/ {
    if (length_seq > 0) {
        total += length_seq
        count++
    }
    length_seq = 0
    next
}
{
    length_seq += length($0)
}
END {
    if (length_seq > 0) {
        total += length_seq
        count++
    }
    if (count > 0) {
        print "Average sequence length:", total / count
    }
    else {
        print "No sequences found"
    }
}' data/raw/test-small.fasta
```

### Explanation

- `^>` identifies a new FASTA header.
- `length_seq` stores the length of the current sequence.
- `length($0)` calculates the number of characters in a sequence line.
- `total` stores the combined sequence lengths.
- `count` stores the number of sequences.
- The `END` block calculates and displays the average.

**Important:** This example assumes a standard FASTA file with one header per sequence record and sequence lines containing only sequence characters.

---

## 38. sed: Stream Editing

### Definition

- `sed` stands for Stream Editor.
- It is used to perform text transformations on input streams.
- It can search for text and replace matching patterns.
- It is useful for modifying text without manually opening a file in an editor.

### Basic Syntax

```bash
sed 'command' filename
```

### Example 1: Replace Text

```bash
sed 's/old/new/' file.txt
```

Replaces the first occurrence of `old` with `new` on each line.

### Example 2: Replace All Occurrences in Each Line

```bash
sed 's/old/new/g' file.txt
```

The `g` option replaces all matching occurrences on each line.

### Example 3: Save Changes Directly to a File

```bash
sed -i 's/old/new/g' file.txt
```

The `-i` option modifies the file directly.

**Important:** When using `-i`, the original file is modified. Keep a backup if the original content must be preserved.

### Example 4: Display Selected Lines

```bash
sed -n '1,5p' file.txt
```

Displays lines 1 through 5.

### When to use sed

- To replace text.
- To remove unwanted text.
- To modify text files.
- To perform repetitive text-cleaning operations.

---

## 39. Building a Simple FASTA Analyser

### Objective

Create a simple Bash script that:

1. Accepts a FASTA file as input.
2. Extracts sequence headers.
3. Counts the number of sequences.
4. Calculates average sequence length.
5. Saves a summary report.
6. Stores error messages separately.

### Example Project Structure

```text
FASTA_Analyser/
├── data/
│   └── test-small.fasta
├── results/
├── logs/
└── fasta_analyser.sh
```

### Example Bash Script

```bash
#!/bin/bash

# Check whether an input file was supplied
if [ "$#" -ne 1 ]; then
    echo "Usage: ./fasta_analyser.sh input.fasta"
    exit 1
fi

input_file="$1"

# Check whether the input file exists
if [ ! -f "$input_file" ]; then
    echo "Error: Input file not found" >&2
    exit 1
fi

# Create output directories
mkdir -p results logs

# Extract FASTA headers
grep "^>" "$input_file" > results/headers.txt

# Count sequences
sequence_count=$(grep -c "^>" "$input_file")

# Calculate average sequence length
average_length=$(awk '
/^>/ {
    if (length_seq > 0) {
        total += length_seq
        count++
    }
    length_seq = 0
    next
}
{
    length_seq += length($0)
}
END {
    if (length_seq > 0) {
        total += length_seq
        count++
    }
    if (count > 0)
        print total / count
    else
        print 0
}' "$input_file")

# Generate summary report
{
    echo "FASTA Analysis Report"
    echo "---------------------"
    echo "Input file: $input_file"
    echo "Number of sequences: $sequence_count"
    echo "Average sequence length: $average_length"
} > results/summary.txt

echo "Analysis completed successfully"
```

### Understanding the Script

| Component | Purpose |
|---|---|
| `#!/bin/bash` | Specifies Bash as the interpreter |
| `$#` | Checks the number of supplied arguments |
| `$1` | Stores the input filename |
| `-f` | Checks whether a regular file exists |
| `mkdir -p` | Creates output directories |
| `grep` | Extracts FASTA headers |
| `grep -c` | Counts FASTA records |
| `awk` | Calculates average sequence length |
| `>` | Saves the report into a file |
| `>&2` | Sends an error message to standard error |
| `exit 1` | Exits with a failure status |

### Important

This is a basic educational FASTA analyser. It assumes a standard FASTA input and does not perform complete biological sequence validation.

---

# Module 3: Pipelines and Best Practices

## 40. Learning Objectives

This module's objectives in the class notes include:

- Manage processes properly.
- Run long jobs safely.
- Handle system signals.
- Design modular scripts.
- Implement structured logging.
- Build a reproducible mini bioinformatics project pipeline.

**Note:** The supplied class notes contain these objectives but do not include the detailed lecture content for this module.

### Topics to Understand

The following are the topics listed in the class objectives. They will need separate learning material if they were not covered in class.

| Topic | Purpose |
|---|---|
| Process management | Manage running programs and system processes |
| Long-running jobs | Execute lengthy analyses safely |
| System signals | Control or communicate with running processes |
| Modular scripts | Divide scripts into reusable sections |
| Structured logging | Record progress, warnings and errors |
| Reproducible pipelines | Make analyses repeatable and organised |

---

# PART D: QUICK COMMAND REFERENCE

## 41. Basic Linux Commands

| Command | Purpose |
|---|---|
| `pwd` | Display current working directory |
| `ls` | List files and directories |
| `ls -l` | Display detailed file information |
| `ls -lh` | Display file sizes in human-readable format |
| `ls -a` | Display hidden files |
| `cd` | Change directory |
| `cd ..` | Move to parent directory |
| `cd .` | Stay in current directory |
| `cd ~` | Move to home directory |
| `cd -` | Return to previous directory |
| `mkdir` | Create a directory |
| `touch` | Create an empty file |
| `echo` | Display text or variable values |
| `cat` | Display file contents |
| `less` | View files interactively |
| `head` | Display the beginning of a file |
| `tail` | Display the end of a file |
| `cp` | Copy files |
| `mv` | Move or rename files |
| `rm` | Delete files |
| `tree` | Display directory structure |
| `du -sh` | Display total directory size |
| `chmod` | Change file permissions |

## 42. Text Processing Commands

| Command | Purpose |
|---|---|
| `grep` | Search for patterns |
| `grep -c` | Count matching lines |
| `grep -i` | Search without case sensitivity |
| `wc -l` | Count lines |
| `wc -w` | Count words |
| `cut` | Extract fields |
| `sort` | Sort lines |
| `awk` | Process structured text and perform calculations |
| `sed` | Edit or transform text streams |

## 43. Bash Scripting Keywords and Variables

| Keyword / Variable | Purpose |
|---|---|
| `#!/bin/bash` | Specifies Bash interpreter |
| `echo` | Displays output |
| `if` | Starts a conditional statement |
| `then` | Begins the true condition block |
| `else` | Defines the alternative block |
| `fi` | Ends the conditional statement |
| `for` | Starts a for loop |
| `while` | Starts a while loop |
| `do` | Begins the loop body |
| `done` | Ends a loop |
| `$1` | First command-line argument |
| `$2` | Second command-line argument |
| `$#` | Number of positional arguments |
| `$@` | All positional arguments |
| `$?` | Exit status of the previous command |
| `$0` | Script name or invocation path |
| `exit` | Terminates a script with an exit status |

## 44. Redirection and Pipes

| Symbol | Purpose |
|---|---|
| `>` | Redirect output and overwrite a file |
| `>>` | Redirect output and append to a file |
| `<` | Supply input from a file |
| `\|` | Send output of one command to another |
| `2>` | Redirect standard error |
| `2>>` | Append standard error to a file |
| `>&2` | Send output to standard error |

---

# PART E: IMPORTANT CONCEPTS TO REMEMBER

## 45. Linux Foundations

1. What is Linux?
2. Why is Linux important in bioinformatics?
3. What is the difference between a terminal and a shell?
4. What is Bash?
5. What is the Linux root directory?
6. What are the purposes of `/home`, `/bin`, `/usr`, `/etc`, `/tmp` and `/var`?
7. What is a file path?
8. What is the difference between an absolute path and a relative path?
9. What is the purpose of `pwd`?
10. What is the purpose of `ls`?
11. What is the difference between `cd .` and `cd ..`?
12. How do you create a directory?
13. How do you create an empty file?
14. What is the difference between `cp` and `mv`?
15. How do you delete a file or directory?
16. What are file permissions?
17. What are read, write and execute permissions?
18. What is the purpose of `chmod`?

## 46. File Processing

1. What is a FASTA file?
2. What does `>` represent in a FASTA file?
3. How do you view the contents of a FASTA file?
4. What is the difference between `cat` and `less`?
5. What is the purpose of `head` and `tail`?
6. What is `grep`?
7. How do you extract FASTA headers?
8. How do you count FASTA sequences?
9. What is the purpose of `wc`?
10. What is the purpose of `cut`?
11. What is the purpose of `sort`?
12. What is a pipe?
13. How does command chaining work?
14. What is output redirection?
15. What is the difference between `>` and `>>`?
16. What is the difference between standard output and standard error?

## 47. Bash Scripting

1. What is Bash?
2. What is a shell script?
3. What is the purpose of the shebang?
4. How do you create and execute a Bash script?
5. How do you define a variable?
6. What are command-line arguments?
7. What is the difference between `$1` and `$2`?
8. What is the purpose of `$#`?
9. What is an exit code?
10. What is the purpose of `$?`?
11. How do you write an if-else statement?
12. What are numeric comparison operators?
13. What is the difference between a for loop and a while loop?
14. What is the purpose of `awk`?
15. What is the purpose of `sed`?
16. How can Bash automate FASTA processing?

---

# PART F: PRACTICAL REVISION

## 48. Basic Linux Practice

Try the following commands in order.

### Task 1: Check Your Location

```bash
pwd
```

### Task 2: List Files

```bash
ls -lah
```

### Task 3: Create a Project Directory

```bash
mkdir Bioinformatics_Project
```

### Task 4: Enter the Directory

```bash
cd Bioinformatics_Project
```

### Task 5: Create Subdirectories

```bash
mkdir Raw_Data Processed_Data Results Scripts
```

### Task 6: Create Files

```bash
touch Scripts/analysis.sh
touch Results/summary.txt
```

### Task 7: Display a Message

```bash
echo "My first Linux project"
```

### Task 8: Write the Message into a File

```bash
echo "My first Linux project" > Results/summary.txt
```

### Task 9: View the File

```bash
cat Results/summary.txt
```

### Task 10: Check the Directory Structure

```bash
tree
```

### Task 11: Check File Permissions

```bash
ls -l Scripts/
```

### Task 12: Make the Script Executable

```bash
chmod +x Scripts/analysis.sh
```

### Task 13: Check the Updated Permissions

```bash
ls -l Scripts/
```

---

## 49. Practical FASTA File Processing

Assume a FASTA file is stored at:

```text
data/raw/test-small.fasta
```

### Task 1: View the FASTA File

```bash
cat data/raw/test-small.fasta
```

### Task 2: View Only the First Few Lines

```bash
head -n 10 data/raw/test-small.fasta
```

### Task 3: Extract FASTA Headers

```bash
grep "^>" data/raw/test-small.fasta
```

### Task 4: Count the Number of Sequences

```bash
grep -c "^>" data/raw/test-small.fasta
```

### Task 5: Count the Number of Lines

```bash
wc -l data/raw/test-small.fasta
```

### Task 6: Save FASTA Headers

```bash
grep "^>" data/raw/test-small.fasta > headers.txt
```

### Task 7: Sort the Headers

```bash
sort headers.txt
```

### Task 8: Count Headers Using a Pipe

```bash
grep "^>" data/raw/test-small.fasta | wc -l
```

---

## 50. Session Completion Checklist

### Module 1: Linux Foundations

- [ ] Understand Linux and its importance in bioinformatics.
- [ ] Understand the terminal and shell.
- [ ] Understand the Linux directory structure.
- [ ] Differentiate absolute and relative paths.
- [ ] Navigate using `pwd`, `ls` and `cd`.
- [ ] Create directories using `mkdir`.
- [ ] Create files using `touch`.
- [ ] Display messages using `echo`.
- [ ] View file contents using `cat`, `less`, `head` and `tail`.
- [ ] Copy, move and delete files.
- [ ] Understand file permissions.
- [ ] Use `chmod`.
- [ ] Inspect FASTA files.
- [ ] Extract FASTA headers using `grep`.
- [ ] Count sequences using `grep` and `wc`.
- [ ] Understand `cut` and `sort`.
- [ ] Use pipes and redirection.
- [ ] Understand stdout and stderr.

### Module 2: Bash Scripting

- [ ] Understand Bash scripting.
- [ ] Create a `.sh` file.
- [ ] Understand the shebang.
- [ ] Execute a Bash script.
- [ ] Define variables.
- [ ] Use command-line arguments.
- [ ] Understand exit codes.
- [ ] Use if-else conditions.
- [ ] Use for loops.
- [ ] Use while loops.
- [ ] Process text using `awk`.
- [ ] Perform text substitution using `sed`.
- [ ] Create a basic FASTA analyser.

### Module 3: Pipelines and Best Practices

- [ ] Understand process management.
- [ ] Understand safe execution of long-running jobs.
- [ ] Understand system signals.
- [ ] Design modular scripts.
- [ ] Implement structured logging.
- [ ] Build a reproducible mini bioinformatics pipeline.

---

**End of Linux Foundations for Bioinformatics**