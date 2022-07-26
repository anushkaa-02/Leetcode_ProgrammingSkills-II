# Min Stack
- ## Question:
>Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.
>
>Implement the MinStack class:

- MinStack() initializes the stack object.
- void push(int val) pushes the element val onto the stack.
- void pop() removes the element on the top of the stack.
- int top() gets the top element of the stack.
- int getMin() retrieves the minimum element in the stack.

- Example :

      Input
      ["MinStack","push","push","push","getMin","pop","top","getMin"]
      [[],[-2],[0],[-3],[],[],[],[]]

      Output
      [null,null,null,null,-3,null,0,-2]
      
- ## Solution:
```cpp
class MinStack {
 public:
  MinStack() = default;
  void push(int val);
  void pop();
  auto top() -> int;
  auto getMin() -> int;

 private:
  vector<pair<int, int>> _stack;
};

void MinStack::push(int val) {
  auto secondValue = _stack.empty() ? val : min(val, _stack.back().second);
  _stack.emplace_back(val, secondValue);
}

void MinStack::pop() { _stack.pop_back(); }

auto MinStack::top() -> int { return _stack.back().first; };

auto MinStack::getMin() -> int { return _stack.back().second; };
```

## Tags
`Stack` `Design`
