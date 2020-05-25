# Uncrossed Lines


We write the integers of A and B (in the order they are given) on two separate horizontal lines.

Now, we may draw connecting lines: a straight line connecting two numbers A[i] and B[j] such that:

    A[i] == B[j];
    The line we draw does not intersect any other connecting (non-horizontal) line.

Note that a connecting lines cannot intersect even at the endpoints: each number can only belong to one connecting line.

Return the maximum number of connecting lines we can draw in this way.

 

### Example 1:

    Input: A = [1,4,2], B = [1,2,4]
    Output: 2
    Explanation: We can draw 2 uncrossed lines as in the diagram.
    We cannot draw 3 uncrossed lines, because the line from A[1]=4 to B[2]=4 will intersect the line from A[2]=2 to B[1]=2.

### Example 2:

    Input: A = [2,5,1,2,5], B = [10,5,2,1,5,2]
    Output: 3

### Example 3:

    Input: A = [1,3,7,1,7,5], B = [1,9,2,5,1]
    Output: 2


## Explanation

1. Simple largest common subsequence, but I have applied memoised dp

## Code:

```
class Solution {
public:
    map<int,vector<int>> mpA,mpB;
    int findi(vector<int> &A, vector<int> &B, int a_i, int b_i, vector<vector<int>> &dp){
        int n = A.size();
        int m = B.size();
        if(a_i==n || b_i==m) return 0;
        if(dp[a_i][b_i]!=-1) return dp[a_i][b_i];
        if(mpB.count(A[a_i])==0) return dp[a_i][b_i] = findi(A,B,a_i+1,b_i,dp);
        
        int ans = findi(A,B,a_i+1,b_i,dp);
        
        for(auto it: mpB[A[a_i]]){
            if(it<b_i)
                continue;
            ans = max(ans,1+findi(A,B,a_i+1,it+1,dp));
        }
        return dp[a_i][b_i] = ans;
        
    }
        
    
    int maxUncrossedLines(vector<int>& A, vector<int>& B) {
        mpA.clear();
        mpB.clear();
        int n = A.size(), m = B.size();
        for(int i=0;i<A.size();i++){
            mpA[A[i]].push_back(i);
        }
        
        for(int i=0;i<B.size();i++){
            mpB[B[i]].push_back(i);
        }
        
        vector<vector<int>> dp(n,vector<int>(m,-1));
        
        return findi(A,B,0,0,dp);
    }
};
```