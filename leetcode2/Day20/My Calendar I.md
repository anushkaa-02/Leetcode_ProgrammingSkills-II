# My Calendar I
- ## Question:
>You are implementing a program to use as your calendar. We can add a new event if adding the event will not cause a double booking.
>
>A double booking happens when two events have some non-empty intersection (i.e., some moment is common to both events.).
>
>The event can be represented as a pair of integers start and end that represents a booking on the half-open interval [start, end), the range of real numbers x such >that start <= x < end.
>
>Implement the MyCalendar class:

- Example :

      Input
      ["MyCalendar", "book", "book", "book"]
      [[], [10, 20], [15, 25], [20, 30]]
      Output
      [null, true, false, true]
      
- ## Solution:
```cpp
class MyCalendar {
public:
   set<pair<int,int>> s;
    MyCalendar() {
        
    }
    
    bool book(int start, int end) {
        if(s.size()==0)
        {
            s.insert({start,end});  
            return true;
        }
        for(auto it:s)
        {
            if((start<=it.first and end>it.first) || (start>=it.first and start<it.second))
                return false;
        }
        s.insert({start,end});
        return true;;
    }
};
```

## Tags
`Binary Search`
