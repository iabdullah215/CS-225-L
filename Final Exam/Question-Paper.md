```jsx
Course: CS-225-L - Operating System Lab
Title : Final Term Exam
Class : BSCYS-F22-IV-A
Date of Exam : June 3rd, 2024
Duration : 3 Hours (9:30 - 11:30)
Total Marks: 20
```

---
# Operating System Lab Final Term Exam
---

## Question Number 01

Write a program that creates a specified number of threads. Each thread should print its thread ID and a unique message. Use synchronization to ensure that the threads print their messages in a sequential order.
**1. Thread Creation:**
- The number of threads should be specified by the user at runtime.
- Each thread should print its thread ID and a unique message.
**2. Synchronization:**
Use a synchronization mechanism to ensure that threads print their messages sequentially, i.e., thread `0` prints first, followed by thread `1` , and so on.

---

## Question Number 02

Design a program in `C/C++` a ticket-selling system with multiple seller threads. The program should initialize a global variable `numTickets` to track the number of available tickets. Create several seller threads that attempt to sell all the tickets. Each seller thread should sell one ticket at a time until no tickets are left. The seller threads should output messages indicating the ticket they sold and the updated count of available tickets. Once all tickets are sold, each seller thread should output a final message indicating the number of tickets they sold individually. Finally, the program should print "Done" when all tickets are sold. For example, if there are 5 tickets and 3 seller threads, the output might look like:

```console
Seller #1 sold one (4 left)
Seller #2 sold one (3 left)
Seller #0 sold one (2 left)
Seller #2 sold one (1 left)
Seller #1 sold one (0 left)
Seller #1 noticed all tickets sold! (I sold 2 myself)
Seller #0 noticed all tickets sold! (I sold 1 myself)
Seller #2 noticed all tickets sold! (I sold 2 myself)
Done
```
