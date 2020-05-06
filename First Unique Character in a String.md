#   First Unique Character in a String

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1. 


### Example:

>s = "leetcode"
>return 0.

>s = "loveleetcode",
>return 2.
 

 


## Explanation

1. Simply count the frequency
2. Now check the first character with frequency 1.


## Code:

```
class Solution {
public:
    int firstUniqChar(string s) {
        int fre[26];
        memset(fre,0,sizeof fre);
        for(auto it: s)
            fre[it-'a']++;
        for(auto it=s.begin();it!=s.end();it++){
            if(fre[*it-'a']==1)
                return it-s.begin(); 
        }
        return -1;
        
    }
};
```