# Permutation in String

Given two strings s1 and s2, write a function to return true if s2 contains the permutation of s1. In other words, one of the first string's permutations is the substring of the second string.

 

### Example 1:

    Input: s1 = "ab" s2 = "eidbaooo"
    Output: True
    Explanation: s2 contains one permutation of s1 ("ba").

### Example 2:

    Input:s1= "ab" s2 = "eidboaoo"
    Output: False



## Explanation

1. Simple check for the anagram.


## Code:

```
class Solution {
public:
    bool checkInclusion(string p, string s) {
        if(s.size()<p.size()) return false;;
        int fre[26];
        memset(fre,0,sizeof fre);
        for(auto it: p)
            fre[it-'a']++;
        int k = p.size();
        int i=0;
        int fre2[26];
        memset(fre2,0,sizeof fre2);
        for(int i=0;i<k-1;i++){
            fre2[s[i]-'a']++;
        }
        vector<int> ans;
        for(int i=k-1;i<s.size();i++){
            fre2[s[i]-'a']++;
            bool flag = true;
            for(int j=0;j<26;j++){
                if(fre[j]!=fre2[j]){
                    flag = false;
                    break;
                }       
            }
            if(flag)
                ans.push_back(i-(k-1));
            fre2[s[i-(k-1)]-'a']--;
        }
        return ans.size();
    }
};
```