# Operating System Scheduling Questions

## Question 01
> Suppose that the following processes arrive for execution at the times indicated. Each process will run for the amount of time listed. In answering the questions, use non preemptive scheduling, and base all decisions on the information you have at the time the decision must be made.

| Process | Arrival Time | Burst Time |
| ------- | ------------ | ---------- |
| P1      | 0.0          | 8          |
| P2      | 0.4          | 4          |
| P3      | 1.0          | 1          |

> `a.` What is the average turnaround time for these processes with the FCFS scheduling algorithm?

> `b.` What is the average turnaround time for these processes with the SJF scheduling algorithm?

## Question 02
> What advantage is there in having different time-quantum sizes at different levels of a multilevel queueing system?

## Question 03
> A CPU scheduling algorithm determines an order for the execution of its scheduled processes. Given n processes to be scheduled on one processor, how many different schedules are possible? Give a formula in terms of n.

## Question 04
> Explain the difference between preemptive and non-preemptive scheduling.

# Solutions

# Operating System Scheduling Solutions

## Question 01

## `a.`
### Average Turnaround Time According to the FCFS:

FCFS (First-Come, First-Served) scheduling executes processes in the order they arrive. Therefore, we will calculate the turnaround time for each process and then find the average.

| Process | Arrival Time | Burst Time | Completion | Turnaround |
| ------- | ------------ | ---------- | ---------- | ---------- |
| P1      | 0.0          | 8          | 8          | 8          |
| P3      | 0.4          | 4          | 12         | 11.6       |
| P2      | 1            | 1          | 13         | 12         |

Average Turnaround Time: ((8 + 11.6 + 12)) / 3 ≈ 10.53

**Gantt Chart**

| P1 | P2 | P3 |
| -- | -- | -- |


## `b.`
### Average Turnaround Time According to the SJF:

SJF (Shortest Job First) scheduling executes the shortest job first. For non-preemptive SJF, we need to know the burst times of all processes before starting.

| Process | Arrival Time | Burst Time | Completion | Turnaround |
| ------- | ------------ | ---------- | ---------- | ---------- |
| P1      | 0.0          | 8          | 8          | 1          |
| P3      | 0.4          | 1          | 9          | 6          |
| P2      | 0.1          | 4          | 13         | 12.6       |

Average Turnaround Time: ((8 + 12.6 + 8)) / 3 ≈ 9.53

**Gantt Chart**

| P1 | P3 | P2 |
| -- | -- | -- |

## Question 02

### Advantages:

- _**Balance between short and long jobs:**_ Employing smaller time quanta in higher-priority levels ensures swift response times for critical processes while allocating larger time quanta in lower-priority levels facilitates the efficient execution of longer jobs without excessive context switching.
- _**Improved system utilization:**_ By dedicating more time to long-running jobs in lower levels with larger quanta, CPU idle time is minimized, leading to enhanced resource utilization and overall system efficiency.
- _**Flexibility for diverse processes:**_ Offering different time quanta accommodates processes with varying execution requirements, allowing the system to adapt dynamically to the needs of different workloads and optimize performance accordingly. This flexibility ensures that both short-term interactive tasks and long-term CPU-bound computations are handled effectively, promoting a balanced and responsive computing environment.

## Question 03

### Solution:

When scheduling `n` Processes on a single processor, the order of execution can be considered as a permutation of the processes. In permutations, the order matters. For `n` Processes, the number of possible permutations is given by the factorial of `n` denoted as `n!`. Therefore, the formula to calculate the number of different schedules in terms of `n` is:

Number of different schedules = `n!`

- If `n` = `3`, then the number of different schedules is `3!` = `3` x `2` x `1` = `6`.
- If `n`= `5`, then the number of different schedules is `5!` = `5` x `4` x `3` x `2` x `1` = `120`.

Therefore, the formula for the number of different schedules in terms of n is n!

## Question 04

### Preemptive vs. Non-Preemptive Scheduling

| Aspect                      | Preemptive Scheduling                                                                                                       | Non-Preemptive Scheduling                                                                                                       |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| Interruption of Processes  | The operating system can interrupt a currently executing process to start or resume another process.                      | Once a process starts execution, it continues until it terminates or voluntarily relinquishes the CPU.                            |
| Basis for Process Switching | Switching can be triggered by time slice expiration, higher priority process arrival, or completion of I/O operations.      | Process switches occur only upon completion or when the running process voluntarily yields control (e.g., waiting for I/O).       |
| Responsiveness             | Offers better responsiveness and fairness in multitasking environments.                                                    | May lead to poor responsiveness, especially if a long-running process monopolizes the CPU.                                         |
| Overhead                   | May incur more overhead due to frequent context switches.                                                                   | Usually involves less overhead compared to preemptive scheduling.                                                                |
| Implementation Complexity  | Generally more complex to implement.                                                                                      | Simpler to implement.                                                                                                            |
