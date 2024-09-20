#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct CircularQueue {
    struct Node *front, *rear;
};

struct Node* createNode(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;
    return newNode;
}

struct CircularQueue* createQueue() {
    struct CircularQueue* queue = (struct CircularQueue*)malloc(sizeof(struct CircularQueue));
    queue->front = queue->rear = NULL;
    return queue;
}

void enQueue(struct CircularQueue* queue, int value) {
    struct Node* newNode = createNode(value);
    if (queue->front == NULL) {
        queue->front = queue->rear = newNode;
        queue->rear->next = queue->front;
    } else {
        queue->rear->next = newNode;
        queue->rear = newNode;
        queue->rear->next = queue->front;
    }
}

int deQueue(struct CircularQueue* queue) {
    if (queue->front == NULL) {
        printf("Queue is empty\n");
        return -1;
    }
    int value;
    if (queue->front == queue->rear) {
        value = queue->front->data;
        free(queue->front);
        queue->front = queue->rear = NULL;
    } else {
        struct Node* temp = queue->front;
        value = temp->data;
        queue->front = queue->front->next;
        queue->rear->next = queue->front;
        free(temp);
    }
    return value;
}

int getFront(struct CircularQueue* queue) {
    if (queue->front == NULL) {
        printf("Queue is empty\n");
        return -1;
    }
    return queue->front->data;
}

int getRear(struct CircularQueue* queue) {
    if (queue->rear == NULL) {
        printf("Queue is empty\n");
        return -1;
    }
    return queue->rear->data;
}

void displayQueue(struct CircularQueue* queue) {
    if (queue->front == NULL) {
        printf("Queue is empty\n");
        return;
    }
    struct Node* temp = queue->front;
    do {
        printf("%d ", temp->data);
        temp = temp->next;
    } while (temp != queue->front);
    printf("\n");
}

int main() {
    struct CircularQueue* queue = createQueue();

    enQueue(queue, 10);
    enQueue(queue, 20);
    enQueue(queue, 30);
    enQueue(queue, 40);

    printf("Front item: %d\n", getFront(queue));
    printf("Rear item: %d\n", getRear(queue));

    printf("Queue: ");
    displayQueue(queue);

    deQueue(queue);
    deQueue(queue);

    printf("After deQueue, Front item: %d\n", getFront(queue));
    printf("Queue: ");
    displayQueue(queue);

    return 0;
}
