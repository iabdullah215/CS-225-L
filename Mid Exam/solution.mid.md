```jsx
Course: CS-225-L - Operating System Lab
Title : Mid Term Exam Solution
Class : BSCYS-F22-IV-A
Name : Muhammad Abdullah
Reg. ID: BCSYS-F22-221546
Date of Exam : April 1st, 2024
Duration : 3 Hours (8:00 - 11:00)
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

