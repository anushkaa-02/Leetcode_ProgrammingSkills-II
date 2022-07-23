# Add Two Numbers
- ## Question:
>You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
>
>You may assume the two numbers do not contain any leading zero, except the number 0 itself.

- Example :

      Input: l1 = [2,4,3], l2 = [5,6,4]
      Output: [7,0,8]
      Explanation: 342 + 465 = 807.
      
- ## Solution:
```cpp
class Solution { 
    private:
     void insertAtTail(ListNode* &head, ListNode* &tail, int val) {
        
        ListNode* temp = new ListNode(val);
        if(head == NULL) {
            head = temp;
            tail = temp;
            return;
        }
        else
        {
            tail -> next = temp;
            tail = temp;
        }
    }
    
    ListNode* add(ListNode* l1, ListNode* l2) {
        int carry = 0;
        
        ListNode* ansHead = NULL;
        ListNode* ansTail = NULL;
        
        while(l1 != NULL || l2 != NULL || carry != 0) {
            
            int val1 = 0;
            if(l1 != NULL)
                val1 = l1 -> val;
                
            int val2 = 0;
            if(l2 !=NULL)
                val2 = l2 -> val;
            
            
            int sum = carry + val1 + val2;
            
            int digit = sum%10;
            
            insertAtTail(ansHead, ansTail, digit);
            
            carry = sum/10;
            if(l1 != NULL)
                l1 = l1 -> next;
            
            if(l2 != NULL)
                l2 = l2 -> next;
        }
        return ansHead;
    }
    
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
         ListNode* ans = add(l1, l2);
        
        return ans;
    }
};
```
## Tags

`Linked List` `Math` `Recursion`
