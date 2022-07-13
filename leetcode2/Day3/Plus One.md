# Plus One
- ## Question:
>You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most >significant to least significant in left-to-right order. The large integer does not contain any leading 0's.
>
>Increment the large integer by one and return the resulting array of digits.

- Example :

      Input: digits = [1,2,3]
      Output: [1,2,4]
      Explanation: The array represents the integer 123.
      Incrementing by one gives 123 + 1 = 124.
      Thus, the result should be [1,2,4].
   
- ## Solution:
```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int n = digits.size();
        
        while(--n >= 0){
            int dig = digits[n];
            dig++;
            digits[n] = dig;
            if (dig != 10) return digits;
            else digits[n] = 0;
        }
        
        digits[0] = 0;
        digits.insert(digits.begin(), 1);
        return digits;
    }
};
```

## Tags
`Array` `Math`
