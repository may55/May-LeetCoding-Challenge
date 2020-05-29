# Counting Bits

Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

### Example 1:

    Input: 2
    Output: [0,1,1]

### Example 2:

    Input: 5
    Output: [0,1,1,2,1,2]



## Explanation

1. We can use DP here.
2. Basically number of bits in anynumber will be 1+number of bit of a number with second MSD of current


## Code:

```
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> ans(num+1,0);
        for(int i=1;i<=num;i++){
            ans[i] = ans[i&(i-1)]+1;
        }
        return ans;
    }
};
```