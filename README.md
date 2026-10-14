# SRT111-Lab5

<div align="center">

**SRT111 Lab 5 - Fall 2026**<br>
Prepared by: Tiayyba Riaz<br>
Total Marks: 10<br>
Percentage Towards Final Grade: 2%

</div>

So far, your programs have taken their input from the keyboard with `input()` and shown their results on the screen with `print()`. When the program ends, all of that data is gone. Real programs usually keep their data in **files**: logs, configuration settings, saved results, records. In this lab, you will learn how to open a text file, read its contents in different ways, process the data line by line, combine data from more than one file, store it in a dictionary, and write the results back to a file. You will continue to use functions and a `main()` function to organize your programs, as practised in Lab 4.

The lab is divided into two components:

- **Part A: In-Class Lab** (must be completed during the scheduled lab period and demonstrated to the professor for grading).
- **Part B: Take-Home Lab** (can be completed independently after the scheduled class).

## Academic Integrity and Use of AI

This lab is intended to assess your individual understanding of Python programming. You may use AI tools (e.g., ChatGPT, Copilot, Gemini) to help explain concepts, syntax, or error messages. However, all submitted code must be your own work, and you must be able to explain your solution if asked by the professor.

Submitting copied, shared, or AI-generated solutions as your own work may result in a grade of zero and may be handled according to the College Academic Integrity Policy.

## Lab Objectives

By the end of this lab, you should be able to:

- Explain why programs store data in files.
- Open and close files using `open()`, `close()`, and the `with` statement.
- Read a file in three ways, using `read()`, `readline()`, and `readlines()`, and explain the difference between them.
- Write to a file using write mode (`'w'`) and append mode (`'a'`), and explain the difference.
- Read a file line by line with a `while` loop and clean each line using `strip()` and `split()`.
- Read two files at the same time, matching their lines, and write the combined result to a new file.
- Load data from files into a dictionary, analyse it, and save the results to a report file.
- Use functions and a `main()` function to organize programs that work with files.

## Required Comment Header

For every script created in this lab include the following comment block at the top of the file/cell.

```python
# Author: Your Name
# Date: YYYY-MM-DD
# Purpose: Brief description of what the program does.
```

## Data Files

Several tasks read from text files. The text of every file is given in the task that uses it. Create each file with exactly that text, **in the same folder as your script or notebook**. Python looks for a file in the folder you run the script from. If the file is somewhere else, you will get `FileNotFoundError`.

| File | Used in |
|---|---|
| `data2.txt` | Task 1 |
| `pythonStatements.txt`, `machineCode.txt` | Task 4 |
| `students.txt`, `grades.txt` | Tasks 5 and 6 |

`fruits.txt`, `rhyme.txt`, `output.txt` and `report.txt` are created by your own programs.

---

## Part A - In-Class Lab [30% of Lab Marks]

Complete all assigned in-class tasks during your scheduled lab.

**Part A Marking (3 marks):**

| Task | Marks |
|---|---|
| Task 1 - Reading a File Three Ways | 1.0 |
| Task 2 - Writing and Appending to a File | 1.0 |
| Task 3 - Processing a File Line by Line | 1.0 |
| **Total** | **3** |

> Marks are awarded only when the required functions and methods are used as instructed. Correct output alone is not enough.

- This part can be completed in Jupyter Lab or VS Code. You have a choice. I recommend using Jupyter Lab.
  - If you are using Jupyter Lab, then please create a single notebook file called `Lab5.ipynb` and complete each task in a unique cell. Create the data files in the same folder as the notebook.
  - If you are using VS Code, then just follow the instructions for each task and create `.py` files.
- Demonstrate your completed work to the professor before leaving the lab.
- The professor may ask you to explain portions of your code.
- No PDF submission is required for Part A unless otherwise instructed.

<details markdown="1">

<summary><b>Quick Reference: Opening, Reading and Closing Files</b></summary>

<br>

**Opening and closing a file**

```python
f = open("data.txt", "r")   # open() returns a file object
content = f.read()
f.close()                   # always close the file when you are finished
```

The `with` statement closes the file for you automatically, even if an error happens:

```python
with open("data.txt", "r") as f:
    content = f.read()
# the file is already closed here
```

**Three ways to read.** Suppose `data.txt` contains three lines: `apple`, `banana`, `cherry`.

| Method | Returns | Result for `data.txt` |
|---|---|---|
| `f.read()` | The **whole file** as **one string** | `'apple\nbanana\ncherry\n'` |
| `f.readline()` | The **next line** only, including its `\n` | 1st call: `'apple\n'`, 2nd call: `'banana\n'`, ... at the end: `''` |
| `f.readlines()` | **All lines** as a **list** of strings | `['apple\n', 'banana\n', 'cherry\n']` |

- Every line read from a file ends with the newline character `\n` (except possibly the last one).
- `strip()` removes spaces and `\n` from both ends of a string: `'apple\n'.strip()` gives `'apple'`.
- The file object remembers its position. Each `readline()` continues from where the previous read stopped.
- Text read from a file is **always a string**, even if it looks like a number.

</details>

### Task 1 - Reading a File Three Ways

**Objective:** Practice reading the same file with `read()`, `readline()`, and `readlines()`, and see what each one returns.

**Instructions:**

- Create a file named `data2.txt` in the same folder as your script, and paste the following text into it:

  ```text
  Line 1: Hello World,
  Line 2: Welcome to File Handling!
  Line 3: This is week 7.
  Line 4: We are progressing well!
  Line 5: Winter is arriving soon!
  ```

- Create a file named `task1.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header:

  ```python
  def read_whole_file(filename):
      # 1. Open the file in read mode ('r')
      # 2. Read the ENTIRE file into one string using read()
      # 3. Close the file
      # 4. Print the string
      pass


  def read_first_two_lines(filename):
      # 1. Open the file in read mode
      # 2. Use readline() TWICE to read the first two lines
      # 3. Close the file
      # 4. Print each line with strip() so no blank lines appear between them
      pass


  def read_into_list(filename):
      # 1. Use a 'with' statement to open the file (it closes automatically)
      # 2. Read all lines into a list using readlines()
      # 3. Print the list itself
      # 4. Print how many lines the file has using len()
      # 5. Print ONLY the last line (hint: index -1), stripped
      pass


  def main():
      print("=== read() ===")
      read_whole_file("data2.txt")
      print("=== readline() ===")
      read_first_two_lines("data2.txt")
      print("=== readlines() ===")
      read_into_list("data2.txt")


  main()
  ```

  > **Note:** `pass` is a placeholder that does nothing. The starter code runs as-is but only prints the three headings. Replace each `pass` with your code as you complete each function.

- Complete the three functions by following the numbered comments inside each one. Do not change `main()`.
- Run your script to test it.

**Expected Output:**

```text
=== read() ===
Line 1: Hello World,
Line 2: Welcome to File Handling!
Line 3: This is week 8.
Line 4: We are progressing well!
Line 5: Spring is arriving soon!

=== readline() ===
Line 1: Hello World,
Line 2: Welcome to File Handling!
=== readlines() ===
['Line 1: Hello World,\n', 'Line 2: Welcome to File Handling!\n', 'Line 3: This is week 8.\n', 'Line 4: We are progressing well!\n', 'Line 5: Spring is arriving soon!\n']
Number of lines: 5
Last line: Line 5: Spring is arriving soon!
```

> **Note:** The blank line after the `read()` section is expected. The last line of the file ends with `\n`, and `print()` adds another newline of its own. Notice the `\n` at the end of every item in the `readlines()` list. That is why you `strip()` lines before printing them.

<details markdown="1">

<summary><b>Quick Reference: Writing and Appending to Files</b></summary>

<br>

**File modes**

| Mode | Meaning | If the file exists | If the file does not exist |
|---|---|---|---|
| `'r'` | Read (the default) | Reads from the beginning | **Error:** `FileNotFoundError` |
| `'w'` | Write | **Erases** all existing content first | Creates it |
| `'a'` | Append | Keeps the content and adds to the **end** | Creates it |

**Writing**

```python
f = open("out.txt", "w")
f.write("first line\n")      # write() does NOT add a newline for you
f.write("second line\n")
f.close()
```

- `write()` only accepts strings. Convert numbers first: `f.write(str(42) + "\n")`.
- Without `\n`, everything you write ends up on one line.

**Reading a whole file line by line with a `while` loop**

```python
f = open("somefile.txt", "r")
line = f.readline()          # 1. read the FIRST line before the loop
while line != "":            # 2. readline() returns '' at the end of the file
    print(line.strip())      # 3. process the line
    line = f.readline()      # 4. read the NEXT line (forget this and the loop never ends)
f.close()
```

</details>

### Task 2 - Writing and Appending to a File

**Objective:** Practice creating a file with write mode (`'w'`), adding to it with append mode (`'a'`), and reading it back line by line with a `while` loop and `readline()`.

**Instructions:**

- Create a file named `task2.py` and add the required comment header.
- Write a function named `write_fruits` that:
  - Takes a file name, `filename`, as a parameter.
  - Opens the file in write mode (`'w'`).
  - Writes the following text using **one** `write()` call, then closes the file:

    ```python
    '1. Apples are crunchy.\n2. Oranges are sweet, sour and juicy.\n3. Strawberries are sweet.\n4. Which fruit do you like?'
    ```

- Write a function named `append_line` that:
  - Takes two parameters: `filename` and `text`.
  - Opens the file in append mode (`'a'`), writes `text` to it, and closes the file.
- Write a function named `print_file_lines` that:
  - Takes a file name, `filename`, as a parameter.
  - Opens the file for reading.
  - Uses a `while` loop and `readline()` to read and print the file one line at a time. Use `strip()` so there are no blank lines between the lines.
    - Hint: `readline()` returns an empty string when the end of the file is reached.
  - Closes the file.
- Write a `main()` function that:
  - Calls `write_fruits("fruits.txt")`, then prints `File fruits.txt has been created`.
  - Calls `append_line()` to add the line `5. Bananas are my favourite!` to `fruits.txt`, then prints `A new line has been appended to fruits.txt`.
    - Hint: The last line written by `write_fruits()` does not end with `\n`. Start the appended text with `\n` so it goes on a new line.
  - Prints `Reading the file fruits.txt ...`.
  - Calls `print_file_lines("fruits.txt")`.
- Add a call to the `main()` function.
- Run your script to test it. In VS Code, run `ls` in the terminal to confirm that `fruits.txt` was created. In Jupyter Lab, it appears in the file browser on the left.

**Expected Output:**

```text
File fruits.txt has been created
A new line has been appended to fruits.txt
Reading the file fruits.txt ...
1. Apples are crunchy.
2. Oranges are sweet, sour and juicy.
3. Strawberries are sweet.
4. Which fruit do you like?
5. Bananas are my favourite!
```

> **Think about it:** Run your script a second time. Why does `fruits.txt` still have only five lines, and not two copies of line 5? Now temporarily change `'w'` to `'a'` in `write_fruits()` and run it twice more. What happens to the file? Be ready to explain why. Put `'w'` back before you demonstrate your work.

<details markdown="1">

<summary><b>Quick Reference: Cleaning and Splitting Lines</b></summary>

<br>

| Code | Result | What it does |
|---|---|---|
| `"  hi there \n".strip()` | `'hi there'` | Removes spaces and `\n` from both ends |
| `"be.".strip('.')` | `'be'` | Removes the given character from both ends |
| `"I made a pet".split()` | `['I', 'made', 'a', 'pet']` | Splits the string into a list of words at the spaces |
| `len(["I", "made", "a", "pet"])` | `4` | Counts the items in a list |

- **Order matters.** `"be.\n".strip('.')` gives `'be.\n'`, because the last character is `\n`, not `.`. Call `strip()` **first** to remove the newline, **then** `strip('.')`.
- `split()` only splits at spaces, so a word like `I'd` counts as one word.
- `print(a, "---", b, "words")` puts one space between each item automatically.

</details>

### Task 3 - Processing a File Line by Line

**Objective:** Practice reading a file line by line, cleaning each line, and counting the words on each line.

**Instructions:**

- Create a file named `task3.py` and add the required comment header.
- Write a function named `create_rhyme` that takes a file name, `filename`, as a parameter and creates the file using the following code:

  ```python
  with open(filename, "w") as dataFile:
      dataFile.write("I made myself a snowball\nAs perfect as could be.\nI thought I'd keep it as a pet\nAnd let it sleep with me.")
  ```

- Write a function named `count_words` that:
  - Takes a file name, `filename`, as a parameter.
  - Opens the file in read mode (`'r'`).
  - Uses a `while` loop and `readline()` to process the file one line at a time. For each line:
    - Removes leading and trailing whitespace using `strip()`.
    - Removes the period at the end of the line using `strip('.')`.
    - Splits the line into words using `split()`.
    - Counts the words using `len()`.
    - Prints the line and its word count in the format: `<line text> --- <number of words> words`
  - Closes the file after processing all lines.
- Write a `main()` function that calls `create_rhyme("rhyme.txt")` and then `count_words("rhyme.txt")`.
- Add a call to the `main()` function.
- Run your script to test it.

**Expected Output:**

```text
I made myself a snowball --- 5 words
As perfect as could be --- 5 words
I thought I'd keep it as a pet --- 8 words
And let it sleep with me --- 6 words
```

---

## Part B - Take-Home Lab [70% of Lab Marks]

Complete the following tasks independently after the scheduled lab using VS Code.

**Part B Marking (7 marks):**

| Task | Marks |
|---|---|
| Task 4 - Combining Two Files into One | 2.0 |
| Task 5 - Loading File Data into a Dictionary | 2.5 |
| Task 6 - Saving Results to a Report File | 2.5 |
| Submission requirements (comment headers, Git push, PDF named correctly, readable screenshots) | up to 100% deduction may apply |
| **Total** | **7** |

> Marks are awarded only when the required functions and methods are used as instructed. Correct output alone is not enough.

**Before You Begin:**

- Open your local Git repository `SRT111F2026` on your computer.
- Create a new folder named `Lab05` inside the repository.
- Open the `Lab05` folder in VS Code.
- Create all Python files for this lab (`task4.py`, `task5.py`, `task6.py`) and all data files (`pythonStatements.txt`, `machineCode.txt`, `students.txt`, `grades.txt`) inside the `Lab05` folder.

**For each task:**

- Run the script using the VS Code terminal.
- Take a screenshot that clearly shows:
  - Your code in the editor.
  - The terminal output, including your username visible in the terminal.
- Insert the screenshots into a Word document under a heading that matches the task name (e.g., Task 4, Task 5). You will export this Word document to PDF and submit it on Blackboard.

<details markdown="1">

<summary><b>Quick Reference: Reading Two Files Together</b></summary>

<br>

When two files have matching lines (line 1 goes with line 1, line 2 with line 2, and so on), open both and read one line from each on every pass of the loop:

```python
fileA = open("a.txt", "r")
fileB = open("b.txt", "r")
lineA = fileA.readline()
lineB = fileB.readline()
while lineA != "" and lineB != "":   # stop as soon as EITHER file runs out
    # ... use lineA and lineB together ...
    lineA = fileA.readline()
    lineB = fileB.readline()
fileA.close()
fileB.close()
```

**Removing a comment from a line of code**

| Code | Result |
|---|---|
| `"x = 1   # add one".split("#")` | `['x = 1   ', ' add one']` |
| `"x = 1   # add one".split("#")[0]` | `'x = 1   '` (index `0` is the part before `#`) |
| `"x = 1   # add one".split("#")[0].strip()` | `'x = 1'` |

- Remove the comment **first**, then `strip()`. If you strip first, the spaces between the code and `#` stay in your result.
- `\t` is the **tab** character. Tabs line text up at the next tab stop, so the gaps may look like different widths. That is expected.

</details>

### Task 4 - Combining Two Files into One

**Objective:** Practice reading two files at the same time, cleaning the data, and writing the combined result to a new file.

The file `pythonStatements.txt` contains four lines of Python code. Each line has extra spaces and a comment explaining the code. The file `machineCode.txt` contains four lines of 16-digit binary code. Suppose each binary line is the machine-language version of the matching Python statement: line 1 of `machineCode.txt` is the machine code for line 1 of `pythonStatements.txt`, and so on.

**Instructions:**

- In your `Lab05` folder, create the file `pythonStatements.txt` with the following text (keep the spaces and comments):

  ```text
  print("Hello World")      # displays a greeting
     x = x + 1    # increase x by one
  for i in range(1,n):   # loop from 1 to n-1
      calculateSum(a,b)  # call the function
  ```

- Create the file `machineCode.txt` with the following text:

  ```text
  0000000000010100
  1100110011001100
  1010101010101010
  1001001001001000
  ```

- Create the file `task4.py` and add the required comment header.
- Write a function named `merge_files` that:
  - Takes three parameters: `py_filename`, `code_filename`, and `out_filename`.
  - Opens the first two files for reading, and opens `out_filename` for writing.
  - Uses a `while` loop to read one line from each input file on every pass. For each pair of lines:
    - Removes the comment from the Python line (everything from `#` onward), then removes leading and trailing whitespace with `strip()`.
    - Removes leading and trailing whitespace from the machine-code line with `strip()`.
    - Writes the cleaned Python statement, a tab (`\t`), the machine code, and a newline (`\n`) to the output file.
  - Closes all three files.
- Write a `main()` function that calls `merge_files("pythonStatements.txt", "machineCode.txt", "output.txt")` and then prints `output.txt has been created`.
- Add a call to the `main()` function.
- Run your script, then run `cat output.txt` in the terminal to display the new file. Include both in your screenshot.

**Expected Output:**

```text
output.txt has been created
```

**Expected contents of `output.txt` (shown by `cat output.txt`):**

```text
print("Hello World")	0000000000010100
x = x + 1	1100110011001100
for i in range(1,n):	1010101010101010
calculateSum(a,b)	1001001001001000
```

> **Note:** If `output.txt` is all on one line, you forgot to write `\n` after each machine code.

<details markdown="1">

<summary><b>Quick Reference: Dictionaries from Files</b></summary>

<br>

**Building a dictionary**

```python
grades = {}                  # an empty dictionary
grades["Avery"] = 88         # adds the key "Avery" with the value 88
print(grades["Avery"])       # 88
print(len(grades))           # 1

for name in grades:          # a for loop over a dictionary gives you each KEY
    print(name, grades[name])
```

**Convert numbers read from a file.** Everything read from a file is a string. Strings are compared character by character, so `'95' > '100'` is `True`. Use `int()` before storing a grade, so comparisons and arithmetic work:

```python
grade = int("88\n".strip())   # 88, an integer
```

**Finding the largest value:** keep two variables, the best name so far and the best grade so far. Loop over the dictionary and replace them whenever you find a larger grade.

**Average:** add every value into a `total`, then divide by `len(grades)`. Use `round(value, 1)` to round to one decimal place.

</details>

### Task 5 - Loading File Data into a Dictionary

**Objective:** Practice reading matching lines from two files into a dictionary, and using functions to analyse the data.

**Instructions:**

- In your `Lab05` folder, create the file `students.txt` with the following names, one per line:

  ```text
  Avery
  Jordan
  Riley
  Taylor
  Sasha
  Amir
  Priya
  Kai
  Lina
  Diego
  ```

- Create the file `grades.txt` with the following grades, one per line. The grades are in the same order as the names, so the first grade belongs to Avery, the second to Jordan, and so on:

  ```text
  88
  95
  82
  91
  77
  85
  90
  93
  80
  87
  ```

- Create the file `task5.py` and add the required comment header.
- Write a function named `load_grades` that:
  - Takes two parameters: `names_filename` and `grades_filename`.
  - Opens both files for reading.
  - Creates an empty dictionary.
  - Uses a `while` loop to read one name and one grade on every pass, as in Task 4. For each pair:
    - Removes whitespace from both lines with `strip()`.
    - Converts the grade to an integer with `int()`.
    - Adds the student to the dictionary, using the name as the **key** and the grade as the **value**.
  - Closes both files and returns the dictionary.
- Write a function named `top_student` that takes the dictionary as a parameter, uses a `for` loop to find the student with the highest grade, and returns that student's **name**.
- Write a function named `average_grade` that takes the dictionary as a parameter, uses a `for` loop to add up all the grades, and returns the average.
- Write a `main()` function that:
  - Calls `load_grades("students.txt", "grades.txt")` and stores the returned dictionary in a variable named `grades`.
  - Prints `Dictionary after reading files`, then prints the dictionary.
  - Prints an empty line, then `Analysis`.
  - Calls `top_student()` and prints the name and grade of the top student. Use the returned name as a key to look up the grade.
  - Calls `average_grade()` and prints the average rounded to one decimal place.
- Add a call to the `main()` function.
- Run your script to test it.

**Expected Output:**

```text
Dictionary after reading files
{'Avery': 88, 'Jordan': 95, 'Riley': 82, 'Taylor': 91, 'Sasha': 77, 'Amir': 85, 'Priya': 90, 'Kai': 93, 'Lina': 80, 'Diego': 87}

Analysis
Highest grade: Jordan with 95
Average grade: 86.8
```

> **Note:** If your grades print with quotes, such as `'Avery': '88'`, you stored strings. Convert each grade with `int()`.

### Task 6 - Saving Results to a Report File

**Objective:** Bring everything together: read data from files, process it in a dictionary, **write** a report with write mode, **append** a summary with append mode, and **read** the report back.

**Instructions:**

- Create the file `task6.py` and add the required comment header.
- Copy your `load_grades()`, `top_student()` and `average_grade()` functions from Task 5, and your `print_file_lines()` function from Task 2.
- Write a function named `letter_grade` that takes a number grade as a parameter and returns:
  - `"A"` for 90 or higher
  - `"B"` for 80 to 89
  - `"C"` for 70 to 79
  - `"D"` for anything below 70
- Write a function named `write_report` that:
  - Takes two parameters: the dictionary `grades` and a file name, `filename`.
  - Opens the file in **write** mode (`'w'`).
  - Writes the heading line `Name`, `Grade`, `Letter`, separated by tabs and ending with `\n`.
  - Uses a `for` loop over the dictionary to write one line per student: the name, the grade, and the letter grade from `letter_grade()`, separated by tabs and ending with `\n`.
    - Hint: `write()` only accepts strings, so use `str()` on the grade.
  - Closes the file.
- Write a function named `append_summary` that:
  - Takes the same two parameters as `write_report`.
  - Opens the file in **append** mode (`'a'`).
  - Writes the line `Top student: <name>` using `top_student()`.
  - Writes the line `Class average: <average>` using `average_grade()`, rounded to one decimal place.
  - Closes the file.
- Write a `main()` function that:
  - Calls `load_grades("students.txt", "grades.txt")` and stores the dictionary in `grades`.
  - Calls `write_report(grades, "report.txt")`, then `append_summary(grades, "report.txt")`.
  - Prints `report.txt has been created`.
  - Calls `print_file_lines("report.txt")` to display the report.
- Add a call to the `main()` function.
- Run your script to test it.

**Expected Output:**

```text
report.txt has been created
Name	Grade	Letter
Avery	88	B
Jordan	95	A
Riley	82	B
Taylor	91	A
Sasha	77	C
Amir	85	B
Priya	90	A
Kai	93	A
Lina	80	B
Diego	87	B
Top student: Jordan
Class average: 86.8
```

> **Note:** Run your script twice. The report should still have one heading and two summary lines, not two copies. `write_report()` uses `'w'`, which erases the old report before `append_summary()` adds to it.

## Part B Sign-Off

- Commit and push your `Lab05` folder to your GitHub repo `SRT111F2026`.
- Submit a PDF named using your Seneca username (e.g., `yoursenecausername.pdf`) on Blackboard.
- Your PDF must include:
  - Task 4 screenshot(s), including the output of `cat output.txt`
  - Task 5 screenshot(s)
  - Task 6 screenshot(s)
- Ensure the code and output are clearly readable. Screenshots should be high-resolution (minimum 800x600) and not blurry.
- Blurry or unreadable submissions will be returned for redo. A resubmission will be marked Satisfactory if the work is acceptable, but it will receive a grade of 0.
