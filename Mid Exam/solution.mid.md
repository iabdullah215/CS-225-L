```jsx
Course: CS-225-L - Operating System Lab
Title : Mid Term Exam Solution
Class : BSCYS-F22-IV-A
Name : Muhammad Abdullah
Reg. ID: BCSYS-F22-221546
Date of Exam : April 1st, 2024
Duration : 3 Hours (8:00 - 11:00)
Obtained Marks: 25
```

---
# Lab Exam Mid Term Operating System
---

# Question Number: 01

## Part A

**Code**

```bash
#!/bin/bash
bubble_sort()
{
 local array=("$@")
 local n=${#array[@]}

 for ((i = 0; i < n-1; i++)); do
 for ((j = 0; j < n-i-1; j++)); do
 if (( ${array[j]} > ${array[j+1]} )); then
 # Swap elements
 temp=${array[j]}
 array[j]=${array[j+1]}
 array[j+1]=$temp
 fi
 done
 done
 echo "Sorted array: ${array[@]}"
}

array=(1 5 12 2 7)
echo "Original array: ${array[@]}"
bubble_sort "${array[@]}"
```

**Output**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Mid-Exam]
└─$ ./q1(A)
Original array: 1 5 12 2 7
Sorted array: 1 2 5 7 12
```

---

# Question Number: 01

## Part B

**Code**

```bash
#!/bin/bash
check()
{
 local file="$1"
 if [[ -f "$file" ]];then
 echo "Entered file is a simple file"
 elif [[ -d "$file" ]];then
 echo "It is a directory"
 elif [[ -e "$file" ]]; then
 echo "It is anyother file"
 else
 echo "Error"
 fi
}
read -p "Enter File name: " filename
check "$filename"
```

**Output**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Mid-Exam]
└─$ ./q1(B)
Enter File name: happy
It is a directory

┌──(MnM@kali)-[~/Desktop/OS-L/Mid-Exam]
└─$ ./q1(B)
Enter File name: simple_file
Entered File is a simple file
```

---

# Question Number: 01

## Part C

**Code**

```bash
#!/bin/bash
echo "Enter first number: "
read num1
echo "Enter second number: "
read num2
echo "Enter the operation you want to perform (+, -, *, /): "
read operation
case $operation in
 +) result=$((num1 + num2)) ;;
 -) result=$((num1 - num2)) ;;
 \*) result=$((num1 * num2)) ;;
 /) result=$((num1 / num2)) ;;
 *) echo "Invalid operation"; exit 1 ;;
esac
echo "Result: $result"
```

**Output**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Mid-Exam]
└─$ ./q1(C)
Enter first number:
1
Enter second number:
2
Enter the operation you want to perform (+, -, *, /)
+
Result: 3
```

---

# Question Number: 02

**Code**

```C
#include<stdio.h>
#include<stdlib.h>

struct rr {
    int pno, btime, sbtime, wtime, lst;
} p[10];

int main() {
    int pp = -1, ts, flag, count, ptm = 0, i, n, twt = 0, totttime = 0;
    
    printf("enter no of processes:");
    scanf("%d", &n);
    printf("enter the time slice:");
    scanf("%d", &ts);
    printf("enter the burst time:");
    
    for (i = 0; i < n; i++) {
        printf("\n process%d\t", i + 1);
        scanf("%d", &p[i].btime);
        p[i].wtime = p[i].lst = 0;
        p[i].pno = i + 1;
        p[i].sbtime = p[i].btime;
    }
    
    printf("scheduling....\n");
    
    do {
        flag = 0;
        for (i = 0; i < n; i++) {
            count = p[i].btime;
            if (count > 0) {
                flag = -1;
                count = (count >= ts) ? ts : count;
                ptm += count;
                p[i].btime -= count;
                if (pp != i) {
                    pp = i; 
                    p[i].wtime += ptm - p[i].lst - count;
                    p[i].lst = ptm;
                }
            }
        }
    } while (flag != -1);
    
    printf("\n\n process\tburst time\twait time\tturnaround time");
    for (i = 0; i < n; i++) {
        printf("\n%d\t\t%d\t\t%d\t\t%d", p[i].pno, p[i].sbtime, p[i].wtime, p[i].sbtime + p[i].wtime);
        twt += p[i].wtime; 
        totttime += p[i].sbtime + p[i].wtime;
    }
    
    printf("\n\n the total waiting time is %d", twt);
    printf("\n\n the average waiting time is %f", (float)twt / n);
    printf("\n\n the total turnaround time is %d", totttime);
    printf("\n\n the average turnaround time is %f", (float)totttime / n);
    
    return 0;
}
```

**Output**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Mid-Exam]
└─$ ./q2
enter no of processes:4
enter the time slice:3
enter the burst time:
 process1       6

 process2       4

 process3       8

 process4       5

 scheduling....


 process        burst time      wait time       turnaround time
1               6               0               6
2               4               3               7
3               8               6               14
4               5               9               14

 the total waiting time is 18

 the average waiting time is 4.500000

 the total turnaround time is 41

 the average turnaround time is 10.250000
```

---
