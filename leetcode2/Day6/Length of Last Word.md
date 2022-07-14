# Length of Last Word
- ## Question:
>Given a string s consisting of words and spaces, return the length of the last word in the string.
>
>A word is a maximal substring consisting of non-space characters only.


- Example :

      Input: s = "Hello World"
      Output: 5
      Explanation: The last word is "World" with length 5.

- ## Solution:
```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        
        string word = "";
        int currentLength = 0;
        for(int i = 0; i < s.length();i ++) {
            if(s[i] != ' ') {
                word += s[i];
            } 
            if (s[i] == ' ' or i == s.length() - 1) {
                if(word.length() != 0) {
                    currentLength = word.length();
                }
                word = "";
            }
        }
        return currentLength;
    }
};
```

## Tags
`String`
