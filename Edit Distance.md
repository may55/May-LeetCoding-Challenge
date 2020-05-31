# Edit Distance

Given two words word1 and word2, find the minimum number of operations required to convert word1 to word2.

You have the following 3 operations permitted on a word:

    Insert a character
    Delete a character
    Replace a character

### Example 1:

    Input: word1 = "horse", word2 = "ros"
    Output: 3
    Explanation: 
    horse -> rorse (replace 'h' with 'r')
    rorse -> rose (remove 'r')
    rose -> ros (remove 'e')

### Example 2:

    Input: word1 = "intention", word2 = "execution"
    Output: 5
    Explanation: 
    intention -> inention (remove 't')
    inention -> enention (replace 'i' with 'e')
    enention -> exention (replace 'n' with 'x')
    exention -> exection (replace 'n' with 'c')
    exection -> execution (insert 'u')



## Explanation

1. Simple Edit distance.

## Code:

```
class Solution {
    int find(string &s1, string &s2,vector<vector<int>> &dp, int i, int j){
        if(i<0 || j<0) return max(i,j)+1;
        if(dp[i][j]!=-1) return dp[i][j];
        if(s1[i]==s2[j])
            return dp[i][j] = find(s1,s2,dp,i-1,j-1);
        dp[i][j] = INT_MAX;
        dp[i][j] = min(dp[i][j],find(s1,s2,dp,i-1,j)+1);
        dp[i][j] = min(dp[i][j],find(s1,s2,dp,i,j-1)+1);
        dp[i][j] = min(dp[i][j],find(s1,s2,dp,i-1,j-1)+1);
        return dp[i][j];
    }
public:
    int minDistance(string word1, string word2) {
        int n = word1.size();
        int m = word2.size();
        vector<vector<int>> dp(n+1,vector<int>(m+1,-1));
        return find(word1,word2,dp,n-1,m-1);
    }
};
```