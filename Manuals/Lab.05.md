```jsx
Course: CS-225-L - Operating System Lab
Name : Muhammad Abdullah
Reg. ID: BS-CYS-F22-221546
Lab Number: 05
```

# C Programming and System Calls

This lab contains basic scripts to demonstrate the usage of System Calls.

## File Creation:
> First, create an empty file by name `system_calls.c`

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ touch system_calls.c

┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ls
hello.sh  system_calls.c
```

## Code Compilation

> `Nano` file editor can be used to edit the file and write code in it.

```bash
sudo nano system_calls.c
```

> Creating an executable `exe` file we'll use the `gcc` compiler

```bash
gcc system_calls.c -o output
```

> Runing the code

```bash
./output
```

## Lab Codes

**Task Number: 01**

> Write a code to explain the use of `fork()` system call

**Code:**

```C
#include <stdio.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <unistd.h>

int main()
{
    pid_t cpid;

    if (for() == 0)
    {
        exit(0);
    }
    else
    {
        cpid = wait(NULL);
        printf("Parent pid = %d\n" , getpid());
        printf("Child pid = %d\n" , cpid);
    }

    return 0;
}
```

**Output:**

```bash
┌──(MnM@kali)-[~/Desktop/OS-L/Tasks]
└─$ ./output
Parent pid = 8890
Child pid = 8891
```

**Explanation**

This `C` program uses the `fork()` system call to create a child process. In the child process, it immediately exits, terminating the child. The parent process waits for the child to complete using `wait()`, capturing the child's process ID. Finally, both the parent and child processes print their respective process `IDs`, demonstrating the creation and termination of the child process.

**Task Number: 02**

> Expalin the use case of `Zombie`

**Code:**

