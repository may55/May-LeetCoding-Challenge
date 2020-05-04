#   Ransom Note

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note. 


### Note:

>You may assume that both strings contain only lowercase letters.

>canConstruct("a", "b") -> false
>canConstruct("aa", "ab") -> false
>canConstruct("aa", "aab") -> true
 


## Explanation

1. Easy, count the frequecy.
2. for every char frequency in ransomNote should be greater than magazine.


## Code:

```
class Solution {
public:
    bool canConstruct(string ransomNote, string magazine) {
        vector<int> fre1(26,0),fre2(26,0);
        for(auto it: ransomNote)
            fre1[it-'a']++;
        for(auto it: magazine)
            fre2[it-'a']++;
        for(int i=0;i<26;i++){
            if(fre1[i]>fre2[i])
                return false;
        }
        return true;
            
        
    }
};
```