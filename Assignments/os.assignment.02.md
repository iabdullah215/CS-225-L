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

> Write a `C` code that opens a file for reading using the `open()` system call, checks if the file was opened successfully, prints a message if successful, closes the file using the `close()` system call, and `returns 0` to indicate successful execution.


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

**Code:**
```C
#include <stdio.h>
#include <dirent.h>

int main() {
    char dirname[100];
    printf("Enter directory name: ");
    scanf("%s", dirname);

    DIR *dir = opendir(dirname);
    if (dir == NULL) {
        printf("Error opening directory\n");
        return 1;
    }

    struct dirent *entry;
    while ((entry = readdir(dir)) != NULL) {
        printf("%s\n", entry->d_name);
    }

    closedir(dir);
    return 0;
}
```

**Code Explaination:**

This  `C` script takes a directory name as input from the user, opens the directory using `opendir()`, reads each entry within the directory using `readdir()`, and prints the name of each file and subdirectory. Finally, it closes the directory using `closedir()`.


**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Assignment]
└─$ ./q2
Enter directory name: ~/Desktop/OS-L
Assignment
Quizzes
Notes.txt
```

## Question Number 02:

**Code:**
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    char filename[100];
    char word[100];

    printf("Enter file name: ");
    scanf("%s", filename);

    printf("Enter word to search: ");
    scanf("%s", word);

    FILE *file = fopen(filename, "r");
    if (file == NULL) {
        printf("Error opening file\n");
        return 1;
    }

    char line[100];
    while (fgets(line, sizeof(line), file)) {
        if (strstr(line, word) != NULL) {
            printf("%s", line);
        }
    }

    fclose(file);
    return 0;
}
```

**Code Explaination:**

This `C` script takes a filename and a word as input from the user, opens the file in read mode, reads each line of the file using `fgets()`, and checks if the user-input word is present in each line using `strstr()`. If found, it prints the line. Finally, it closes the file.

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Assignment]
└─$ ./q2
Enter file name: test.txt
Enter word to search: Abdullah
Hi there I am Abdullah.
Abdullah is writting code in C lang.
```

## Question Number 03:

**Code:**
```C
#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid = fork();
    if (pid == 0) {
        printf("The child process ID is %d\n", getpid());
    } else if (pid > 0) {
        printf("The parent process ID is %d\n", getpid());
    } else {
        printf("Fork failed\n");
        return 1;
    }
    return 0;
}
```

**Code Explaination:**
This C script uses `fork()` to create a child process. The child process prints its own process `ID` using `getpid()`, while the parent process prints its own process `ID`. If `fork()` fails, it prints an error message.

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Assignment]
└─$ ./q3
The parent process ID is 1612
The child process ID is 1613
```

## Question Number 04:

**Code:**
```C
#include <stdio.h>

int main(int argc, char *argv[]) {
    FILE *file;
    char ch;

    if (argc < 2) {
        printf("Usage: %s <filename>\n", argv[0]);
        return 1;
    }

    file = fopen(argv[1], "r");
    if (file == NULL) {
        printf("Error opening file\n");
        return 1;
    }

    while ((ch = fgetc(file)) != EOF) {
        printf("%c", ch);
    }

    fclose(file);
    return 0;
}
```

**Code Explaination:**

This `C` script replicates the `cat` command in Linux. It takes a `filename` as a `command-line argument`, opens the file in read mode, reads each character using `fgetc()`, and prints it to the standard output. Finally, it closes the file.

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Assignment]
└─$ ./q4 test.txt
This is a test text file. 
Hi there I am Abdullah.
Abdullah is writting code in C lang.
```

## Question Number 05:

**Code:**
```C
#include <stdio.h>
#include <fcntl.h>

int main() {
    int fd = open("test.txt", O_RDONLY);
    if (fd == -1) {
        printf("Error opening file\n");
        return 1;
    }

    printf("File opened successfully\n");

    if (close(fd) == -1) {
        printf("Error closing file\n");
        return 1;
    }

    printf("File closed successfully\n");
    return 0;
}
```

**Code Explaination:**

This `C` script opens a file by the name `test.txt` for reading using the `open()` system call with the `O_RDONLY` flag. It checks if the file was opened successfully, prints a message if successful, closes the file using the `close()` system call, and `returns 0` to indicate successful execution.

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Assignment]
└─$ ./q5
File opened successfully
File closed successfully
```
