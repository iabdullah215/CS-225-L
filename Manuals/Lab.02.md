```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Lab Number: 02
```

# Bash Scripting

This lab contains basic bash scripts.

## File Creation:
> First, create an empty file by name `hello.sh`

```console
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

```console
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

```console
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

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh is running
Hello World
Abdullah
hello.sh is running
```

## Task 04:

Use an array in your code.

> `my_array=($@)` would essentially create an array called `my_array` containing all the **positional parameters** passed to the **script** or **function**.

```bash
#!/bin/bash

echo "Hello World"
name="Abdullah"
echo $name

my_array=("apple" "banana")

echo "Elements of the array:"
echo "${my_array[0]}" 
echo "${my_array[1]}" 
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
```

Now, let's execute the file

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh happy hacking
Hello World
Abdullah
Elements of the array:
apple
banana
Script name: ./script.sh
First argument: happy
Second argument: hacking
```

## Task 05:

Write a code that asks for an `integer` value from the user and then checks whether it is equal to 100 or not. (Use If Else statments)

```bash
#!/bin/bash

echo "Please enter an integer value:"
read integer

  if [ "$integer" -eq 100 ]; then
    echo "The entered integer is equal to 100."
  else
    echo "The entered integer is not equal to 100."
  fi
```

Now, let's execute the file

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh 
Please enter an integer value:
12
The entered integer is not equal to 100.

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh 
Please enter an integer value:
100
The entered integer is equal to 100.
```

## Task 06:

Write a code that asks for an `integer` value from the user and then checks whether it is greater than or less than 100. (Use If Else and Else If statments)

```bash
#!/bin/bash

echo "Please enter an integer value:"
read integer

    if [ "$integer" -eq 100 ]; then
        echo "The entered integer is equal to 100."
    elif [ "$integer" -gt 100 ]; then
        echo "The entered integer is greater than 100."
    else
        echo "The entered integer is less than 100."
    fi
```

Now, let's execute the file

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh 
Please enter an integer value:
12
The entered integer is less than 100.

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh 
Please enter an integer value:
100
The entered integer is equal to 100.

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh 
Please enter an integer value:
200
The entered integer is greater than 100.
```

## Task 07:

Write a bash script that asks the user to enter a file name and then checks whether that file is present in the current directory or not.

```bash
#!/bin/bash

read -p "Please enter an integer value: " file

  if [ -e "$file" ]; then
    echo "File Found!"
  else
    echo "Error"
  fi
```

> `-p` flag is used with the read command to display a prompt message to the user. In this script, it prompts the user to enter an integer value. `-e` flag is used with the `[` command (equivalent to the `test` command) to check if a file exists. If the file exists, the expression evaluates to `true`; otherwise, it evaluates to `false`. In this script, it checks if the file exists in the current directory.

Now, let's execute the file

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh 
Please enter an integer value: hello.sh
File Found!

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./hello.sh 
Please enter an integer value: hello.txt
Error
```
