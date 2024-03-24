# CS-225-L

This is all the learning material and lab manuals from the course CS-225-L (Operating System)

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
