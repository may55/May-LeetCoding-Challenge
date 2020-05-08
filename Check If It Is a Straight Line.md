# Check If It Is a Straight Line

You are given an array coordinates, coordinates[i] = [x, y], where [x, y] represents the coordinate of a point. Check if these points make a straight line in the XY plane.



### Example 1:

>Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
>Output: true

### Example 2:

>Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
>Output: false


## Explanation

1. Find the initial slope and then all the slopes and compare to it.


## Code:

```
class Solution {
public:
    bool checkStraightLine(vector<vector<int>>& arr) {
        double slope = (arr[1][1]-arr[0][1]);
        slope /= (double)((arr[1][0]-arr[0][0]));
        // double val = 1/0;
        
        for(int i=2;i<arr.size();i++){
            double slope2 = (arr[i][1]-arr[i-1][1]);
            slope2 /= (double)((arr[i][0]-arr[i-1][0]));
            if( slope!=slope2)
                return false;
        }
        return true;
        
    }
};
```