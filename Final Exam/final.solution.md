```jsx
Course: CS-225-L - Operating System Lab
Title : Final Term Exam Solution
Class : BSCYS-F22-IV-A
Name : Muhammad Abdullah
Reg. ID: BCSYS-F22-221546
Date of Exam : April 1st, 2024
Duration : 2 Hours (9:30 - 11:30)
Obtained Marks: 19.5
```

---
# Lab Exam Final Term Operating System
---

## Question Number: 01

**Code:**

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <string.h> // Include string.h for strcpy()

pthread_mutex_t mutex;
int current_thread = 0;

typedef struct {
    int id;
    char message[100];
} ThreadData;

void *thread_function(void *args) {
    ThreadData *thread_data = (ThreadData *)args;
    int id = thread_data->id;
    char *message = thread_data->message;
    
    pthread_mutex_lock(&mutex);
    
    while (current_thread != id) {
        pthread_mutex_unlock(&mutex);
        pthread_mutex_lock(&mutex);
    }
    
    printf("Thread %d: %s\n", id, message);
    
    current_thread++;
    pthread_mutex_unlock(&mutex);
    
    pthread_exit(NULL);
}

int main() {
    int num_threads;
    char message[100];
    
    printf("Enter the number of threads: ");
    scanf("%d", &num_threads);
    
    printf("Enter the message to print: ");
    scanf("%s", message);
    
    pthread_t threads[num_threads];
    ThreadData thread_data[num_threads];
    pthread_mutex_init(&mutex, NULL);
    
    for (int i = 0; i < num_threads; i++) {
        thread_data[i].id = i;
        strcpy(thread_data[i].message, message); // Copy message to thread_data
        pthread_create(&threads[i], NULL, thread_function, (void *)&thread_data[i]);
    }
    
    for (int i = 0; i < num_threads; i++) {
        pthread_join(threads[i], NULL);
    }
    
    pthread_mutex_destroy(&mutex);
    
    return 0;
}
```

**Output:**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Finals]
└─$ ./question1.c
Seller #0 sold one (4 left)
Seller #2 sold one (3 left)
Seller #1 sold one (2 left)
Seller #0 sold one (1 left)
Seller #2 sold one (0 left)
Seller #1 noticed all tickets sold! (I sold 2)
Seller #2 noticed all tickets sold! (I sold 1)
Seller #0 noticed all tickets sold! (I sold 2)
Done
```

---

## Question Number: 02

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <semaphore.h>
#include <unistd.h>

#define NUM_TICKETS 5
#define NUM_SELLERS 3

int num_Tickets = NUM_TICKETS;
sem_t semaphore;

void* seller(void* sellerID) {
    int sold = 0;
    while (1) {
        sem_wait(&semaphore);
        if (num_Tickets > 0) {
            num_Tickets--;
            printf("Seller #%d sold one (%d left)\n", *(int*)sellerID, num_Tickets);
            sold++;
        } else {
            printf("Seller #%d noticed all tickets sold! (I sold %d)\n", *(int*)sellerID, sold);
            sem_post(&semaphore);
            pthread_exit(NULL);
        }
        sem_post(&semaphore);
        sleep(1); 
    }
}

int main() {
    pthread_t sellers[NUM_SELLERS];
    int sellerIDs[NUM_SELLERS];
    sem_init(&semaphore, 0, 1); // Initialize semaphore
    for (int i = 0; i < NUM_SELLERS; i++) {
        sellerIDs[i] = i;
        pthread_create(&sellers[i], NULL, seller, &sellerIDs[i]);
    }
    for (int i = 0; i < NUM_SELLERS; i++) {
        pthread_join(sellers[i], NULL);
    }
    sem_destroy(&semaphore); // Destroy semaphore
    return 0;
}
```

**Output:**

```console
┌──(MnM@kali)-[~/Desktop/OS-L/Finals]
└─$ ./question2.c
Enter number of threads: 03
Enter the message to print: OSINT-KING
Thread 0: OSINT-KING
Thread 1: OSINT-KING
Thread 2: OSINT-KING
```

---
