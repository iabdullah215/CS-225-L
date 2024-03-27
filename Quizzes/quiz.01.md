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

