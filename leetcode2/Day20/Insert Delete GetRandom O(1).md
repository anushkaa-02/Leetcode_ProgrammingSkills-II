# Insert Delete GetRandom O(1)
- ## Question:
>Implement the RandomizedSet class:
>
- RandomizedSet() Initializes the RandomizedSet object.
- bool insert(int val) Inserts an item val into the set if not present. Returns true if the item was not present, false otherwise.
- bool remove(int val) Removes an item val from the set if present. Returns true if the item was present, false otherwise.
- int getRandom() Returns a random element from the current set of elements (it's guaranteed that at least one element exists when this method is called). Each element    must have the same probability of being returned.
>You must implement the functions of the class such that each function works in average O(1) time complexity.


- Example :

      Input
      ["RandomizedSet", "insert", "remove", "insert", "getRandom", "remove", "insert", "getRandom"]
      [[], [1], [2], [2], [], [1], [2], []]
      Output
      [null, true, false, true, 2, true, false, 2]
      
- ## Solution:
```cpp
class RandomizedSet {
public:
    
    unordered_map<int,int>random;
    vector<int>to;
    RandomizedSet() {
        
    }
    
    bool insert(int val) {
         if(random.find(val)!=random.end())
        {
            return false;
        }
        
        to.push_back(val);
        random[val]=to.size()-1;
        return true;
    }
    
    bool remove(int val) {
          
        if(random.find(val)==random.end())
        {
            return false;
        }
        int last=to.back();
     to[random[val]]=to.back();
        to.pop_back();
        random[last]=random[val];
        random.erase(val);
        
        return true;
    }
    
    int getRandom() {
       int ran= rand()%to.size();
        return to[ran];
    }
};
```

## Tags
`Array` `Hash Table`

