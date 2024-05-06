
```bash
Name: Muhammad Abdullah
Reg ID: F22-A-221546
Lab Task: 
```

## Lab Description:

This lab demonstrates the use of Multithreading and Synchronization.

## Task 2:

Create a program which has two thread functions, one thread increments a variable and the other decrements the same variable after increment. Use Mutex lock and unlock for synchronization of incrementing and decrementing a variable.

## Code:

```nasm
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <unistd.h>

int shared_variable = 0;
pthread_mutex_t variable_lock;

void* increment_function(void* arg) {
    pthread_mutex_lock(&variable_lock);
    shared_variable++;
    printf("Incremented to %d\\n", shared_variable);
    pthread_mutex_unlock(&variable_lock);
    return NULL;
}

void* decrement_function(void* arg) {
    pthread_mutex_lock(&variable_lock);
    shared_variable--;
    printf("Decremented to %d\\n", shared_variable);
    pthread_mutex_unlock(&variable_lock);
    return NULL;
}

int main() {
    pthread_mutex_init(&variable_lock, NULL);

    pthread_t inc_thread;
    pthread_t dec_thread;

    pthread_create(&inc_thread, NULL, increment_function, NULL);
    pthread_join(inc_thread, NULL);

    pthread_create(&dec_thread, NULL, decrement_function, NULL);
    pthread_join(dec_thread, NULL);

    pthread_mutex_destroy(&variable_lock);

    return 0;
}
```

## Code Compilation:

- First, create a file with a `**.c`** extension.

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
Incremented to 1
Decremented to 0
```
