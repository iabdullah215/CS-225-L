# CS225-L

This is all the learning material that I made or collected including lab manuals, quizzes, assignments, and notes from the course CS-225-L (Operating System Lab)

## Some basics before you start.

## What is Bash and Bash Scripting

Bash (Bourne Again Shell) is a command language interpreter that we use in order to interact with the linux kernel. It is a command line interpreter that we use in order to interact with the linux kernel.

Bash scripting is the process of writing a set of commands in a file and then executing them in order to automate a task.

---

## Introduction to Text Editors

In Linux, we have multiple commands that act as the `notepad` of linux. Such softwares include (but are not limited to):

- nano
- vim
- emacs  

In this course, we'll be studying nano.

### Nano

Nano is a command line text editor that we can use to write, read and delete data from within a file.

In order to open a file in nano, we type the following command:

```bash
nano <file-name>
```

Now, in order to save data into the file, we will firstly press `CTRL+S` and then, in order to exit, we need to press `CTRL+X`.

## Writing your first bash script

The first line in a bash script must be `#!/bin/bash` and is called as `SHEBANG` line.

> A she-bang is set of sequence that begins with `#!` and then the interpreter is specified. In our case, we'll be using `/bin/bash` as the interpreter.

Then, we will use `echo` command in order to print data into the stdout.

```bash
#!/bin/bash

echo "Hello World"
```

Now, in order to execute this file, we need to give it executable permissions. We can do that by using the `chmod` command.

```bash
chmod +x <file-name>
```

Now, we can execute the file by using the following command:

```bash

./<file-name>
```

---

## C Language Overview

The C programming language is a versatile and powerful programming language commonly used for system programming, application development, and low-level programming tasks. It provides a structured approach to writing programs and offers a wide range of functionalities for developing efficient and portable software.

### Introduction to C Programming

C programming involves writing code using a set of predefined keywords, data types, functions, and syntax rules. It allows developers to create programs that can interact with the underlying hardware and operating system, making it suitable for developing system software, device drivers, and embedded systems.

## Writing Your First C Program

A basic C program typically consists of several components, including:

- Include directives to import necessary header files
- Function definitions, including the main function
- Statements and expressions to perform tasks and calculations

Here's an example of a simple "Hello World" program written in C:

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

To compile and execute a C program, follow these steps:

- Save the program with a .c extension, such as hello.c.
- Open a terminal window and navigate to the directory containing the program.
- Use a C compiler (such as gcc) to compile the program:

Execute the compiled program:

```bash
gcc hello.c -o hello
```

Execute the compiled program:

```bash
./hello
```

This will output:

```bash
Hello, World!
```

> This demonstrates the basic structure of a C program and the process of compiling and executing it on a Unix-like operating system.

---

## C System Calls

System calls in C provide an interface between user-level programs and the operating system kernel, allowing programs to request services from the operating system. These services include file operations, process management, memory allocation, and communication with hardware devices.

### Using System Calls

In C programming, system calls are typically invoked using library functions provided by the C standard library, such as `open()`, `read()`, `write()`, and `close()` for file operations, and `fork()`, `exec()`, and `wait()` for process management.

#### Example: File Operations

```c
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

int main() {
    int fd = open("file.txt", O_RDONLY);
    if (fd == -1) {
        printf("Error opening file\n");
        return 1;
    }

    printf("File opened successfully\n");

    char buffer[100];
    ssize_t bytes_read = read(fd, buffer, sizeof(buffer));
    if (bytes_read == -1) {
        printf("Error reading from file\n");
        return 1;
    }

    printf("Read %zd bytes: %s\n", bytes_read, buffer);

    if (close(fd) == -1) {
        printf("Error closing file\n");
        return 1;
    }

    printf("File closed successfully\n");
    return 0;
}

```

In this example, the `open()` system call is used to open a file named `file.txt` for reading. The `read()` system call is then used to read data from the file into a buffer, and the `close()` system call is used to close the file.

## Summary:

C system calls provide a powerful mechanism for interacting with the operating system kernel, enabling low-level operations and system-level programming tasks. By using system calls, C programs can perform a wide range of operations, including file manipulation, process management, and communication with hardware devices.

---
