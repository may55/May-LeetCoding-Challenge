# Find All Anagrams in a String

Given a string s and a non-empty string p, find all the start indices of p's anagrams in s.

Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100.

The order of output does not matter.

### Example 1:

    Input:
    s: "cbaebabacd" p: "abc"

    Output:
    [0, 6]

    Explanation:
    The substring with start index = 0 is "cba", which is an anagram of "abc".
    The substring with start index = 6 is "bac", which is an anagram of "abc".

### Example 2:

    Input:
    s: "abab" p: "ab"

    Output:
    [0, 1, 2]

    Explanation:
    The substring with start index = 0 is "ab", which is an anagram of "ab".
    The substring with start index = 1 is "ba", which is an anagram of "ab".
    The substring with start index = 2 is "ab", which is an anagram of "ab".


## Explanation

1. Simple check for every window of size of pattern.


## Code:

```
class Solution {
public:
    vector<int> findAnagrams(string s, string p) {
        if(s.size()<p.size()) return {};
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
        return ans;
    }
};
```