# Sort Characters By Frequency


Given a string, sort it in decreasing order based on the frequency of characters.

### Example 1:

    Input:
    "tree"

    Output:
    "eert"

    Explanation:
    'e' appears twice while 'r' and 't' both appear once.
    So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.

### Example 2:

    Input:
    "cccaaa"

    Output:
    "cccaaa"

    Explanation:
    Both 'c' and 'a' appear three times, so "aaaccc" is also a valid answer.
    Note that "cacaca" is incorrect, as the same characters must be together.

### Example 3:

    Input:
    "Aabb"

    Output:
    "bbAa"

    Explanation:
    "bbaA" is also a valid answer, but "Aabb" is incorrect.
    Note that 'A' and 'a' are treated as two different characters.

## Explanation

1. Count frequency and sort with it.


## Code:

```
class Solution {
public:
    string frequencySort(string s) {
        vector<pair<int,int>> fre(256,{0,0});
        // for(int i=0;i<26;i++)
        //     fre[i].second = i;
        for(auto it: s){
            fre[it].first++;
            fre[it].second = it;
        }
        sort(fre.begin(),fre.end(),greater<pair<int,int>>());
        string ans;
        for(auto it: fre){
            while(it.first--)
                ans.push_back(it.second);
        }   
        return ans;
    }
};
```