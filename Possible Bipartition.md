#  Possible Bipartition

Given a set of N people (numbered 1, 2, ..., N), we would like to split everyone into two groups of any size.

Each person may dislike some other people, and they should not go into the same group. 

Formally, if dislikes[i] = [a, b], it means it is not allowed to put the people numbered a and b into the same group.

Return true if and only if it is possible to split everyone into two groups in this way.

 

### Example 1:

    Input: N = 4, dislikes = [[1,2],[1,3],[2,4]]
    Output: true
    Explanation: group1 [1,4], group2 [2,3]

### Example 2:

    Input: N = 3, dislikes = [[1,2],[1,3],[2,3]]
    Output: false

### Example 3:

    Input: N = 5, dislikes = [[1,2],[2,3],[3,4],[4,5],[1,5]]
    Output: false


## Explanation

1. Simple graph coloring.


## Code:

```
class Solution {
public:
    bool flag;
    void dfs(vector<vector<int>> &adj, int src, vector<int> &color,int curr){
        color[src] = curr;
        for(auto it: adj[src]){
            if(color[it]==-1){
                dfs(adj,it,color,1-curr);
            }
            else if(color[it]==color[src]){
                flag = false;
                return;
            }
        }
    }
    
    bool possibleBipartition(int N, vector<vector<int>>& dislikes) {
        vector<int> color(N+1,-1);
        vector<vector<int>> adj(N+1);
        flag = true;
        for(auto it: dislikes){
            adj[it[0]].push_back(it[1]);
            adj[it[1]].push_back(it[0]);
        }
        for(int i=1;i<=N;i++){
            if(color[i]==-1){
                dfs(adj,i,color,0);
            }
            if(!flag) return flag;
        }
        return flag;
    }
};
```