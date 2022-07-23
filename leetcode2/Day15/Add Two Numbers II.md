# Add Two Numbers II
- ## Question:
>You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contains a single >digit. Add the two numbers and return the sum as a linked list.
>
>You may assume the two numbers do not contain any leading zero, except the number 0 itself.

- Example :

      Input: l1 = [7,2,4,3], l2 = [5,6,4]
      Output: [7,8,0,7]
      
- ## Solution:
```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    vector<int> v1, v2;
    
    for(auto node = l1; node; node = node->next) v1.push_back(node->val);
    for(auto node = l2; node; node = node->next) v2.push_back(node->val);
    
    int i = v1.size()-1, j = v2.size()-1;
    
    int c = 0, sum = 0;
    
    ListNode* head = nullptr, *temp = nullptr;

    while(i >= 0 or j >= 0 or c > 0){
        sum = c;
        
        int val1 = i >= 0 ? v1[i] : 0;
        int val2 = j >= 0 ? v2[j] : 0;
        
        sum += val1 + val2;
        
        c = sum / 10;
        
        temp = new ListNode(sum%10);
        temp->next = head;
        head = temp;
        
        i--; 
        j--;
    }        
    return head;
}
};
```

## Tags
`Linked List` `Math` `Stack`
