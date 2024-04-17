```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Assignment Number: 01
```

# Assignment Description:

**Question Number 01:**

> Write a shell script to check whether a year is leap or not.

**Question Number 02:**

> Write a shell script to find the Factorial of a given number

**Question Number 03:**

> Write a shell script to Swap two numbers.

## Solution:

**Task Number 01:**

```bash
#!/bin/bash

echo "Enter a year: "
read year

if (( ($year % 4 == 0 && $year % 100 != 0) || ($year % 400 == 0) ))
then
    echo "$year is a leap year."
else
    echo "$year is not a leap year."
fi

```

**Code Explaination:**

This script takes a year as input from the user and checks whether it's a leap year or not based on the leap year algorithm. It divides the given year by `4`, `100`, and `400` to determine if it's evenly divisible. If it's divisible by `4` but not by `100` or it's divisible by `400`, then it's a leap year.

**Output:**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Assignment]
└─$ ./task1
Enter a year: 
2024
2024 is a leap year.

```

**Task Number 02:**

```bash
#!/bin/bash

echo "Enter a number: "
read num

factorial=1
for ((i=1; i<=$num; i++))
do
    factorial=$((factorial * i))
done

echo "Factorial of $num is: $factorial"

```

**Code Explaination:**

This script calculates the factorial of a given number provided by the user. It initializes the factorial variable to `1` and then iterates from `1` to the given `number`, multiplying each iteration's value to the factorial variable.

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Assignment]
└─$ ./task2
Enter a number: 
5
Factorial of 5 is: 120

```

**Task Number 03:**

```bash
#!/bin/bash

echo "Enter first number: "
read num1
echo "Enter second number: "
read num2

echo "Numbers before swapping: $num1 $num2"

temp=$num1
num1=$num2
num2=$temp

echo "Numbers after swapping: $num1 $num2"

```

**Code Explaination:**

This script swaps the values of two numbers provided by the user. It stores the first number in a temporary variable, assigns the value of the second number to the first number, and then assigns the value stored in the temporary variable to the second number.

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Assignment]
└─$ ./task3
Enter first number: 
10
Enter second number: 
20
Numbers before swapping: 10 20
Numbers after swapping: 20 10

```
