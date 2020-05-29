# Course Schedule

There are a total of numCourses courses you have to take, labeled from 0 to numCourses-1.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: [0,1]

Given the total number of courses and a list of prerequisite pairs, is it possible for you to finish all courses?

 

### Example 1:

    Input: numCourses = 2, prerequisites = [[1,0]]
    Output: true
    Explanation: There are a total of 2 courses to take. 
                 To take course 1 you should have finished course 0. So it is possible.

### Example 2:

    Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
    Output: false
    Explanation: There are a total of 2 courses to take. 
                 To take course 1 you should have finished course 0, and to take course 0 you should
                 also have finished course 1. So it is impossible.


## Explanation

1. Here I found the cycle using dfs. 
2. It can also be done by writing topological sort. 


## Code:

```
class Solution {    
private:
    bool dfs(int src,vector<int> &vis,vector<vector<int>> &adj){
        if(vis[src]==2)
            return true;
        vis[src] = 1;
        for(auto it: adj[src]){
            if(vis[it]==2) continue;
            if(vis[it]==1) return false;
            if(!dfs(it,vis,adj)) return false;
        }
        vis[src] = 2;
        return true;
    }
public:
    bool canFinish(int n, vector<vector<int>>& pair) {
        vector<vector<int>> adj(n);
        for(auto it: pair){
            adj[it[1]].push_back(it[0]);
        }
        vector<int> vis(n,0);
        for(int i=0;i<n;i++){
            if(!vis[i]){
                if(!dfs(i,vis,adj)) return false;
            }
        }
        return true;
        
    }
};
```