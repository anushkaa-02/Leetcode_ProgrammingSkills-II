# Arithmetic Subarrays
- ## Question:
>A sequence of numbers is called arithmetic if it consists of at least two elements, and the difference between every two consecutive elements is the same. More >formally, a sequence s is arithmetic if and only if s[i+1] - s[i] == s[1] - s[0] for all valid i.

- Example :

      Input: nums = [4,6,5,9,3,7], l = [0,0,2], r = [2,3,5]
      Output: [true,false,true]
      Explanation:
      In the 0th query, the subarray is [4,6,5]. This can be rearranged as [6,5,4], which is an arithmetic sequence.
      In the 1st query, the subarray is [4,6,5,9]. This cannot be rearranged as an arithmetic sequence.
      In the 2nd query, the subarray is [5,9,3,7]. This can be rearranged as [3,5,7,9], which is an arithmetic sequence.
      
- ## Solution:
```cpp
class Solution {
public:
    
    bool findRes(vector<int> ex){
        sort(ex.begin(),ex.end());
        for(int i=0;i<ex.size()-1;i++){
            if(ex[i+1]-ex[i]!=ex[1]-ex[0]){
                return false;
            }
        }
        return true;
    }  
    vector<bool> checkArithmeticSubarrays(vector<int>& nums, vector<int>& l, vector<int>& r) {
        vector<bool> res;
        for(int i=0;i<l.size();i++){
            vector<int> ex;
            int x=l[i];
            while(x<=r[i]){
                ex.push_back(nums[x]);
                x++;
            }
            bool ans=findRes(ex);
            res.push_back(ans);
        }
        return res;
    }
};
```

## Tags
`Array` `Sorting`
