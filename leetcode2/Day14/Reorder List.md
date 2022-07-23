# Reorder List
- ## Question:
>You are given the head of a singly linked-list. The list can be represented as:

    L0 → L1 → … → Ln - 1 → Ln
    
>Reorder the list to be on the following form:

    L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …
    
- Example :

      Input: head = [1,2,3,4]
      Output: [1,4,2,3]
      
 - ## Solution:
```cpp
class Solution
{
public:
  void reorderList(ListNode* head)
  {
    //
    deque<ListNode*> deq;

    ListNode* curr = head->next;
    while (curr) {
      deq.push_back(curr);
      curr = curr->next;
    }

    bool fromBack = true;
    while (!deq.empty()) {
      ListNode* next = nullptr;
      if (fromBack) {
        next = deq.back();
        deq.pop_back();
      } else {
        next = deq.front();
        deq.pop_front();
      }
      head->next = next;
      head = head->next;

      fromBack = !fromBack;
    }

    head->next = nullptr;
  }
};
```

## Tags
`Linked List` `Two Pointers` `Stack`
