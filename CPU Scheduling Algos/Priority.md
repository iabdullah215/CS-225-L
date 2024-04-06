```jsx
 /$$$$$$$           /$$                     /$$   /$$                      /$$$$$$            /$$                       /$$           /$$ /$$                    
| $$__  $$         |__/                    |__/  | $$                     /$$__  $$          | $$                      | $$          | $$|__/                    
| $$  \ $$ /$$$$$$  /$$  /$$$$$$   /$$$$$$  /$$ /$$$$$$   /$$   /$$      | $$  \__/  /$$$$$$$| $$$$$$$   /$$$$$$   /$$$$$$$ /$$   /$$| $$ /$$ /$$$$$$$   /$$$$$$ 
| $$$$$$$//$$__  $$| $$ /$$__  $$ /$$__  $$| $$|_  $$_/  | $$  | $$      |  $$$$$$  /$$_____/| $$__  $$ /$$__  $$ /$$__  $$| $$  | $$| $$| $$| $$__  $$ /$$__  $$
| $$____/| $$  \__/| $$| $$  \ $$| $$  \__/| $$  | $$    | $$  | $$       \____  $$| $$      | $$  \ $$| $$$$$$$$| $$  | $$| $$  | $$| $$| $$| $$  \ $$| $$  \ $$
| $$     | $$      | $$| $$  | $$| $$      | $$  | $$ /$$| $$  | $$       /$$  \ $$| $$      | $$  | $$| $$_____/| $$  | $$| $$  | $$| $$| $$| $$  | $$| $$  | $$
| $$     | $$      | $$|  $$$$$$/| $$      | $$  |  $$$$/|  $$$$$$$      |  $$$$$$/|  $$$$$$$| $$  | $$|  $$$$$$$|  $$$$$$$|  $$$$$$/| $$| $$| $$  | $$|  $$$$$$$
|__/     |__/      |__/ \______/ |__/      |__/   \___/   \____  $$       \______/  \_______/|__/  |__/ \_______/ \_______/ \______/ |__/|__/|__/  |__/ \____  $$
                                                          /$$  | $$                                                                                     /$$  \ $$
                                                         |  $$$$$$/                                                                                    |  $$$$$$/
                                                          \______/                                                                                      \______/
```

## Definition:

Priority Scheduling is a non-preemptive or preemptive scheduling algorithm used in operating systems and task management systems.

## Principle:

Priority Scheduling assigns a priority level to each task, and tasks with higher priority levels are executed before tasks with lower priority levels.

## Execution:

- In non-preemptive Priority Scheduling, the CPU is allocated to the highest priority task in the ready queue, and the task continues to execute until completion.
- In preemptive Priority Scheduling, a task with a higher priority can preempt a currently executing task with a lower priority. The preempted task is placed back into the ready queue.

## Characteristics:

- **Flexibility:** Priority Scheduling allows for flexible task management by assigning different priority levels to tasks based on their importance or urgency.
- **Responsiveness:** Preemptive Priority Scheduling provides better responsiveness compared to non-preemptive Priority Scheduling, as higher priority tasks can interrupt lower priority tasks.
- **Starvation:** Lower priority tasks may suffer from starvation if higher priority tasks continuously arrive, as they may not get an opportunity to execute.

## Example:

Suppose four tasks, `A`, `B`, `C`, and `D`, with priority levels `1`, `2`, `3`, and `4`, respectively, are in the ready queue. Task `D`, with the highest priority, will be executed first, followed by tasks `C`, `B`, and `A` in descending order of priority.

## Application:

- Priority Scheduling is suitable for environments where tasks have different levels of importance or urgency.
- It is commonly used in real-time systems, where tasks must meet specific deadlines or response times.

## Limitations:

- **Priority Inversion:** Lower priority tasks may hold resources required by higher priority tasks, leading to priority inversion and degraded system performance.
- **Priority Aging:** Without priority aging mechanisms, lower priority tasks may starve if higher priority tasks continue to arrive.

## Variations:

- **Dynamic Priority Scheduling:** A variant of Priority Scheduling where task priorities are adjusted dynamically based on factors such as waiting time or resource usage.
- **Multilevel Feedback Queue:** Combines Priority Scheduling with multiple priority queues and aging mechanisms to provide better task management and prevent starvation.

## Overall:

Priority Scheduling is a versatile scheduling algorithm that allows for flexible task management based on priority levels. It is suitable for environments where tasks have varying levels of importance or urgency, but careful consideration is needed to prevent issues such as priority inversion or starvation. Preemptive Priority Scheduling provides better responsiveness but may incur higher overhead compared to non-preemptive Priority Scheduling.

## Code:

```C++
#include <bits/stdc++.h> 
using namespace std; 
  
struct Process { 
    int pid;
    int bt;
    int priority;
}; 
  
bool comparison(Process a, Process b) 
{ 
    return (a.priority > b.priority); 
} 
  
void findWaitingTime(Process proc[], int n, int wt[]) 
{ 
    wt[0] = 0; 
  
    for (int i = 1; i < n; i++) 
        wt[i] = proc[i - 1].bt + wt[i - 1]; 
} 
  
void findTurnAroundTime(Process proc[], int n, int wt[], int tat[]) 
{ 
    for (int i = 0; i < n; i++) 
        tat[i] = proc[i].bt + wt[i]; 
} 
  
void findavgTime(Process proc[], int n) 
{ 
    int wt[n], tat[n], total_wt = 0, total_tat = 0; 
  
    findWaitingTime(proc, n, wt); 
  
    findTurnAroundTime(proc, n, wt, tat); 
  
    cout << "\nProcesses  "
         << " Burst time  "
         << " Waiting time  "
         << " Turn around time\n"; 
  
    for (int i = 0; i < n; i++) { 
        total_wt = total_wt + wt[i]; 
        total_tat = total_tat + tat[i]; 
        cout << "   " << proc[i].pid << "\t\t" << proc[i].bt 
             << "\t    " << wt[i] << "\t\t  " << tat[i] 
             << endl; 
    } 
  
    cout << "\nAverage waiting time = "
         << (float)total_wt / (float)n; 
    cout << "\nAverage turn around time = "
         << (float)total_tat / (float)n; 
} 
  
void priorityScheduling(Process proc[], int n) 
{ 
    sort(proc, proc + n, comparison); 
  
    cout << "Order in which processes gets executed \n"; 
    for (int i = 0; i < n; i++) 
        cout << proc[i].pid << " "; 
  
    findavgTime(proc, n); 
} 
  
int main() 
{ 
    Process proc[] = { { 1, 10, 2 }, { 2, 5, 0 }, { 3, 8, 1 } }; 
    int n = sizeof proc / sizeof proc[0]; 
    priorityScheduling(proc, n); 
    return 0; 
}
```

## Output

```linux
┌──(MnM@kali)-[~/Desktop/OS-L/CPU]
└─$ ./Priority
Order in which processes gets executed 
1 3 2 
Processes  Burst time  Waiting time  Turn around time
 1        10     0         10
 3        8     10         18
 2        5     18         23

Average waiting time = 9.33333
Average turn around time = 17
```

> The code or the output may have errors in it

**Visit the [website](https://www.geeksforgeeks.org/program-for-priority-cpu-scheduling-set-1/) for more**
