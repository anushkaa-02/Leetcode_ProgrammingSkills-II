#  Next Greater Element III
- ## Question:
>Given a positive integer n, find the smallest integer which has exactly the same digits existing in the integer n and is greater in value than n. If no such positive >integer exists, return -1.
>
>Note that the returned integer should fit in 32-bit integer, if there is a valid answer but it does not fit in 32-bit integer, return -1.

- Example :

      Input: n = 21
      Output: -1
      
- ## Solution:
```cpp
class Solution {
public:
    int nextGreaterElement(int num) {
        string s=to_string(num);
        int i,j,n=s.size();
        for(i=n-1;i>0;i--)
        {
            if(s[i]>s[i-1])
                break;
        }
        if(i==0)
        {
            return -1;
        }
        for(j=n-1;j>=i;j--)
        {
            if(s[j]>s[i-1])
            {
                swap(s[j],s[i-1]);
                break;
            }
        }
        sort(s.begin()+i,s.end());
        long long int ans=0;
        for(i=0;i<n;i++)
        {
            int x=s[i]-'0';
            ans=ans*10+x;
        }
        if(ans>INT_MAX)
            return -1;
        return ans;
    }
};
```

## Tags

`Math` `Two Pointers` `String`
