```c++
```class MinStack {

public:
    std::stack<std::pair<int, int>> minStack;
    MinStack() {}
    void push(int val) {
        int currentMin = minStack.empty() ? val : min(val, minStack.top().second);
        minStack.push({val, currentMin});
    }
    void pop() {
        minStack.pop();
    }
    int top() {
        return minStack.top().first;
    } 
    int getMin() {
        return minStack.top().second;
    }
};