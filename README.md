# menu-driven-circular-queue
## Description

This project implements a menu-driven Circular Queue of Characters using an array-based approach in C.
A circular queue efficiently utilizes memory by treating the array as circular, where the last position is connected back to the first.

The program allows the user to perform basic queue operations such as insertion, deletion, and display through a simple menu interface.

## Features

Array implementation of Circular Queue

Stores characters

Menu-driven program

Handles overflow and underflow conditions

Uses modulo arithmetic for circular behavior

## Queue Operations

Enqueue – Insert a character into the circular queue

Dequeue – Delete a character from the circular queue

Display – Show all elements present in the queue

Exit – Terminate the program

Constants Used

MAX – Defines the maximum size of the circular queue

## Conditions

Queue Full Condition

(rear + 1) % MAX == front


Queue Empty Condition

front == -1

## Code

#include <stdio.h>
#define MAX 5

char cq[MAX];
int front = -1, rear = -1;

/* Function to insert an element */
void enqueue(char item)
{
    if ((rear + 1) % MAX == front)
    {
        printf("Queue Overflow! Circular Queue is full.\n");
        return;
    }

    if (front == -1)   // First insertion
        front = 0;

    rear = (rear + 1) % MAX;
    cq[rear] = item;

    printf("Inserted: %c\n", item);
}

/* Function to delete an element */
void dequeue()
{
    if (front == -1)
    {
        printf("Queue Underflow! Circular Queue is empty.\n");
        return;
    }

    printf("Deleted: %c\n", cq[front]);

    if (front == rear)   // Queue becomes empty
    {
        front = rear = -1;
    }
    else
    {
        front = (front + 1) % MAX;
    }
}

/* Function to display the queue */
void display()
{
    int i;

    if (front == -1)
    {
        printf("Circular Queue is empty.\n");
        return;
    }

    printf("Queue elements: ");
    i = front;
    while (1)
    {
        printf("%c ", cq[i]);
        if (i == rear)
            break;
        i = (i + 1) % MAX;
    }
    printf("\n");
}

/* Main function */
int main()
{
    int choice;
    char item;

    do
    {
        printf("\n--- Circular Queue Menu ---\n");
        printf("1. Enqueue\n");
        printf("2. Dequeue\n");
        printf("3. Display\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice)
        {
        case 1:
            printf("Enter a character to insert: ");
            scanf(" %c", &item);   // space before %c is important
            enqueue(item);
            break;

        case 2:
            dequeue();
            break;

        case 3:
            display();
            break;

        case 4:
            printf("Exiting program.\n");
            break;

        default:
            printf("Invalid choice!\n");
        }
    } while (choice != 4);

    return 0;
}



## Compile
gcc circular_queue.c -o circular_queue

## Run
./circular_queue

## Sample Menu Output
--- Circular Queue Menu ---
1. Enqueue
2. Dequeue
3. Display
4. Exit
Enter your choice:

## Applications

Buffer management

CPU scheduling

Data streaming

Real-time systems

## Author
Sanjana Patil

