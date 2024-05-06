```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Lab Number: 08
```

## Lab Description:

This lab demonstrates the use of Semaphore, Types of Semaphore, Semaphore System calls, and Practical examples of Semaphore with implementation.

## Task 2:

Write a program that creates a certain number of seller threads that attempt to sell all the available tickets. There is a global variable **`num_Tickets`** which tracks the number of tickets remaining to sell. We will create many threads that will attempt to sell tickets until they are all gone. Each thread will exit after all the tickets have been sold. E.g. if we have **`4`** tickets and **`2`** seller threads then the output should be like:

```nasm
Seller #1 sold one (3 left)
Seller #0 sold one (2 left)
Seller #1 sold one (1 left)
Seller #0 sold one (0 left)
Seller #1 noticed all tickets sold! (I sold 2 myself)
Seller #0 noticed all tickets sold! (I sold 2 myself)
Done
```

## Code:

```nasm
include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <unistd.h>
#include <stdbool.h>

#define MAX_SELLERS 10

int num_Tickets = 4;
pthread_mutex_t ticket_lock;

typedef struct {
    int seller_id;
    int tickets_sold;
} Seller;

void* seller_function(void* arg) {
    Seller* seller = (Seller*)arg;
    while (true)
       {
        pthread_mutex_lock(&ticket_lock);
        if (num_Tickets > 0) {
            printf("Seller (%d) sold one (%d left)\\n", seller->seller_id, --     >num_Tic-
            >kets);
            seller->tickets_sold++;
            pthread_mutex_unlock(&ticket_lock);
        } else {
            pthread_mutex_unlock(&ticket_lock);
            break;
        }
        usleep(50000);
    }
    printf("Seller (#%d) noticed all tickets sold! (I sold %d myself)\\n", sel-
    >ler->seller_id, seller->tickets_sold);
    return NULL;
}

int main() {
    int num_sellers = 2;
    pthread_t sellers[MAX_SELLERS];
    Seller seller_data[MAX_SELLERS];
    pthread_mutex_init(&ticket_lock, NULL);
    for (int i = 0; i < num_sellers; i++)
    {
        seller_data[i].seller_id = i;
        seller_data[i].tickets_sold = 0;
        pthread_create(&sellers[i], NULL, seller_function, &seller_data[i]);
    }
    for (int i = 0; i < num_sellers; i++) {
        pthread_join(sellers[i], NULL);
    }
    printf("Done\\n");
    pthread_mutex_destroy(&ticket_lock);
    return 0;
}
```

## Code Compilation:

- First, create a file with a **`.c`** extension.

```bash
touch <file-name>.c
```

- Now open the file in a code editor like **nano.**

```bash
sudo nano <file-name>.c
```

- Now create an executable of the file.

```bash
gcc <file-name>.c -o <output-file-name>
```

- Run the executable file.

```bash
./<output-file-name>
```

## Output:

```console
┌──(MnM㉿kali)-[~/Desktop/OS-L/Tasks]
└─$ ./output                 
Seller (1) sold one (3 left)
Seller (0) sold one (2 left)
Seller (1) sold one (1 left)
Seller (0) sold one (0 left)
Seller (#1) noticed all tickets sold! (I sold 2 myself)
Seller (#0) noticed all tickets sold! (I sold 2 myself)
Done
```

---
