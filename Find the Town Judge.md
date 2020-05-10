# Find the Town Judge


In a town, there are N people labelled from 1 to N.  There is a rumor that one of these people is secretly the town judge.

If the town judge exists, then:

    1. The town judge trusts nobody.
    2. Everybody (except for the town judge) trusts the town judge.
    3. There is exactly one person that satisfies properties 1 and 2.

You are given trust, an array of pairs trust[i] = [a, b] representing that the person labelled a trusts the person labelled b.

If the town judge exists and can be identified, return the label of the town judge.  Otherwise, return -1.


### Example 1:

> Input: N = 2, trust = [[1,2]]
> Output: 2

### Example 2:

> Input: N = 3, trust = [[1,3],[2,3]]
> Output: 3

### Example 3:

> Input: N = 3, trust = [[1,3],[2,3],[3,1]]
> Output: -1

### Example 4:

> Input: N = 3, trust = [[1,2],[2,3]]
> Output: -1

### Example 5:

> Input: N = 4, trust = [[1,3],[1,4],[2,3],[2,4],[4,3]]
> Output: 3


## Explanation

1. Simple celebirty problem.


## Code:

```
class Solution {
public:
    int findJudge(int N, vector<vector<int>>& trust) {
        set<int> ans;
        for(int i=1;i<=N;i++) 
            ans.insert(i);
        vector<int> count(N+1,0);
        for(auto it: trust){
            // cout << it[0] << " " << it[1] << "\n";
            if(ans.find(it[0])!=ans.end()){
                ans.erase(it[0]);
                // for(auto it: ans)
                //     cout << it << " ";
                // cout << "\n";
            }
            count[it[1]]++;
        }
        for(auto it: ans){
            // cout << it << "\n";
            if(count[it]==(N-1))
                return it;
        }
        return -1;
    }
};
```