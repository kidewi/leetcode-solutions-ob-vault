```c++
```#include <iostream>
using namespace std;

// A node structure for the linked list
struct Node {
    int data;
    Node* next;
};

// A class to represent a queue
class Queue {
    Node *front, *rear; // Pointers to the front and rear of the queue

public:
    Queue() : front(nullptr), rear(nullptr) {}

    // Function to add an element to the queue
    void enqueue(int value) {
        Node* newNode = new Node{value, nullptr};
        if (rear == nullptr) { // If queue is empty
            front = rear = newNode;
            return;
        }
        rear->next = newNode;
        rear = newNode;
    }

    // Function to remove an element from the queue
    void dequeue() {
        if (front == nullptr) // If queue is empty
            return;
        Node* temp = front;
        front = front->next;
        if (front == nullptr) // If queue becomes empty after dequeue
            rear = nullptr;
        delete temp;
    }

    // Function to get the front element of the queue
    int getFront() {
        if (front == nullptr)
            return -1;
        return front->data;
    }

    // Function to check if the queue is empty
    bool isEmpty() {
        return front == nullptr;
    }
};
