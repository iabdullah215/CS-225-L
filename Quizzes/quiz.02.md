```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Quiz Number: 02
```

# Quiz Description:

> Implement the `Shortest Job First (SJF)` scheduling algorithm in `C/C++` programming language for a simple operating system. Assume that you have a list of processes with their respective burst times (time required to complete execution) stored in an array. Write a `C` function that takes this array of burst times as input and returns the sequence of process execution based on `SJF` scheduling. Also, provide the average waiting time for the processes.

**The burst times are as follows:** `{5, 3, 8, 2, 6}`

Your task is to:
- Write the `C` function to implement `SJF` scheduling.
- Provide the sequence of process execution.
- Calculate the _**average waiting time**_ for the given burst times.

## Solution:

**Code For The `Shortest Job First (SJF)` scheduling algorithm:**

```c++
#include <iostream>
using namespace std;

int main() 
{
    int A[100][4];
    int i, j, n, total = 0, index, temp;
    float avg_wt;

    cout << "ENTER NUMBER OF PROCESSES: ";
    cin >> n;
    cout << "-----------------------------------" << endl;

    cout << "ENTER BURST TIME: " << endl;

    for (i = 0; i < n; i++) {
        cout << "P" << i + 1 << ": ";
        cin >> A[i][1];
        A[i][0] = i + 1;
    }
    cout << "-----------------------------------" << endl;

    for (i = 0; i < n; i++) {
        index = i;
        for (j = i + 1; j < n; j++)
            if (A[j][1] < A[index][1])
                index = j;
        temp = A[i][1];
        A[i][1] = A[index][1];
        A[index][1] = temp;

        temp = A[i][0];
        A[i][0] = A[index][0];
        A[index][0] = temp;
    }

    A[0][2] = 0;
    for (i = 1; i < n; i++) {
        A[i][2] = 0;
        for (j = 0; j < i; j++)
            A[i][2] += A[j][1];
        total += A[i][2];
    }

    avg_wt = (float)total / n;
    total = 0;
    cout << "P     BT     WT" << endl;
    cout << "-----------------------------------" << endl;

    for (i = 0; i < n; i++) {
        A[i][3] = A[i][1] + A[i][2];
        total += A[i][3];
        cout << "P" << A[i][0] << "     " << A[i][1] << "     " << A[i][2] << endl;
    }

    cout << "-----------------------------------" << endl;
    cout << "AVERAGE WAITING TIME: " << avg_wt << endl;
    cout << "-----------------------------------" << endl;
}
```

**Code Explaination:**

This `C++` code simulates a basic scheduling algorithm to manage processes' execution by calculating their average waiting time. Initially, it prompts the user to input the number of processes and their corresponding burst times. Subsequently, it employs the selection sort algorithm to arrange the processes in ascending order based on their burst times. After sorting, it iteratively computes the waiting time for each process, which accumulates the sum of burst times of all preceding processes. By summing these waiting times, it derives the total waiting time, dividing it by the number of processes to obtain the average waiting time. The code concludes by displaying a tabulated view of each process's ID, burst time, and waiting time, followed by the computed average waiting time. This process scheduling approach offers insights into optimizing system performance and resource allocation.

**Code Compilation**

> Compile your `C++` code using a `C++ compiler` like `g++`. The command generally looks like this:

```bash
g++ -o <output-file-name> <source-file>.cpp
```

>  Once your code is compiled without any errors, you can run your program. To run the code you would type:

```bash
./<output-file-name>
```

> Output after compilation

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Quiz]
└─$ ./output
ENTER NUMBER OF PROCESSES: 5
-----------------------------------
ENTER BURST TIME:
P1: 5
P2: 3
P3: 8
P4: 2
P5: 6
-----------------------------------
P     BT     WT
-----------------------------------
P4     2     0
P2     3     2
P1     5     5
P5     6     10
P3     8     16
-----------------------------------
AVERAGE WAITING TIME: 6.6
-----------------------------------
```

## Gantt Chart:

| P4 | P2 | P1 | P5 | P3 |
| -- | -- | -- | -- | -- |

> What is a _**Gantt Chart**_?

A Gantt chart is a type of bar chart that illustrates a project schedule. It provides a graphical representation of the start and finish dates/times of the various elements of a project. The horizontal axis of the chart represents the timeline, typically broken down into increments such as `seconds`, `days`, `weeks`, or `months`, while the vertical axis lists the `tasks` or `activities` involved in the project.
