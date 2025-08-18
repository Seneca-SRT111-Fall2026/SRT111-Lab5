# Lab 5
In this lab, you will create ten simple Python scripts. All scripts must be written in GitHub Codespaces.<br>
So far, you have created Python scripts that take input either through the input() function or from command-line arguments using the `sys.argv` list. However, programs often need to work with external data stored in files. Being able to read data from a file and save processed results back to a file is a crucial programming skill. In this lab, you will learn how to:
- Open a text file.
- Read its contents in different ways.
- Process the data.
- Write results back to a file.

# Lab Objectives
- Understand the importance of file handling in programming and real-world applications.
- Open and close files in Python using the open() and close() functions.
- Read file contents using different methods: read(), readline(), and readlines().
- Write data to a file using different file modes ('w', 'a').
- Explain the differences between reading the entire file, reading line by line, and reading into a list.
- Apply file operations to solve simple tasks, such as processing text data, logging results, or saving program output.
  
# Submission Instructions
For each task:
1. **Write the script** in Codespaces.  
2. **Run the script** from the **terminal**.  
3. **Take a screenshot** that clearly shows:  
   - Your **code** in the editor.  
   - The **terminal output**, including your **username** visible in the terminal.  
4. **Insert the screenshot** into a Word document under the heading that matches the task name:  
   - Example: **Lab4a**, **Lab4b**, **Lab4c**, etc.  
5. After completing all tasks, **convert the Word document to PDF**.  Name the PDF file using your **yoursenecausername.pdf**
6. **Submit the PDF file** as your final lab submission on Blackbaord.

## INVESTIGATION 1: WORKING WITH FILES
File operations are very common in programming. For example, they are used for logging output or errors, storing configuration data, and handling temporary files. You will now explore some of the most useful file functions in Python.
You can use the following functions while working with files in python :

Here are some commonly used file functions in Python:

- **`open()`** – Opens a file in a specified mode (e.g., read `'r'`, write `'w'`, append `'a'`).  
  Returns a file object.  
  ```python
  f = open("data.txt", "r")
  ```

- **`read()`** – Reads the entire file as a single string.

```Python
content = f.read()
```

- **`readlines()`** – Reads all lines into a list, where each element is one line.

```Python
f.readlines()
```


- **`cloase()`** – Closes the file and releases system resources.

```Python
f.close()
```
**Note:** It is recommended to use the with statement, which automatically closes the file after use:
```Python
with open("data.txt", "r") as f:
    content = f.read()
```

### lab5a.py - Reading data from files
Look at the example below.
```Python
with open("data.txt") as dataFile:
  data = dataFile.read()
  print(data)
Output :
Line 1
Line 2
Line 3
```

The variable `dataFile` above is a file object. We can access file contents through this file object while the file is open. Here we used the method `read()`, which returns the contents of the file as a single string. So, in this case the string returned by `read()` method would be “Line 1 \nLine 2\nLine 3”.
Text files can be thought of as lists of strings, each string representing a single line in the file. We can go through the `list` using a `for loop`.

- Create a new file called data2.txt  and paste the following text in this file:
  ```Python
  Hello World, Welcome to File Handling!	
  Line 2
  Line 3
  Line 4
  Line 5
  ```
- Complete the functions from lab5a.py according to given instructions.
- Run the script from command line using the command: python ./lab5a.py
- Take clear screenshots of the script and output. Make sure there are no empty lines in the script.


## Lab 5 Sign-Off
- Submit a PDF on Blackboard, named using your Seneca username (e.g., **yoursenecausername.pdf**).
- The PDF must include screenshots of the following scripts and their terminal output, clearly showing your GitHub username.
    - lab5a.py
    - lab5b.py
    - lab5c.py
    - lab5d.py
    - lab5e.py
    - lab5f.py
    - lab5g.py
    - lab5h.py
    - lab5i.py
    - lab5j.py
      
- Ensure the code and output are clearly readable. Screenshots should be high-resolution (minimum 800x600) and not blurry.
- Blurry or unreadable submissions will be returned for redo. Resubmissions will only be graded as **Satisfactory** with a grade of 0, provided the work is satisfactory.

