```c++
```#define MAX 100 // Maximum Stack size

class Stack {
	int top;
public:
	int stackArray[MAX]; // Array to store stack elements
	Stack() {top = -1; }
	bool push(int x);
	int pop();
	int peek();
	bool isEmpty();
};

bool Stack::push(int x) {
	if (top >= (MAX - 1)) {
		cout << "Stack Overflow";
		return false;
	} else {
		stackArray[++top] = x;
		cout << x << " pushed onto stack\n";
		return true;
	}
}

int Stack::pop() {
	if (top < 0) {
		cout << "Stack Underflow";
		return 0;
	} else {
		int x = stackArray[top--];
		return x;
	}
}

bool Stack::isEmpty() {
	return (top < 0);
}

int Stack::total() const {
    int sum = 0;
    for (int num : stackArray) {
        sum += num;
    }
    return sum;
}