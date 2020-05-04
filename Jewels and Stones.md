#   Jewels and Stones


You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".


### Example 1:

>Input: J = "aA", S = "aAAbbbb"
>Output: 3

### Example 2:

>Input: J = "z", S = "ZZ"
>Output: 0


 


## Explanation

1. For every character in J, add its frequency in S to the result.


## Code:

```
class Solution {
public:
    int numJewelsInStones(string J, string S) {
        map<char,int> mp;
        for(auto it: S)
            mp[it]++;
        int ans = 0;
        for(auto it: J){
            if(mp.count(it))
                ans += mp[it];
        }
        return ans;
        
    }
};
```