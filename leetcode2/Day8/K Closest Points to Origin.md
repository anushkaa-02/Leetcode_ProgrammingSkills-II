# K Closest Points to Origin
- ## Question:
>Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane and an integer k, return the k closest points to the origin `(0, 0)`.
>
>The distance between two points on the X-Y plane is the Euclidean distance `(i.e., √(x1 - x2)2 + (y1 - y2)2)`.

- Example :

        Input: points = [[1,3],[-2,2]], k = 1
        Output: [[-2,2]]
        Explanation:
        The distance between (1, 3) and the origin is sqrt(10).
        The distance between (-2, 2) and the origin is sqrt(8).
        Since sqrt(8) < sqrt(10), (-2, 2) is closer to the origin.
        We only want the closest k = 1 points from the origin, so the answer is just [[-2,2]].
        
- ## Solution:
```cpp
class Solution {
public:

    vector<vector<int>> kClosest(vector<vector<int>>& points, int k) {
        
        priority_queue<pair<int,vector<int>>>max_h;
        vector<vector<int>>ans;
        for(int i=0;i<points.size();i++)
        {
            int d=points[i][0]*points[i][0] + points[i][1]*points[i][1];
            max_h.push({d,points[i]});
            if(max_h.size()>k)max_h.pop();
        }
        while(max_h.size()!=0)
        {
            auto x=max_h.top();
            ans.push_back(x.second);
            max_h.pop();
        }
        return ans;
    }
};
```

## Tags
`Array` `Math` `Divide and Conquer`
