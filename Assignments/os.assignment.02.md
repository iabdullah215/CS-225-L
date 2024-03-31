```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Assignment Number: 02
```

# C Coding and System Calls

## Question Number 01

> Write a `C` Script that takes a directory name as an input from the user and listes all its files and subdirectories.

## Question Number 02

> Write a `C` Script that takes a name of a `txt` file as an input and then asks from the user to enter a word or string and then it prints out all the sentences in which that user input string is being used.

## Question Number 03

> Write a `C` script forms two processes a `parent` and a `child` process using the `fork()` function and then friends an output as shown.

```C
The parent process ID is <any-ID>
The child process ID is <any-ID>
```

## Question Number 04

> Write a `C` script that replicates the `cat` command in linux.

## Question Number 05

> Write a `C` code that opens a file for reading using the `open()` system call, checks if the file was opened successfully, prints a message if successful, closes the file using the `close()` system call, and returns `0` to indicate successful execution.


# Solution:

## How to Run a C code in linux:

- First create an empty file using the `touch` command with the `.c` extension.

```bash
touch <file-name>.c
```

- After creating the file, open it in any of the file editors.

```bash
sudo nano <file-name>.c
```

- Write your code in it and then save it.
- Now create an executable for you respective code.

```bash
gcc <file-name>.c -o <out-put-file-name>
```

- Now to simply execute the output file.

```bash
./<out-put-file-name>
```

## Question Number 01:

