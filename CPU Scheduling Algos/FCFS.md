```jsx
                  $$$$$$$$\        $$$$$$\        $$$$$$$$\        $$$$$$\  
                  $$  _____|      $$  __$$\       $$  _____|      $$  __$$\ 
                  $$ |            $$ /  \__|      $$ |            $$ /  \__|
                  $$$$$\          $$ |            $$$$$\          \$$$$$$\  
                  $$  __|         $$ |            $$  __|          \____$$\ 
                  $$ |            $$ |  $$\       $$ |            $$\   $$ |
                  $$ |            \$$$$$$  |      $$ |            \$$$$$$  |
                  \__|             \______/       \__|             \______/

                  FIRST             COME          FIRST              SERVE 
```

## Definition

FCFS is a non-preemptive scheduling algorithm used in operating systems and task management systems.

## Principle:

FCFS schedules tasks based on the order in which they arrive in the system.

## Execution:

- Tasks are executed in the same order they enter the system's queue, without any prioritization.
- Once a task starts execution, it continues until completion without interruption by other tasks.

## Characteristics:

- **Simplicity:** FCFS is straightforward to implement, making it a popular choice in many systems.
- **Fairness:** It provides fairness in task execution, as tasks are processed strictly based on their arrival time.
- **Non-preemptive:** Preemption, or interrupting a task before its completion, is not allowed in FCFS. Once a task starts execution, it runs to completion.
- **Potential for Long Waiting Times:** FCFS may lead to long waiting times for later-arriving tasks, especially if earlier tasks are long-running.

## Example:

Consider three tasks, `A`, `B`, and `C`, arriving in that order. If task `A` arrives first, it will be executed first, followed by tasks `B` and `C` in the sequence of their arrival.

## Application:

- FCFS is commonly used in scenarios where tasks have similar execution times or when simplicity in scheduling is prioritized over optimization.
- It is often seen in batch processing systems, simple task queues, and non-real-time environments.

## Limitations:

- FCFS may not be optimal in terms of minimizing average waiting times or maximizing system throughput, especially in scenarios with a mix of short and long tasks.
- It can suffer from the **_"convoy effect,"_** where short tasks are delayed significantly by long-running tasks that arrived earlier.

## Variations:

- **Shortest Job First (SJF):** A preemptive variant of FCFS where tasks are scheduled based on their expected execution time, allowing shorter tasks to execute first.
- **Round Robin (RR):** A preemptive scheduling algorithm where each task is assigned a fixed time slice, allowing tasks to be interleaved and preventing long waiting times.

## Overall:

FCFS is a fundamental scheduling algorithm that provides simplicity and fairness in task execution but may not always be the most efficient choice in terms of system performance.

## Code:

```C
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

## Output:

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/CPU]
└─$ ./FCFS
Processes  Burst time  Waiting time  Turn around time
 1           10            0              10
 2           5            10              15
 3           8            15              23
Average waiting time = 8.33333
Average turn around time = 16
```

> The output or the code may have some errors.

**For more help feel freeto visit this [website](https://www.geeksforgeeks.org/program-for-fcfs-cpu-scheduling-set-1/)**
