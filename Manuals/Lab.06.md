```jsx
Name: Muhammad Abdullah
Reg. ID: BsCYS-F22-A-221546
Course: Operating System Lab
Lab Task: 06
```

## Task Number: 01
> Write a code for First Come First Serve (FCFS) Algo.

**Code:**

```c
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

**Output:**

```console

```

## Task Number: 02
> Write a code for Shortest Job First (SJF) Algo.

**Code**

```c

```

**Output:**

```console

```

## Task Number: 03
> Write a code for Round Robin (RR) Algo.

**Code**

```c

```

**Output:**

```console

```

---
