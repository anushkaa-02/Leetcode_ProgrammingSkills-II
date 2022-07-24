# Seat Reservation Manager
- ## Question:
>Design a system that manages the reservation state of n seats that are numbered from 1 to n.
>
>Implement the SeatManager class:
  - SeatManager(int n) Initializes a SeatManager object that will manage n seats numbered from 1 to n. All seats are initially available.
  - int reserve() Fetches the smallest-numbered unreserved seat, reserves it, and returns its number.
  - void unreserve(int seatNumber) Unreserves the seat with the given seatNumber.


- Example :

      Input
      ["SeatManager", "reserve", "reserve", "unreserve", "reserve", "reserve", "reserve", "reserve", "unreserve"]
      [[5], [], [], [2], [], [], [], [], [5]]
      Output
      [null, 1, 2, null, 2, 3, 4, 5, null]
      
- ## Solution:
```cpp
class SeatManager {
public:
    priority_queue<int,vector<int>,greater<int>> pq;
    SeatManager(int n) {
        for(int i=1;i<=n;i++){
            pq.push(i);
        }
    }
    int reserve() {
        int k = pq.top();
        pq.pop();
        return k;
    }
    
    void unreserve(int seatNumber) {
        pq.push(seatNumber);
    }
};
```

## Tags
`Design` `Heap(Priority Queue)`
