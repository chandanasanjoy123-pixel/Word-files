#include <stdio.h>
#define MAX 10

int queue[MAX];
int front = -1;
int rear = -1;

void enqueue() {
    int value;

    if(rear == MAX - 1) {
        printf("Queue Overflow\n");
    }
    else {
        printf("Enter value: ");
        scanf("%d", &value);

        if(front == -1) {
            front = 0;
        }

        rear++;
        queue[rear] = value;

        printf("Inserted Successfully\n");
    }
}

void dequeue() {

    if(front == -1 || front > rear) {
        printf("Queue Underflow\n");
    }
    else {
        printf("Deleted element = %d\n", queue[front]);
        front++;

        if(front > rear) {
            front = rear = -1;
        }
    }
}

void display() {
    int i;

    if(front == -1) {
        printf("Queue is Empty\n");
    }
    else {
        printf("Queue elements are:\n");

        for(i = front; i <= rear; i++) {
            printf("%d ", queue[i]);
        }
        printf("\n");
    }
}

int main() {

    int choice;

    do {
        printf("\n--- LINEAR QUEUE MENU ---\n");
        printf("1. Enqueue\n");
        printf("2. Dequeue\n");
        printf("3. Display\n");
        printf("4. Exit\n");

        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {

            case 1:
                enqueue();
                break;

            case 2:
                dequeue();
                break;

            case 3:
                display();
                break;

            case 4:
                printf("Program Exited\n");
                break;

            default:
                printf("Invalid Choice\n");
        }

    } while(choice != 4);

    return 0;
}
OUTPUT:-

--- LINEAR QUEUE MENU ---
1. Enqueue
2. Dequeue
3. Display
4. Exit
Enter choice: 1
Enter value: 25
Inserted Successfully

--- LINEAR QUEUE MENU ---
1. Enqueue
2. Dequeue
3. Display
4. Exit
Enter choice: 2
Deleted element = 25

--- LINEAR QUEUE MENU ---
1. Enqueue
2. Dequeue
3. Display
4. Exit
Enter choice: 3
Queue is Empty

--- LINEAR QUEUE MENU ---
1. Enqueue
2. Dequeue
3. Display
4. Exit
Enter choice: 4
Program Exited
3#include <stdio.h>
#define MAX 10

int deque[MAX];
int front = -1;
int rear = -1;

void insertFront(int value) {

    if(front == 0) {
        printf("Insertion at front not possible\n");
    }
    else if(front == -1) {
        front = rear = 0;
        deque[front] = value;
        printf("Inserted at Front\n");
    }
    else {
        front = front - 1;
        deque[front] = value;
        printf("Inserted at Front\n");
    }
}

void insertRear(int value) {

    if(rear == MAX - 1) {
        printf("Deque Overflow\n");
    }
    else if(front == -1) {
        front = rear = 0;
        deque[rear] = value;
        printf("Inserted at Rear\n");
    }
    else {
        rear = rear + 1;
        deque[rear] = value;
        printf("Inserted at Rear\n");
    }
}

void deleteFront() {

    if(front == -1) {
        printf("Deque Underflow\n");
    }
    else {
        printf("Deleted element = %d\n", deque[front]);

        if(front == rear) {
            front = rear = -1;
        }
        else {
            front = front + 1;
        }
    }
}

void deleteRear() {

    if(front == -1) {
        printf("Deque Underflow\n");
    }
    else {
        printf("Deleted element = %d\n", deque[rear]);

        if(front == rear) {
            front = rear = -1;
        }
        else {
            rear = rear - 1;
        }
    }
}

void display() {

    int i;

    if(front == -1) {
        printf("Deque is Empty\n");
    }
    else {
        printf("Deque elements are:\n");

        for(i = front; i <= rear; i++) {
            printf("%d ", deque[i]);
        }

        printf("\n");
    }
}

int main() {

    int choice, value;

    do {

        printf("\n--- DEQUE MENU ---\n");
        printf("1. Insert Front\n");
        printf("2. Insert Rear\n");
        printf("3. Delete Front\n");
        printf("4. Delete Rear\n");
        printf("5. Display\n");
        printf("6. Exit\n");

        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {

            case 1:
                printf("Enter value: ");
                scanf("%d", &value);
                insertFront(value);
                break;

            case 2:
                printf("Enter value: ");
                scanf("%d", &value);
                insertRear(value);
                break;

            case 3:
                deleteFront();
                break;

            case 4:
                deleteRear();
                break;

            case 5:
                display();
                break;

            case 6:
                printf("Program Exited\n");
                break;

            default:
                printf("Invalid Choice\n");
        }

    } while(choice != 6);

    return 0;
}
OUTPUT:-

--- DEQUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter choice: 1
Enter value: 10
Inserted at Front

--- DEQUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter choice: 2
Enter value: 20
Inserted at Rear

--- DEQUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter choice: 3
Deleted element = 10

--- DEQUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter choice: 30
Invalid Choice

--- DEQUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter choice: 4
Deleted element = 20

--- DEQUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter choice: 5
Deque is Empty

--- DEQUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter choice: 6
Program Exited
4. #include <stdio.h>

#define MAX 10

int cqueue[MAX];
int front = -1;
int rear = -1;

void enqueue() {
    
    int value;

    // Check Overflow
    if((front == 0 && rear == MAX - 1) || (front == rear + 1)) {
        printf("Circular Queue Overflow\n");
    }
    else {

        printf("Enter value: ");
        scanf("%d", &value);

        // First element insertion
        if(front == -1) {
            front = rear = 0;
        }

        // Circular increment
        else if(rear == MAX - 1) {
            rear = 0;
        }

        else {
            rear++;
        }

        cqueue[rear] = value;

        printf("Inserted Successfully\n");
    }
}

void dequeue() {

    // Check Underflow
    if(front == -1) {
        printf("Circular Queue Underflow\n");
    }
    else {

        printf("Deleted element = %d\n", cqueue[front]);

        // Only one element
        if(front == rear) {
            front = rear = -1;
        }

        // Circular increment
        else if(front == MAX - 1) {
            front = 0;
        }

        else {
            front++;
        }
    }
}

void display() {

    int i;

    if(front == -1) {
        printf("Circular Queue is Empty\n");
    }
    else {

        printf("Circular Queue elements are:\n");

        // If rear >= front
        if(rear >= front) {

            for(i = front; i <= rear; i++) {
                printf("%d ", cqueue[i]);
            }
        }

        // If queue is circular
        else {

            for(i = front; i < MAX; i++) {
                printf("%d ", cqueue[i]);
            }

            for(i = 0; i <= rear; i++) {
                printf("%d ", cqueue[i]);
            }
        }

        printf("\n");
    }
}

int main() {

    int choice;

    do {

        printf("\n--- CIRCULAR QUEUE MENU ---\n");
        printf("1. Insertion\n");
        printf("2. Deletion\n");
        printf("3. Display\n");
        printf("4. Exit\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {

            case 1:
                enqueue();
                break;

            case 2:
                dequeue();
                break;

            case 3:
                display();
                break;

            case 4:
                printf("Program Exited\n");
                break;

            default:
                printf("Invalid Choice\n");
        }

    } while(choice != 4);

    return 0;
}
OUTPUT:-

--- CIRCULAR QUEUE MENU ---
1. Insertion
2. Deletion
3. Display
4. Exit
Enter your choice: 1
Enter value: 46
Inserted Successfully

--- CIRCULAR QUEUE MENU ---
1. Insertion
2. Deletion
3. Display
4. Exit
Enter your choice: 2
Deleted element = 46

--- CIRCULAR QUEUE MENU ---
1. Insertion
2. Deletion
3. Display
4. Exit
Enter your choice: 3
Circular Queue is Empty

--- CIRCULAR QUEUE MENU ---
1. Insertion
2. Deletion
3. Display
4. Exit
Enter your choice: 4
Program Exited
5. #include <stdio.h>

#define MAX 10

int deque[MAX];
int front = -1;
int rear = -1;

void insertFront() {

    int value;

    // Overflow condition
    if((front == 0 && rear == MAX - 1) || (front == rear + 1)) {
        printf("Deque Overflow\n");
        return;
    }

    printf("Enter value: ");
    scanf("%d", &value);

    // First element
    if(front == -1) {
        front = rear = 0;
    }

    // Circular movement
    else if(front == 0) {
        front = MAX - 1;
    }

    else {
        front--;
    }

    deque[front] = value;

    printf("Inserted at Front\n");
}

void insertRear() {

    int value;

    // Overflow condition
    if((front == 0 && rear == MAX - 1) || (front == rear + 1)) {
        printf("Deque Overflow\n");
        return;
    }

    printf("Enter value: ");
    scanf("%d", &value);

    // First element
    if(front == -1) {
        front = rear = 0;
    }

    // Circular movement
    else if(rear == MAX - 1) {
        rear = 0;
    }

    else {
        rear++;
    }

    deque[rear] = value;

    printf("Inserted at Rear\n");
}

void deleteFront() {

    // Underflow condition
    if(front == -1) {
        printf("Deque Underflow\n");
        return;
    }

    printf("Deleted element = %d\n", deque[front]);

    // Only one element
    if(front == rear) {
        front = rear = -1;
    }

    // Circular movement
    else if(front == MAX - 1) {
        front = 0;
    }

    else {
        front++;
    }
}

void deleteRear() {

    // Underflow condition
    if(front == -1) {
        printf("Deque Underflow\n");
        return;
    }

    printf("Deleted element = %d\n", deque[rear]);

    // Only one element
    if(front == rear) {
        front = rear = -1;
    }

    // Circular movement
    else if(rear == 0) {
        rear = MAX - 1;
    }

    else {
        rear--;
    }
}

void display() {

    int i;

    if(front == -1) {
        printf("Deque is Empty\n");
        return;
    }

    printf("Deque elements are:\n");

    i = front;

    while(i != rear) {
        printf("%d ", deque[i]);

        i = (i + 1) % MAX;
    }

    printf("%d", deque[rear]);

    printf("\n");
}

int main() {

    int choice;

    do {

        printf("\n--- DOUBLE CIRCULAR QUEUE MENU ---\n");
        printf("1. Insert Front\n");
        printf("2. Insert Rear\n");
        printf("3. Delete Front\n");
        printf("4. Delete Rear\n");
        printf("5. Display\n");
        printf("6. Exit\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {

            case 1:
                insertFront();
                break;

            case 2:
                insertRear();
                break;

            case 3:
                deleteFront();
                break;

            case 4:
                deleteRear();
                break;

            case 5:
                display();
                break;

            case 6:
                printf("Program Exited\n");
                break;

            default:
                printf("Invalid Choice\n");
        }

    } while(choice != 6);

    return 0;
}
OUTPUT:-

--- DOUBLE CIRCULAR QUEUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter your choice: 1
Enter value: 10
Inserted at Front

--- DOUBLE CIRCULAR QUEUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter your choice: 2
Enter value: 20
Inserted at Rear

--- DOUBLE CIRCULAR QUEUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter your choice: 3
Deleted element = 10

--- DOUBLE CIRCULAR QUEUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter your choice: 4
Deleted element = 20

--- DOUBLE CIRCULAR QUEUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter your choice: 5
Deque is Empty

--- DOUBLE CIRCULAR QUEUE MENU ---
1. Insert Front
2. Insert Rear
3. Delete Front
4. Delete Rear
5. Display
6. Exit
Enter your choice: 6
Program Exited


