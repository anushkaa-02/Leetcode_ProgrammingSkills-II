# Subarray Product Less Than K
- ## Question:
>Given an array of integers nums and an integer k, return the number of contiguous subarrays where the product of all the elements in the subarray is strictly less >than k.


- Example :

      Input: nums = [10,5,2,6], k = 100
      Output: 8
      Explanation: The 8 subarrays that have product less than 100 are:
      [10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]
      Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.


- ## Solution:
```cpp
class Solution {
	public:
		int numSubarrayProductLessThanK(vector<int>& nums, int k) 
		{
			int cnt=0;
			if(k<=1)
				return 0;
			int prod=1;
			int left=0;
			for(int right=0;right<nums.size();right++)
			{
				prod*=nums[right];
				while(prod>=k)
				{
					prod/=nums[left++];
				}
				cnt=cnt+(right-left+1);
			}
			return cnt;
		}
	};
  ```
  
  ## Tags
  
  `Array` `Sliding Window`
