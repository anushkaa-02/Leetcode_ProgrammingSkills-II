# Smallest Range II
- ## Question:
>You are given an integer array nums and an integer k.
>
>For each index i where 0 <= i < nums.length, change nums[i] to be either nums[i] + k or nums[i] - k.
>
>The score of nums is the difference between the maximum and minimum elements in nums.
>
>Return the minimum score of nums after changing the values at each index.

- Example :

      Input: nums = [1], k = 0
      Output: 0
      Explanation: The score is max(nums) - min(nums) = 1 - 1 = 0.
      
- ## Solution:
```cpp
class Solution {
public:
    int smallestRangeII(vector<int>& nums, int k) {
        std::sort(nums.begin(), nums.end());
        for (int &num : nums) num -= k;
        
        const int firstNum = nums.front();
        const int lastNum = nums.back();
        int minScore = lastNum - firstNum;
        for (int i = 0; i < nums.size() - 1; i++) {
            nums[i] += 2 * k;
            const int minNum = std::min({nums[0], nums[i], nums[i + 1]});
            const int maxNum = std::max({nums[i], nums[i + 1], lastNum});
            minScore = std::min(minScore, maxNum - minNum);
        }
        return minScore;
    }
};
```

## Tags
`Array` `Sliding Window`

