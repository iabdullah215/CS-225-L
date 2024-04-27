```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Quiz Number: 01
```

# Quiz Description:

**Task Number 01:**
> Develop a shell script that prompts the user to enter a number. The script should then determine if the entered number is prime or not and display the result.

**Task Number 02:**
> Write a shell script that counts the number of files in the current directory and displays the count as output

**Task Number 03:**
> Design a shell script that takes a number as input and counts down from that number to 1, displaying each number with a one-second delay between counts. Utilize a while loop for the countdown

## Solution:

**Task Number 01:**

```bash
#!/bin/bash

echo "Enter a number: "
read num

is_prime=1

if [ $num -eq 1 ]; then
    is_prime=0
fi

for ((i=2; i<=$num/2; i++))
do
    if [ $((num%i)) -eq 0 ]; then
        is_prime=0
        break
    fi
done

if [ $is_prime -eq 1 ]; then
    echo "$num is a prime number."
else
    echo "$num is not a prime number."
fi
```

**Code Explaination:**

The shell script checks whether a user-entered number is prime or not. It begins by prompting the user to input a number. The script then initializes a variable to indicate whether the number is prime. It sets this variable to `1`, assuming initially that the number is prime. However, it specifically handles the case when the input number is `1` by setting the variable to `0`, as `1` is not considered a prime number. Using a for loop, the script iterates from `2` to half of the input number, checking if the number is divisible by any integer in this range. If it finds such a divisor, it sets the prime variable to `0` and breaks out of the loop. Finally, it checks the value of the prime variable: if it remains `1`, the script concludes that the input number is prime; otherwise, it determines that the number is not prime and displays the result accordingly.

**Output:**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Quiz]
└─$ ./task1
Enter a number:
7
7 is a prime number.

┌──(MnM@kali)-[~/Desktop/OS-L/Quiz]
└─$ ./task1
Enter a number:
12
12 is not a prime number.
```

**Task Number 02:**

```bash
#!/bin/bash

file_count=$(ls -l | grep "^-" | wc -l)

echo "Number of files in the current directory: $file_count"
```

**Code Explaination:**

- `ls -1` lists the files in the current directory, one per line.
- This output is piped (`|`) to `wc -l`, which counts the number of files in the output.
- The final count is stored in the variable named `file_count`

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Quiz]
└─$ ./task2
Number of files in the current directory: 3
```

**Task Number 03:**

```bash
#!/bin/bash

echo "Enter a number: "
read num

while [ $num -gt 0 ]; do
    echo $num
    sleep 1
    num=$((num - 1))
done
echo "fsociety : )"
```

**Code Explaination:**

This code takes as input as an argument. We assign that entered value to a variable name 
number. After that a while loop starts with a condition that checks whether the entered 
number is greater than zero or not. Then it displays the number and waits for 1 second after 
that it decrements the number value by 1 and again stores it in the variable number. After the 
number is becomes equal to zero it breaks the loop and prints `fsociety : )` in the end

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Quiz]
└─$ ./task3
Enter a number:
3
3
2
1
fsociety : )
```
