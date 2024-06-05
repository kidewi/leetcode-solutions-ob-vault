```c++
```class Stack {
private:
    vector<int> stackArray;

public:
    Stack() {}

    void push(int record) {
        stackArray.push_back(record);
    }

    void pop() {
        if (!isEmpty()) {
            stackArray.pop_back();
        }
    }

    int peek() const {
        if (!isEmpty()) {
            return stackArray.back();
        } else {
            cerr << "Stack is empty." << endl;
            return 0;
        }
    }

    bool isEmpty() const {
        return stackArray.empty();
    }

    int total() const {
        int sum = 0;
        for (int num : stackArray) {
            sum += num;
        }
        return sum;
    }
};

