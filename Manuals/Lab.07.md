```jsx
Name: Muhammad Abdullah
Reg. ID: BsCYS-F22-A-221546
Course: Operating System Lab
Lab Task: 07
```

## Task Number: 01

Write a program that prints the following Using threads. Make a structure to store the following information and pass the object to a new thread:

```jsx
First Name Last Name
Class, Section
Air University Islamabad
```

## Solution:

First, create a file with the extension `**.c**`

`**touch <file-name>.c**`

Now open the file in a code editor.

`**sudo nano <file-name>.c**`

To create a `**C**` program that uses threads to print the information stored in a structure, you'll need to use the **`POSIX`** Threads library **`pthreads`**. This example demonstrates how to define a structure to hold the specified information, create a thread, and pass this structure to the new thread. The thread will then print the information.

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

typedef struct 
{
    char firstName[50];
    char lastName[50];
    char className[50];
    char section[10];
} StudentInfo;

void* printInfo(void* arg) 
{
    StudentInfo* info = (StudentInfo*)arg;

    printf("Student Information:\\n");
    printf("First Name: %s\\n", info->firstName);
    printf("Last Name: %s\\n", info->lastName);
    printf("Class: %s\\n", info->className);
    printf("Section: %s\\n", info->section);
    printf("Institution: Air University Islamabad\\n");

    pthread_exit(NULL);
}

int main() 
{
    StudentInfo student;
    snprintf(student.firstName, sizeof(student.firstName), "Muhammad");
    snprintf(student.lastName, sizeof(student.lastName), "Abdullah");
    snprintf(student.className, sizeof(student.className), "BsCYS-F22");
    snprintf(student.section, sizeof(student.section), "A");

    pthread_t thread;

    if (pthread_create(&thread, NULL, printInfo, (void*)&student) != 0) {
        perror("Failed to create thread");
        return 1;
    }

    if (pthread_join(thread, NULL) != 0) {
        perror("Failed to join thread");
        return 1;
    }

    return 0;
}
```

## Code Explanation:

This code snippet demonstrates a simple program that creates a thread and passes a structure containing student information. The thread prints the information. The **`pthread_create`** function creates a new thread, and **`pthread_join`** ensures that the main program waits for the thread to complete before exiting.

## Code Compilation:

Now first create the executable of the code file using the following command.

**`gcc <file-name>.c -o <output-file-name>`**

To run the executable use the succeeding command.

**`./<output-file-name>`**

## Output:

```console
┌──(MnM㉿kali)-[~/Desktop/Os-L/Lab-Tasks]
└─$ ./output    
Student Information:
First Name: Muhammad
Last Name: Abdullah
Class: BsCYS-F22
Section: A
Institution: Air University Islamabad
```

---

## Task Number: 02

Write a C program that prints the following series using threads.

```jsx
1                     1
1  2                  2  2
1  2  3               3  3  3
1  2  3  4            4  4  4  4
```

## Solution:

First, create a file with the extension `**.c**`

`**touch <file-name>.c**`

Now open the file in a code editor.

`**sudo nano <file-name>.c**`

To create a C program that prints the given series using threads, you'll need to define the desired output and structure the thread functions accordingly. The two specified patterns are:

1. A triangle with increasing numbers, where each row contains numbers from **`1`** to **`n`** (e.g., row 1 contains "1", row 2 contains "1 2", etc.).
2. A triangle where each row contains the same number repeated **`n`** times (e.g., row 1 contains "1", row 2 contains "2 2", etc.).

Here's a program in C that uses threads to print these two patterns separately:

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

#define MAX_ROWS 4

void* printPattern1(void* arg) {
		printf("-----------\\n");
    printf("Pattern 1:\\n-----------\\n");
    for (int i = 1; i <= MAX_ROWS; i++) {
        for (int j = 1; j <= i; j++) {
            printf("%d ", j);
        }
        printf("\\n");
    }
    printf("-----------\\n");
    pthread_exit(NULL);
}

void* printPattern2(void* arg) {
    printf("Pattern 2:\\n-----------\\n");
    for (int i = 1; i <= MAX_ROWS; i++) {
        for (int j = 1; j <= i; j++) {
            printf("%d ", i);
        }
        printf("\\n");
    }
    printf("-----------\\n");
    pthread_exit(NULL);
}

int main() {
    pthread_t thread1, thread2;

    if (pthread_create(&thread1, NULL, printPattern1, NULL) != 0) {
        perror("Failed to create thread1");
        return 1;
    }

    if (pthread_create(&thread2, NULL, printPattern2, NULL) != 0) {
        perror("Failed to create thread2");
        return 1;
    }

    if (pthread_join(thread1, NULL) != 0) {
        perror("Failed to join thread1");
        return 1;
    }

    if (pthread_join(thread2, NULL) != 0) {
        perror("Failed to join thread2");
        return 1;
    }

    return 0;
}

```

## Code Explanation:

- Two thread functions, **`printPattern1`** and **`printPattern2`**, are defined to print the specified patterns.
- The main function creates and starts both threads.
- **`pthread_join`** ensures that the main program waits for both threads to complete before exiting.

## Code Compilation:

Now first create the executable of the code file using the following command.

**`gcc <file-name>.c -o <output-file-name>`**

To run the executable use the succeeding command.

**`./<output-file-name>`**

## Output:

```console
┌──(kali㉿kali)-[~/Desktop/Os-L/Lab-Tasks]
└─$ ./output
-----------           
Pattern 2:
-----------
1 
2 2 
3 3 3 
4 4 4 4 
-----------
Pattern 1:
-----------
1 
1 2 
1 2 3 
1 2 3 4 
-----------
```
---

## Task Number: 03

Write a code for multithreading in which you should take number of threads to be created as input from user. Each created thread should display: • Thread id • Exit status • And message which should have been taken from user to be printed

## Solution:

First, create a file with the extension `**.c**`

`**touch <file-name>.c**`

Now open the file in a code editor.

`**sudo nano <file-name>.c**`

To write a C program that creates a specified number of threads and displays thread-specific information, you can use the POSIX Threads library (**`pthread.h`**). Here's a sample program that prompts the user for the number of threads to create, and for a custom message to display. Each thread displays its ID, exit status, and the message provided by the user:

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <unistd.h>

typedef struct {
    int threadIndex;
    char* message;
} ThreadData;

void* printThreadInfo(void* arg) {
    ThreadData* data = (ThreadData*)arg;

    // Get the current thread ID
    pthread_t threadId = pthread_self();

printf("Thread %d (ID: %lu) - Message: %s\\n", data->threadIndex, threadId, data->message);

    int* exitStatus = malloc(sizeof(int));
    *exitStatus = 0; 
    pthread_exit((void*)exitStatus);
}

int main() {
    int numThreads;
    char message[100];

    printf("Enter the number of threads to create: ");
    scanf("%d", &numThreads);

    printf("Enter a message to print in each thread: ");
    scanf("%s", message);

    pthread_t* threads = (pthread_t*)malloc(numThreads * sizeof(pthread_t));
    ThreadData* threadData = (ThreadData*)malloc(numThreads * sizeof(ThreadData));

    for (int i = 0; i < numThreads; i++) {
        threadData[i].threadIndex = i + 1;
        threadData[i].message = message;

      if (pthread_create(&threads[i], NULL, printThreadInfo, (void*)&threadData[i]) != 0)
        {
            perror("Failed to create thread");
            free(threads);
            free(threadData);
            return 1;
        }
    }

    for (int i = 0; i < numThreads; i++) {
        void* status;
        if (pthread_join(threads[i], &status) != 0) {
            perror("Failed to join thread");
        } else {
            int exitStatus = *(int*)status;
            printf("Thread %d exited with status %d\\n", i + 1, exitStatus);
            free(status);
        }
    }

    free(threads);
    free(threadData);
    return 0;
}

```

This program does the following:

- Takes the number of threads and a custom message as input from the user.
- Creates a specified number of threads, each of which displays its ID, the given message, and its index.
- Joins all threads and retrieves their exit status, displaying it after each thread finishes.

## Code Compilation:

Now first create the executable of the code file using the following command.

**`gcc <file-name>.c -o <output-file-name>`**

To run the executable use the succeeding command.

**`./<output-file-name>`**

## Output:

```console
┌──(MnM㉿kali)-[~/Desktop/Os-L/Lab-Tasks]
└─$ ./output
Enter the number of threads to create: 2
Enter a message to print in each thread: H_A_C_K_E_D
Thread 1 (ID: 139683137586880) - Message: H_A_C_K_E_D
Thread 2 (ID: 139683129194176) - Message: H_A_C_K_E_D
Thread 1 exited with status 0
Thread 2 exited with status 0
```

---
