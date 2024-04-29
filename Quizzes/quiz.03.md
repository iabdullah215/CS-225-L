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

```C
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

typedef struct {
    int* list;
    int length;
    int result;
} ThreadData;

void* calculate_sum(void* arg) {
    ThreadData* data = (ThreadData*)arg;
    int sum = 0;
    for (int i = 0; i < data->length; i++) {
        sum += data->list[i];
    }
    data->result = sum;
    printf("Thread 1: Calculated sum: %d\n", sum);
    pthread_exit(NULL);
}

void* find_maximum(void* arg) {
    ThreadData* data = (ThreadData*)arg;
    int max = data->list[0];
    for (int i = 1; i < data->length; i++) {
        if (data->list[i] > max) {
            max = data->list[i];
        }
    }
    data->result = max;
    printf("Thread 2: Maximum value: %d\n", max);
    pthread_exit(NULL);
}

void* sort_list(void* arg) {
    ThreadData* data = (ThreadData*)arg;
    for (int i = 0; i < data->length - 1; i++) {
        for (int j = i + 1; j < data->length; j++) {
            if (data->list[i] > data->list[j]) {
                int temp = data->list[i];
                data->list[i] = data->list[j];
                data->list[j] = temp;
            }
        }
    }
    printf("Thread 3: Sorted list: [");
    for (int i = 0; i < data->length; i++) {
        if (i > 0) printf(", ");
        printf("%d", data->list[i]);
    }
    printf("]\n");
    pthread_exit(NULL);
}

void* count_even_odd(void* arg) {
    ThreadData* data = (ThreadData*)arg;
    int even_count = 0;
    int odd_count = 0;
    for (int i = 0; i < data->length; i++) {
        if (data->list[i] % 2 == 0) even_count++;
        else odd_count++;
    }
    printf("Thread 4: Even count: %d, Odd count: %d\n", even_count, odd_count);
    pthread_exit(NULL);
}

void* compute_factorial(void* arg) {
    ThreadData* data = (ThreadData*)arg;
    int n = data->result;
    int factorial = 1;
    for (int i = 1; i <= n; i++) {
        factorial *= i;
    }
    data->result = factorial;
    printf("Thread 5: Factorial of %d: %d\n", n, factorial);
    pthread_exit(NULL);
}

void show_menu() {
    printf("Choose a thread to run:\n");
    printf("1. Calculate sum\n");
    printf("2. Find maximum value\n");
    printf("3. Sort a list\n");
    printf("4. Count even and odd numbers\n");
    printf("5. Compute factorial\n");
}

int main() {
    int continue_running = 1;
    int thread_number;

    while (continue_running) {
        show_menu();
        printf("Enter your choice (1-5): ");
        scanf("%d", &thread_number);

        pthread_t thread;
        ThreadData data;
        int length, result;
        int* list;

        switch (thread_number) {
            case 1:
                printf("Enter the length of the list: ");
                scanf("%d", &length);
                list = (int*)malloc(length * sizeof(int));
                printf("Enter the elements of the list: ");
                for (int i = 0; i < length; i++) {
                    scanf("%d", &list[i]);
                }
                data.list = list;
                data.length = length;
                pthread_create(&thread, NULL, calculate_sum, (void*)&data);
                break;

            case 2:
                printf("Enter the length of the list: ");
                scanf("%d", &length);
                list = (int*)malloc(length * sizeof(int));
                printf("Enter the elements of the list: ");
                for (int i = 0; i < length; i++) {
                    scanf("%d", &list[i]);
                }
                data.list = list;
                data.length = length;
                pthread_create(&thread, NULL, find_maximum, (void*)&data);
                break;

            case 3:
                printf("Enter the length of the list: ");
                scanf("%d", &length);
                list = (int*)malloc(length * sizeof(int));
                printf("Enter the elements of the list: ");
                for (int i = 0; i < length; i++) {
                    scanf("%d", &list[i]);
                }
                data.list = list;
                data.length = length;
                pthread_create(&thread, NULL, sort_list, (void*)&data);
                break;

            case 4:
                printf("Enter the length of the list: ");
                scanf("%d", &length);
                list = (int*)malloc(length * sizeof(int));
                printf("Enter the elements of the list: ");
                for (int i = 0; i < length; i++) {
                    scanf("%d", &list[i]);
                }
                data.list = list;
                data.length = length;
                pthread_create(&thread, NULL, count_even_odd, (void*)&data);
                break;

            case 5:
                printf("Enter the number to compute factorial: ");
                scanf("%d", &result);
                data.result = result;
                pthread_create(&thread, NULL, compute_factorial, (void*)&data);
                break;

            default:
                printf("Invalid choice. Try again.\n");
                continue;
        }

        pthread_join(thread, NULL);

        free(list);

        printf("Do you want to run another task? (1 for Yes, 0 for No): ");
        scanf("%d", &continue_running);
    }

    printf("Exiting program.\n");
    return 0;
}
```

## Code Compilation:

> Creat a file with an extension `.c`.

```console
touch <file-name>.c
```

> Now make an executable file.

```console
gcc <file-name>.c -o <out-put-file-name>
```

> Fun the **exe** file.

```console
./<out-put-file-name>
```

## Output:

```console
┌──(MnM㉿kali)-[~/Desktop/Os-L/Quizzes]
└─$ ./output
----------------------
Choose a thread to run:
----------------------
1. Calculate sum
2. Find maximum value
3. Sort a list
4. Count even and odd numbers
5. Compute factorial
----------------------
Enter your choice (1-5): 1
Enter the length of the list: 2
Enter the elements of the list: 1 2
Thread 1: Calculated sum: 3
----------------------
Do you want to run another task? (1 for Yes, 0 for No): 1
----------------------
Choose a thread to run:
1. Calculate sum
2. Find maximum value
3. Sort a list
4. Count even and odd numbers
5. Compute factorial
----------------------
Enter your choice (1-5): 2
Enter the length of the list: 2
Enter the elements of the list: 2 4
Thread 2: Maximum value: 4
----------------------
Do you want to run another task? (1 for Yes, 0 for No): 3
----------------------
Choose a thread to run:
----------------------
1. Calculate sum
2. Find maximum value
3. Sort a list
4. Count even and odd numbers
5. Compute factorial
----------------------
Enter your choice (1-5): 3
Enter the length of the list: 4
Enter the elements of the list: 4 3 2 1
Thread 3: Sorted list: [1, 2, 3, 4]
----------------------
Do you want to run another task? (1 for Yes, 0 for No): 1
----------------------
Choose a thread to run:
1. Calculate sum
2. Find maximum value
3. Sort a list
4. Count even and odd numbers
5. Compute factorial
----------------------
Enter your choice (1-5): 4
Enter the length of the list: 5
Enter the elements of the list: 1 1 2 2 3 
Thread 4: Even count: 2, Odd count: 3
----------------------
Do you want to run another task? (1 for Yes, 0 for No): 1
----------------------
Choose a thread to run:
1. Calculate sum
2. Find maximum value
3. Sort a list
4. Count even and odd numbers
5. Compute factorial
----------------------
Enter your choice (1-5): 5
Enter the number to compute factorial: 2
Thread 5: Factorial of 2: 2
----------------------
free(): double free detected in tcache 2
zsh: IOT instruction  ./output
```
