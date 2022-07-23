# Rotate List
- ## Question:
>Given the head of a linked list, rotate the list to the right by k places.

- Example :

      Input: head = [1,2,3,4,5], k = 2
      Output: [4,5,1,2,3]
      
- ## Solution:
```cpp
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if (!head || !head->next || !k) { return head; }
        
        int len = 1;
        ListNode *curr = head;
        while (curr->next) { ++len; curr = curr->next; }
        k %= len;
        if (k == 0) { return head; }
        curr->next = head;
        
        curr = head;
        int cnt = len - k;
        while (--cnt) {
            curr = curr->next;
        }
        head = curr->next;
        curr->next = nullptr;
        return head;
    }
};
```

## Tags

`Linked List` `Two Pointers`
