```jsx
				$$$$$$\           $$$$$\       $$$$$$$$\ 
                               $$  __$$\          \__$$ |      $$  _____|
                               $$ /  \__|            $$ |      $$ |      
                               \$$$$$$\              $$ |      $$$$$\    
                                \____$$\       $$\   $$ |      $$  __|   
                               $$\   $$ |      $$ |  $$ |      $$ |      
                               \$$$$$$  |      \$$$$$$  |      $$ |      
                                \______/        \______/       \__|

                                SHORTEST           JOB         FIRST
```

## Definition:

Shortest Job First (SJF) is a preemptive or non-preemptive scheduling algorithm used in operating systems and task management systems.

## Principle:

SJF schedules tasks based on their expected execution time, also known as burst time.

## Execution:

- In non-preemptive SJF, the task with the shortest burst time is selected for execution first.
- In preemptive SJF, if a new task arrives with a shorter burst time than the currently executing task, the CPU is preempted, and the shorter task is executed first.

## Characteristics:

- **Efficiency:** SJF aims to minimize average waiting time and maximize system throughput by executing shorter tasks first.
- **Fairness:** Shorter tasks are prioritized over longer tasks, leading to a fairer distribution of CPU resources.
- **Preemption:** In preemptive SJF, tasks can be interrupted if a shorter task arrives, allowing for better responsiveness.

## Example:

Consider three tasks, `A`, `B`, and `C`, with burst times of `4`, `2`, and `6` units, respectively. In non-preemptive SJF, task `B` will be executed first, followed by task `A` and then task `C`.

## Application:

- SJF is beneficial in scenarios where tasks have varying execution times and minimizing average waiting time is crucial.
- It is commonly used in batch processing systems, job scheduling in operating systems, and time-sharing environments.

## Limitations:

- **Starvation:** Longer tasks may suffer from starvation if shorter tasks continuously arrive, as they may never get a chance to execute.
- **Estimation of Burst Time:** SJF requires accurate estimation of task burst times, which may not always be feasible in practical systems.

## Variations:

- **Shortest Remaining Time First (SRTF):** A preemptive variant of SJF where tasks are scheduled based on their remaining burst time rather than their initial burst time.
- **Priority Scheduling:** Similar to SJF, but tasks are scheduled based on priority levels assigned to them, allowing for more flexible task management.

## Overall:

SJF is an effective scheduling algorithm for minimizing average waiting time and maximizing system throughput, especially in scenarios with varying task execution times. However, it requires accurate estimation of task burst times and may suffer from starvation in certain situations.

## Code 

> **Shortest Job First**

```C
#include <stdio.h>
int main()
{
	int A[100][4];
	int i, j, n, total = 0, index, temp;
	float avg_wt, avg_tat;
	printf("Enter number of process: ");
	scanf("%d", &n);
	printf("Enter Burst Time:\n");
	for (i = 0; i < n; i++) {
		printf("P%d: ", i + 1);
		scanf("%d", &A[i][1]);
		A[i][0] = i + 1;
	}
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
	printf("P	 BT	 WT	 TAT\n");
	for (i = 0; i < n; i++) {
		A[i][3] = A[i][1] + A[i][2];
		total += A[i][3];
		printf("P%d	 %d	 %d	 %d\n", A[i][0],
			A[i][1], A[i][2], A[i][3]);
	}
	avg_tat = (float)total / n;
	printf("Average Waiting Time= %f", avg_wt);
	printf("\nAverage Turnaround Time= %f", avg_tat);
}
```

> **Output**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/CPU]
└─$ ./SJF
Enter number of process: 5
Enter Burst Time:
P1: 6
P2: 3
P3: 8
P4: 2
P5: 7
P	 BT	 WT	 TAT
P4	 2	 0	 2
P2	 3	 2	 5
P5	 7	 5	 12
P1	 6	 8	 14
P3	 8	 14	 22
Average Waiting Time= 5.800000
Average Turnaround Time= 11.000000
```

> **Shortest Remaining Time First**

```C
#include <stdio.h> 
#include <stdbool.h> 
  
#define MAX_PROCESSES 100 
  
struct process { 
    int pid; 
    int arrival_time; 
    int burst_time; 
    int remaining_time; 
}; 
  
int main() { 
    int n; 
    struct process processes[MAX_PROCESSES]; 
    bool completed[MAX_PROCESSES] = {false}; 
    int current_time = 0; 
    int shortest_time = 0; 
    int shortest_index = 0; 
  
    printf("Enter the number of processes: "); 
    scanf("%d", &n); 
  
    for (int i = 0; i < n; i++) { 
        printf("Enter arrival time and burst time for process %d: ", i+1); 
        scanf("%d %d", &processes[i].arrival_time, &processes[i].burst_time); 
        processes[i].pid = i+1; 
        processes[i].remaining_time = processes[i].burst_time; 
    } 
  
    printf("\n"); 
  
    while (true) { 
        bool completed_all = true; 
        for (int i = 0; i < n; i++) { 
            if (!completed[i]) { 
                all_completed = false; 
                if (processes[i].arrival_time <= current_time && 
                    processes[i].remaining_time < processes[shortest_index].remaining_time) { 
                    shortest_index = i; 
                } 
            } 
        } 
        if (completed_all) { 
            break; 
        } 
        if (shortest_index != -1) { 
            processes[shortest_index].remaining_time--; 
            if (processes[shortest_index].remaining_time == 0) { 
                completed[shortest_index] = true; 
            } 
        } 
        current_time++; 
        shortest_index = -1; 
    } 
  
    printf("Process\tArrival Time\tBurst Time\tWaiting Time\tTurnAround Time\n"); 
  
    int total_waiting_time = 0; 
    int total_turnaround_time = 0; 
    for (int i = 0; i < n; i++) { 
        int waiting_time = 0; 
        int turnaround_time = 0; 
        waiting_time = current_time - processes[i].burst_time - processes[i].arrival_time; 
        turnaround_time = current_time - processes[i].arrival_time; 
        total_waiting_time += waiting_time; 
        total_turnaround_time += turnaround_time; 
        printf("%d\t%d\t\t%d\t\t%d\t\t%d\n", processes[i].pid, processes[i].arrival_time, processes[i].burst_time, waiting_time, turnaround_time); 
    } 
  
    float avg_waiting_time = (float) total_waiting_time / n; 
    float avg_turnaround_time = (float) total_turnaround_time / n; 
  
    printf("The Average Waiting Time: %.2f\n", avg_waiting_time); 
    printf("The Average Turnaround Time: %.2f\n", avg_turnaround_time); 
  
    return 0; 
}
```

> **Output**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/CPU]
└─$ ./SRTF
Enter the number of processes: 4
Enter arrival time and burst time for the process 1: 1 4
Enter arrival time and burst time for the process 2: 2 7
Enter arrival time and burst time for the process 3: 5 10
Enter arrival time and burst time for the process 4: 6 12

Process Arrival Time    Burst Time    Waiting Time    Turnaround Time
        1               4             28              32
        2               7             24              31
        5               10            18              28
        6               12            15              27
Average Waiting Time: 21.25
Average Turnaround Time: 29.50
```

> The code or the output may have some errors.

**Wisit this website to read more about [SRTF](https://www.geeksforgeeks.org/shortest-remaining-time-first-srtf-with-predicted-time/) and [SJF](https://www.geeksforgeeks.org/program-for-shortest-job-first-or-sjf-cpu-scheduling-set-1-non-preemptive/)**
