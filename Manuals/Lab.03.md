```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Lab Number: 03
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

Take sum of two numbers as parameters and then display it on the terminal.

```bash
#!/bin/bash

echo "Hello There!"
echo "Sum of Entered Number is:"
sum = $(( $1 + &2 ))
echo "$sum"
```
