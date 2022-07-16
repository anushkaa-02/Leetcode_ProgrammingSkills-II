# Determine Whether Matrix Can Be Obtained By Rotation
- ## Question:
>Given two n x n binary matrices mat and target, return true if it is possible to make mat equal to target by rotating mat in 90-degree increments, or false otherwise.

- Example :

      Input: mat = [[0,1],[1,0]], target = [[1,0],[0,1]]
      Output: true
      Explanation: We can rotate mat 90 degrees clockwise to make mat equal target.


- ## Solution:
```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& m) {
        int n=m.size();
        int i=0,j=n-1;
        for(int i=0;i<=n/2-1;i++){
            for(int j=i;j<n-i-1;j++){
                int temp=m[i][j];
                m[i][j]=m[n-1-j][i];
                m[n-1-j][i]=m[n-1-i][n-1-j];
                m[n-i-1][n-1-j]=m[j][n-i-1];
                m[j][n-i-1]=temp;
            }
        }
    }
    bool findRotation(vector<vector<int>>& mat, vector<vector<int>>& target) {   
        int n=mat.size(),m=target.size();
        if(m!=n){
            return false;
        }
        int rot=4;
        bool ans=false;
        while(rot--){
            ans=(mat==target);
            if(ans){
                return ans;
            }
            rotate(mat);
        }
        return ans;
    }
};
```

## Tags
`Array` `Matrix`
