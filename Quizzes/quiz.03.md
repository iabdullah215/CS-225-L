```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Quiz Number: 03
```

## Question

> Write a `C` program that creates multiple threads to perform specific tasks concurrently. The program should:

- Take an integer input `n`, representing the number of threads to create.
- Assign a unique task to each thread.
- Use `pthread_create` to launch the threads and `pthread_join` to ensure the main thread waits for all other threads to complete.
- Include appropriate error handling for thread creation and synchronization.

> Tasks for Each Thread:

- **Thread 1:** Calculate the sum of a list of integers.
- **Thread 2:** Find the maximum value in a list of integers.
- **Thread 3:** Sort a list of integers.
- **Thread 4:** Count the number of even and odd numbers in a list.
- **Thread 5:** Compute the factorial of a given number.

> Examply output:

```console
Thread 1: Calculated sum: 15
Thread 2: Maximum value: 9
Thread 3: Sorted list: [1, 3, 5, 7, 9]
Thread 4: Even count: 2, Odd count: 3
Thread 5: Factorial of 5: 120
```

## Question
