# Design Linked List
- ## Question:
>Design your implementation of the linked list. You can choose to use a singly or doubly linked list.
>A node in a singly linked list should have two attributes: val and next. val is the value of the current node, and next is a pointer/reference to the next node.
>If you want to use the doubly linked list, you will need one more attribute prev to indicate the previous node in the linked list. Assume all nodes in the linked list >are 0-indexed. Implement the MyLinkedList class:

- MyLinkedList() Initializes the MyLinkedList object.
- int get(int index) Get the value of the indexth node in the linked list. If the index is invalid, return -1.
- void addAtHead(int val) Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
- void addAtTail(int val) Append a node of value val as the last element of the linked list.
- void addAtIndex(int index, int val) Add a node of value val before the indexth node in the linked list. If index equals the length of the linked list, the node will be appended to the end of the linked list. If index is greater than the length, the node will not be inserted.
- void deleteAtIndex(int index) Delete the indexth node in the linked list, if the index is valid.

- Example :

      Input
      ["MyLinkedList", "addAtHead", "addAtTail", "addAtIndex", "get", "deleteAtIndex", "get"]
      [[], [1], [3], [1, 2], [1], [1], [1]]
      Output
      [null, null, null, null, 2, null, 3]

- ## Solution:
```cpp
class MyLinkedList {
    struct Node{
        int val;
        Node *next=NULL;
        Node(int value){
            val=value;
            next=NULL;
        }
    };
   
    Node *head;
    int size=0;
    
public:
    MyLinkedList() {
        head=NULL;
        size=0;
    }
    int get(int index) {
      if(head==NULL)return -1;
    if(index<0||index>=size)return -1;
        Node *currNode=head;
        for (int i=0;i<index;i++){
            currNode=currNode->next;
        }
        return currNode->val;
    }
    
    void addAtHead(int val) {
        Node *newNode=new Node(val);
        
        if(head==NULL)head=newNode;
        newNode->next=head;
        head=newNode;
        size++;
    }
    
    void addAtTail(int val) {
        Node *newNode=new Node(val);
        Node *currNode=head;
        if(head==NULL)head=newNode;
      
        else{
        for(int i=0;i<size-1;i++){
            currNode=currNode->next;
            
        }
        currNode->next=newNode;
        
        }
        
        size++;
    }
    
    void addAtIndex(int index, int val) {
               Node *newNode=new Node(val);
        Node *currNode=head;
        if(head==NULL)head=newNode;
        if(index<0||index>size)return;
        else if(index==0){
            newNode->next=head;head=newNode;
        }
        else{
        for(int i=0;i<index-1;i++){
            currNode=currNode->next;
            
        }
        newNode->next=currNode->next;
        currNode->next=newNode;
        }
        size++; 
    }
    
    void deleteAtIndex(int index) {
        
        Node *delNode=head;
        Node *currNode=head;
        if(head==NULL)return;
        if(index>=size||index<0)return;
        else if(index==0){
            
            head=head->next;
            delNode->next=NULL;
            delete delNode;    
        }
        else{
        for(int i=0;i<index-1;i++){
            currNode=currNode->next;
        }
        Node *nextNode=currNode->next->next;
      
        delete currNode->next;
            currNode->next=nextNode;
        }
        size--;
    }
};
```
## Tags
`Linked List` `Design`
