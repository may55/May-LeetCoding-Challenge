# Contiguous Array

Given a binary array, find the maximum length of a contiguous subarray with equal number of 0 and 1.

### Example 1:

    Input: [0,1]
    Output: 2
    Explanation: [0, 1] is the longest contiguous subarray with equal number of 0 and 1.

### Example 2:

    Input: [0,1,0]
    Output: 2
    Explanation: [0, 1] (or [1, 0]) is a longest contiguous subarray with equal number of 0 and 1.

Note: The length of the given binary array will not exceed 50,000. 


## Explanation

1. Replace 0 with -1 and find the array with sum zero.

## Code:

```
class Solution {
public:
    int findMaxLength(vector<int>& nums) {
        if(nums.size()==0) return 0;
        for(auto &it: nums)
            if(it==0)
                it=-1;
        map<int,int> mp;
        int ans =0;
        mp[nums[0]] = 1;
        mp[0] = 0;
        for(int i=1;i<nums.size();i++){
            nums[i] += nums[i-1];
            if(mp.count(nums[i]))
                ans = max(ans,i+1-mp[nums[i]]);
            else
                mp[nums[i]] = i+1;
        }
        return ans;
    }
};
```