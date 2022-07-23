# Copy List with Random Pointer
- ## Question:
>A linked list of length n is given such that each node contains an additional random pointer, which could point to any node in the list, or null.
>
>Construct a deep copy of the list. The deep copy should consist of exactly n brand new nodes, where each new node has its value set to the value of its corresponding >original node. Both the next and random pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied >list represent the same list state. None of the pointers in the new list should point to nodes in the original list.
>
>For example, if there are two nodes X and Y in the original list, where X.random --> Y, then for the corresponding two nodes x and y in the copied list, x.random --> >y.
>
>Return the head of the copied linked list.

- Example :

      Input: head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
      Output: [[7,null],[13,0],[11,4],[10,2],[1,0]]
      
- ## Solution:
```cpp
class Solution {
public:
    Node* copyRandomList(Node* head) {
        
        Node* copied = new Node(0);
        Node* temp2 = copied;
        unordered_map<Node*, Node*> mp;
        
        Node* temp = head;
        
        while (temp)
        {
            Node* n = new Node(temp->val);
            n->random = temp->random;
         
            temp2->next = n;
            temp2 = temp2->next;
         
            mp[temp] = n;
        
            temp = temp->next;
        }
        temp2 = copied->next;
        while (temp2)
        {
            if (temp2->random)
                temp2->random = mp[temp2->random];
            temp2 = temp2->next;
        }
        
        return copied->next;
    }
};
```

## Tags
`Hash Table` `Linked list`
