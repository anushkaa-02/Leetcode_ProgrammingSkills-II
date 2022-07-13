# Repeated substring pattern
- ## Question:
>Given a string s, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.

- Example :

      Input: s = "abab"
      Output: true
      Explanation: It is the substring "ab" twice.
      
- ## Solution:
```cpp
class Solution {
public:
     bool repeatedSubstringPattern(string s) {
        string str=s+s;
        str.erase(str.begin());
        str.erase(str.size()-1);
        int pos=-1,c=0;
        for(int i=0;i<str.size();i++)
        {
            if(str[i]==s[0])
            {
                c++;
                pos=i;
                for(int j=1;j<s.size();j++)
                {
                    if(c==s.size())
                        return true;
                    if(str[i+j]==s[j])
                    {
                        c++;
                    }
                    else
                    {
                        c=0;
                        pos=-1;
                        break;
                    }
                }
                if(c==s.size())
                    return true;
            }
        }
        return false;
    }
};
```
## Tags
`String` `String Matching`
