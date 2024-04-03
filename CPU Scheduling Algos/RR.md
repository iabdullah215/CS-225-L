```jsx
                                    $$$$$$$\        $$$$$$$\  
                                    $$  __$$\       $$  __$$\ 
                                    $$ |  $$ |      $$ |  $$ |
                                    $$$$$$$  |      $$$$$$$  |
                                    $$  __$$<       $$  __$$< 
                                    $$ |  $$ |      $$ |  $$ |
                                    $$ |  $$ |      $$ |  $$ |
                                    \__|  \__|      \__|  \__|

                                      ROUND           ROBIN                           
```

## Definition:

Round Robin (RR) is a preemptive scheduling algorithm used in operating systems and task management systems.

## Principle:

RR schedules tasks in a circular queue fashion, allowing each task to execute for a fixed time slice called a time quantum.

## Execution:

- Tasks are executed in a cyclic manner, with each task getting a turn to execute for a fixed time quantum.
- Once a task's time quantum expires, it is preempted, and the CPU is allocated to the next task in the queue.
- If a task does not complete within its time quantum, it is placed at the end of the queue to wait for its next turn.

## Characteristics:

- **Fairness:** RR provides fairness in task execution by giving each task an equal opportunity to execute within the time quantum.
- **Responsiveness:** It offers better responsiveness compared to non-preemptive algorithms, as tasks are regularly preempted, allowing for quicker context switches.
- **Time Quantum:** The choice of time quantum affects system performance and responsiveness. A shorter time quantum provides better responsiveness but may lead to higher overhead due to frequent context switches.

## Example:

Suppose four tasks, `A`, `B`, `C`, and `D`, are in the ready queue, and the time quantum is set to `3` units. The execution order might be: `A`, `B`, `C`, `D`, `A`, `B`, `C`, `D`, and so on.

## Application:

- RR is commonly used in time-sharing systems and environments where fairness and responsiveness are important.
- It is suitable for scenarios where tasks have similar priority levels or where preemptive scheduling is preferred.

## Limitations:

- **Higher Overhead:** RR may incur higher overhead due to frequent context switches, especially with shorter time quanta.
- **Performance Impact:** The performance of RR can degrade if the time quantum is too long or too short compared to the average task execution time.

## Variations:

- **Dynamic Round Robin:** A variant of RR where the time quantum dynamically adjusts based on the characteristics of the tasks in the queue.
- **Multilevel Queue with Round Robin:** Combines RR with multiple priority queues, allowing for more flexible scheduling based on task priority levels.

## Overall:

RR is a widely used preemptive scheduling algorithm that provides fairness and responsiveness in task execution. While it may incur higher overhead compared to non-preemptive algorithms, it is suitable for environments where fairness and quick context switches are essential. Adjusting the time quantum can significantly impact system performance and responsiveness.

## Code:

> Round Robin

```C++
#include<iostream> 
using namespace std; 

void findWaitingTime(int processes[], int n, 
            int bt[], int wt[], int quantum) 
{ 
    int rem_bt[n]; 
    for (int i = 0 ; i < n ; i++) 
        rem_bt[i] = bt[i]; 
 
    int t = 0; 
 
    while (1) 
    { 
        bool done = true; 
 
        for (int i = 0 ; i < n; i++) 
        { 
            if (rem_bt[i] > 0) 
            { 
                done = false; 
 
                if (rem_bt[i] > quantum) 
                { 
                    t += quantum; 
 
                    rem_bt[i] -= quantum; 
                } 
 
                else
                { 
                    t = t + rem_bt[i]; 
 
                    wt[i] = t - bt[i]; 
 
                    rem_bt[i] = 0; 
                } 
            } 
        } 
 
        if (done == true) 
        break; 
    } 
} 

void findTurnAroundTime(int processes[], int n, 
                        int bt[], int wt[], int tat[]) 
{ 
    for (int i = 0; i < n ; i++) 
        tat[i] = bt[i] + wt[i]; 
} 
 
void findavgTime(int processes[], int n, int bt[], 
                                    int quantum) 
{ 
    int wt[n], tat[n], total_wt = 0, total_tat = 0; 
 
    findWaitingTime(processes, n, bt, wt, quantum); 
 
    findTurnAroundTime(processes, n, bt, wt, tat); 

    cout << "PN\t "<< " \tBT "
        << "  WT " << " \tTAT\n"; 
 
    for (int i=0; i<n; i++) 
    { 
        total_wt = total_wt + wt[i]; 
        total_tat = total_tat + tat[i]; 
        cout << " " << i+1 << "\t\t" << bt[i] <<"\t "
            << wt[i] <<"\t\t " << tat[i] <<endl; 
    } 
 
    cout << "Average waiting time = "
        << (float)total_wt / (float)n; 
    cout << "\nAverage turn around time = "
        << (float)total_tat / (float)n; 
} 
 
int main() 
{  
    int processes[] = { 1, 2, 3}; 
    int n = sizeof processes / sizeof processes[0]; 

    int burst_time[] = {10, 5, 8}; 
 
    int quantum = 2; 
    findavgTime(processes, n, burst_time, quantum); 
    return 0; 
} 
```

> Output

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/CPU]
└─$ ./RR
PN	     BT    WT      TAT
1		     10	   13		    23
2		     5	   10		    15
3		     8	   14		    22
Average waiting time = 12.3333
Average turn around time = 20
```

> With priority

```C++

```

> Output

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/CPU]
└─$ ./RR
PN	     BT    WT      TAT   Priority
 1		   10	   7		   17		 3
 3		   8	   2		   10		 2
 2		   5	   0		   5		 1
Average waiting time = 3
Average turn around time = 10.6667
```

> The code and the output may have errors.

**Visit this [website](https://www.geeksforgeeks.org/program-for-round-robin-scheduling-for-the-same-arrival-time/) to read more about RR** 
