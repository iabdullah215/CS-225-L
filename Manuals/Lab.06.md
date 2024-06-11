```jsx
Name: Muhammad Abdullah
Reg. ID: BsCYS-F22-A-221546
Course: Operating System Lab
Lab Task: 06
```

## Task Number: 01
> Write a code for First Come First Serve (FCFS) Algo.

**Code:**

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

**Output:**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/CPU]
└─$ ./SJF
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

## Task Number: 02
> Write a code for Shortest Job First (SJF) Algo.

**Code**

```c
#include<stdio.h> 
void findWaitingTime(int processes[], int n,  
                          int bt[], int wt[]) 
{ 
    wt[0] = 0; 
   
    for (int  i = 1; i < n ; i++ ) 
        wt[i] =  bt[i-1] + wt[i-1] ; 
} 
   
void findTurnAroundTime( int processes[], int n,  
                  int bt[], int wt[], int tat[]) 
{ 
    for (int  i = 0; i < n ; i++) 
        tat[i] = bt[i] + wt[i]; 
} 
   
void findavgTime( int processes[], int n, int bt[]) 
{ 
    int wt[n], tat[n], total_wt = 0, total_tat = 0; 
   
    findWaitingTime(processes, n, bt, wt); 
   
    findTurnAroundTime(processes, n, bt, wt, tat); 
   
    printf("Processes   Burst time   Waiting time   Turn around time\n"); 
   
    for (int  i=0; i<n; i++) 
    { 
        total_wt = total_wt + wt[i]; 
        total_tat = total_tat + tat[i]; 
        printf("   %d ",(i+1));
        printf("       %d ", bt[i] );
        printf("       %d",wt[i] );
        printf("       %d\n",tat[i] ); 
    } 
    float s=(float)total_wt / (float)n;
    float t=(float)total_tat / (float)n;
    printf("Average waiting time = %f",s);
    printf("\n");
    printf("Average turn around time = %f ",t); 
} 
   
int main() 
{ 
    int processes[] = { 1, 2, 3}; 
    int n = sizeof processes / sizeof processes[0]; 
   
    //Burst time of all processes 
    int  burst_time[] = {10, 5, 8}; 
   
    findavgTime(processes, n,  burst_time); 
    return 0; 
} 
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
