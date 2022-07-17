# Rotate Image
- ## Question:
>You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).
>
>You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

- Example :

      Input: matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
      Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
      
- ## Solution:
```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        vector<vector<int>> dup = matrix;
        int n = matrix.size();
        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                matrix[i][j] = dup[n-j-1][i];
            }
        }
    }
};
```

## Tags
`Array` `Math` `Matrix`
