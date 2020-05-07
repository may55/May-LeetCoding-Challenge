#   Majority Element

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

### Example 1:

>Input: [3,2,3]
>Output: 3

### Example 2:

>Input: [2,2,1,1,1,2,2]
>Output: 2
 


## Explanation

1. Use Moore Voting Algorithm
2. Take the idx and count variable initilize with 0 and 1 respectively.
3. No if element at arr[i]==arr[idx], increase count else decrease it.
4. If count become 0 then reinitialize the variable with i and 1.
5. This algo gives the correct answer only if there is a majority element in the array.

## Code:

```
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int idx = 0, count = 1;
        for(int i=1;i<nums.size();i++){
            if(nums[i]==nums[idx]){
                count++;
            }
            else
                count--;
            if(!count)
                count=1,idx=i;
        }
        return nums[idx];
    }
};
```
