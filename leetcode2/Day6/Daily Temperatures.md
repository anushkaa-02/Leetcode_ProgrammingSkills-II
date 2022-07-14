# Daily Temperatures
- ## Question:
> Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after >the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead

- Example :

      Input: temperatures = [73,74,75,71,69,72,76,73]
      Output: [1,1,4,2,1,1,0,0]
      
- ## Solution:
```cpp
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& tmp) {
        int n=tmp.size();
        vector<int>ans(n,0);
        stack<pair<int,int>>stk;
        stk.push({tmp[n-1],n-1});
        for(int i=n-2;i>=0;i--){
            while(!stk.empty() && stk.top().first<=tmp[i]){
                stk.pop();
            }
            if(!stk.empty())ans[i]=stk.top().second-i;
            stk.push({tmp[i],i});
        }
        return ans;
    }
};
```

## Tags
`Array` `Stack` `Monotonic Stack`
