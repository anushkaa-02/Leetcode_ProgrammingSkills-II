# Design Circular Queue
- ## Question:
>Design your implementation of the circular queue. The circular queue is a linear data structure in which the operations are performed based on FIFO (First In First >Out) principle and the last position is connected back to the first position to make a circle. It is also called "Ring Buffer".
>
>One of the benefits of the circular queue is that we can make use of the spaces in front of the queue. In a normal queue, once the queue becomes full, we cannot >insert the next element even if there is a space in front of the queue. But using the circular queue, we can use the space to store new values.

- Example :

      Input
      ["MyCircularQueue", "enQueue", "enQueue", "enQueue", "enQueue", "Rear", "isFull", "deQueue", "enQueue", "Rear"]
      [[3], [1], [2], [3], [4], [], [], [], [4], []]
      Output
      [null, true, true, true, false, 3, true, true, true, 4]
      
- ## Solution:
```cpp
class MyCircularQueue {
    int *arr;
    int size;
    int front;
    int rear;
public:
    MyCircularQueue(int k) {
        size = k;
        arr = new int[size];
        front = -1;
        rear = -1;
    }
    
    bool enQueue(int value) {
        if((front == 0 && rear == size-1) ||(rear ==(front -1)%(size))){
            return false;
        }
        else if(front == -1){
            front = 0;
            rear = 0;
            arr[rear] = value;
        }
        else if(rear == size-1 && front!=0){
            rear = 0;
            arr[rear] = value;
        }
   
        else{
            rear++;
            arr[rear] = value;
        }
        return 1;
    }
    
    bool deQueue() {
        if(front == -1){
            return 0;
        }
        if(front == rear){
            arr[front] = -1;
            front = rear = -1;
        }
        else if(front == size-1){
            arr[front] = -1;
            front = 0;
        }
        else{
            arr[front] = -1;
            front++;
            
        }
        return 1;
    }
    
    int Front() {
        if(front == -1){
            return -1;
        }
        return arr[front];
    }
    
    int Rear() {
        if(rear == -1){
            return -1;
        }
        return arr[rear];
    }
    
    bool isEmpty() {
        if(front == -1){
            return 1;
        }
        return 0;
    }
    
    bool isFull() {
        if((front == 0 && rear == size-1) ||(rear ==(front -1)%(size-1))){
            return true;
        }
        return false;
    }
};
```
## Tags

`Array` `Queue`

