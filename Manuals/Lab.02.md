```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Lab Number: 02
```

# Bash Scripting

This lab contains basic bash scripting codes.

## File Creation:
> First, create an empty file by name `hello.sh`

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ touch hello.sh

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ls
hello.sh
```

## Task 01:

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
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh
Hello World

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ bash hello.sh
Hello World
```

## Task 02:

Write a code with a variable `name` having your name assigned to it. It should display you name on the terminal upon execution of the code.
```bash
#!/bin/bash

echo "Hello World"
name = "Abdullah"
echo $name
```

Now, we can execute the file

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh
Hello World
Abdullah
```

## Task 03:

Use the command `echo $0 $1 $2` in your code.
- `$0`: This represents the name of the script or shell itself.
- `$1`: This represents the first command-line argument passed to the script or function.
- `$2`: Similarly, this represents the second command-line argument.

```bash
#!/bin/bash

echo "Hello World"
name = "Abdullah"
echo $name
echo $0 $1 $2
```

Now, let's execute the file

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh is running
Hello World
Abdullah
hello.sh is running
```
