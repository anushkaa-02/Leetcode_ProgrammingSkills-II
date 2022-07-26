# Flatten Nested List Iterator
- ## Question:
>You are given a nested list of integers nestedList. Each element is either an integer or a list whose elements may also be integers or other lists. Implement an iterator to flatten it.

- Example :

      Input: nestedList = [1,[4,[6]]]
      Output: [1,4,6]
      Explanation: By calling next repeatedly until hasNext returns false, the order of elements returned by next should be: [1,4,6].
      
- ## Solution:
```cpp
class NestedIterator {
queue<int> data;

public:
    NestedIterator(vector<NestedInteger> &nestedList) {
        flatten(nestedList);
    }

    void flatten(vector<NestedInteger> &list) {
        for (NestedInteger el : list)
            if (el.isInteger()) data.push(el.getInteger());
            else flatten(el.getList());
    }

    int next() {
        int res = data.front(); data.pop();
        return res;
    }

    bool hasNext() { return data.size() > 0; }
};
```

## Tags
`Stack` `Tree` `DFS`
