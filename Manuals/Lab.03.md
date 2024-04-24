```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Lab Number: 03
```

# Bash Scripting

This lab contains basic bash scrips.

## File Creation:
> First, create an empty file by name `hello.sh`

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ touch lab02.sh

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ls
hello.sh  lab02.sh
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

**Output:**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./lab02.sh 1 2
Hello There!
Sum of Entered Number is:
3
```

## Task 02:

Take two numbers and then which one of them is the greater.

```bash
#!/bin/bash

echo "Hello There!"
read -p "Number 1:" num1
read -p "Number 2:" num2

  if [ "$num1" -gt "$num2" ]
  then
        echo "Number 1 is Greater"
  else
        echo "Number 2 is Greater"
  fi
```

**Output:**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./lab02.sh
Hello There!
Number 1: 2
Number 2: 3
Number 2 is Greater

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./lab02.sh
Hello There!
Number 1: 3
Number 2: 2
Number 1 is Greater
```

## Task 03:

Make a simple calculator using operators

```bash
#!/bin/bash

echo "Simple Calculator"
echo "1. Addition"
echo "2. Subtraction"
echo "3. Multiplication"
echo "4. Division"

read -p "Enter your choice (1-4): " choice

read -p "Enter first number: " num1
read -p "Enter second number: " num2

if [[ $choice -eq 1 ]]; then
    result=$((num1 + num2))
    echo "Result: $result"
elif [[ $choice -eq 2 ]]; then
    result=$((num1 - num2))
    echo "Result: $result"
elif [[ $choice -eq 3 ]]; then
    result=$((num1 * num2))
    echo "Result: $result"
elif [[ $choice -eq 4 ]]; then
    if [[ $num2 -eq 0 ]]; then
        echo "Error: Division by zero!"
    else
        result=$(echo "scale=2; $num1 / $num2" | bc)
        echo "Result: $result"
    fi
else
    echo "Invalid choice"
fi

```

**Output:**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./lab02.sh 1 2
Simple Calculator
1. Addition
2. Subtraction
3. Multiplication
4. Division
Enter your choice (1-4): 1
Enter first number: 10
Enter second number: 20
Result: 30

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./lab02.sh 1 2
Simple Calculator
1. Addition
2. Subtraction
3. Multiplication
4. Division
Enter your choice (1-4): 2
Enter first number: 50
Enter second number: 30
Result: 20

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./lab02.sh 1 2
Simple Calculator
1. Addition
2. Subtraction
3. Multiplication
4. Division
Enter your choice (1-4): 3
Enter first number: 5
Enter second number: 6
Result: 30

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./lab02.sh 1 2
Simple Calculator
1. Addition
2. Subtraction
3. Multiplication
4. Division
Enter your choice (1-4): 4
Enter first number: 15
Enter second number: 4
Result: 3.75

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./lab02.sh 1 2
Simple Calculator
1. Addition
2. Subtraction
3. Multiplication
4. Division
Enter your choice (1-4): 4
Enter first number: 10
Enter second number: 0
Error: Division by zero!

```
