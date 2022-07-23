# Range Sum Query 2D - Immutable
- ## Question:
>Given a 2D matrix matrix, handle multiple queries of the following type:
>
>Calculate the sum of the elements of matrix inside the rectangle defined by its upper left corner (row1, col1) and lower right corner (row2, col2).

- Example :

      Input
      ["NumMatrix", "sumRegion", "sumRegion", "sumRegion"]
      [[[[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]], [2, 1, 4, 3], [1, 1, 2, 2], [1, 2, 2, 4]]
      Output
      [null, 8, 11, 12]

      Explanation
      NumMatrix numMatrix = new NumMatrix([[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]);
      numMatrix.sumRegion(2, 1, 4, 3); // return 8 (i.e sum of the red rectangle)
      numMatrix.sumRegion(1, 1, 2, 2); // return 11 (i.e sum of the green rectangle)
      numMatrix.sumRegion(1, 2, 2, 4); // return 12 (i.e sum of the blue rectangle)
      
 - ## Solution:
```cpp
class NumMatrix {
public:
    vector<vector<int>> sum;
    NumMatrix(vector<vector<int>>& matrix) {
        int m = matrix.size(), n = matrix[0].size();
        sum = vector<vector<int>>(m + 1, vector<int>(n + 1)); 
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                sum[i][j] = sum[i - 1][j] + sum[i][j - 1] - sum[i - 1][j - 1] + matrix[i - 1][j - 1];
            }
        }
    }
    int sumRegion(int r1, int c1, int r2, int c2) {
        r1++; c1++; r2++; c2++; 
        return sum[r2][c2] - sum[r2][c1 - 1] - sum[r1 - 1][c2] + sum[r1 - 1][c1 - 1];
    }
};
```

# Tags
`Array` `Design` `Matrix`
