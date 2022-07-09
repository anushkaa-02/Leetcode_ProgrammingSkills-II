# Implement strStr()
- ## Question:
>Given two strings `needle` and `haystack`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

- Clarification:
>What should we return when `needle` is an empty string? This is a great question to ask during an interview.
>
>For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().

- Example :

      Input: haystack = "hello", needle = "ll"
      Output: 2
      
      Input: haystack = "aaaaa", needle = "bba"
      Output: -1
      
- ## Solution:
```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        if ( needle.size() == 1 && haystack.size() == 1) 
        {
            return haystack == needle ? 0 : -1;
        }
        int left = 0;
        int n = haystack.size();
        while(left != n) {
            
            string s = haystack.substr(left, needle.size());
            if(s == needle) 
            {
                return left;
            }
            left++;  
        }
        return -1; 
    }
};
```

## Tags
`Two Pointers` `String`
