# Time Needed to Inform All Employees
- ## Question:
>A company has n employees with a unique ID for each employee from 0 to n - 1. The head of the company is the one with headID.
>
>Each employee has one direct manager given in the manager array where manager[i] is the direct manager of the i-th employee, manager[headID] = -1. Also, it is >guaranteed that the subordination relationships have a tree structure.
>
>The head of the company wants to inform all the company employees of an urgent piece of news. He will inform his direct subordinates, and they will inform their >subordinates, and so on until all employees know about the urgent news.
>
>The i-th employee needs informTime[i] minutes to inform all of his direct subordinates (i.e., After informTime[i] minutes, all his direct subordinates can start >spreading the news).
>
>Return the number of minutes needed to inform all the employees about the urgent news.

- Example :

      Input: n = 1, headID = 0, manager = [-1], informTime = [0]
      Output: 0
      Explanation: The head of the company is the only employee in the company.
      
- ## Solution:
```cpp
class Solution {
public:
    int dfs(vector<int>adj[],int headID,vector<int>& informTime){
        int mn = 0;
        for(int i:adj[headID]){
            mn = max(mn,dfs(adj,i,informTime));
        }
        return mn + informTime[headID];
    }
    int numOfMinutes(int n, int headID, vector<int>& manager, vector<int>& informTime) {
        vector<int>adj[n];
        for(int i = 0;i<n;i++){
            if(manager[i]!=-1){
                adj[manager[i]].push_back(i);
            }
        }
        return dfs(adj,headID,informTime);
    }
};
```

## Tags
`Tree` `DFS`
