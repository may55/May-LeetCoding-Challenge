# Flood Fill

An image is represented by a 2-D array of integers, each integer representing the pixel value of the image (from 0 to 65535).

Given a coordinate (sr, sc) representing the starting pixel (row and column) of the flood fill, and a pixel value newColor, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image. 


### Example 1:

> Input: 
> image = [[1,1,1],[1,1,0],[1,0,1]]
> sr = 1, sc = 1, newColor = 2
> Output: [[2,2,2],[2,2,0],[2,0,1]]


## Explanation

1. Simple run bfs from the source.


## Code:

```
vector<int> X = {1,-1,0,0};
vector<int> Y = {0,0,1,-1};

class Solution {
public:
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor) {
        int oldColor = image[sr][sc];
        
        queue<pair<int,int>> q;
        int n = image.size();
        int m = image[0].size();
        q.push({sr,sc});
        int visited[n][m];
        memset(visited,false,sizeof(visited));
        while(!q.empty()){
            auto top = q.front();q.pop();
            int x = top.first,y=top.second;
            visited[x][y] = true;
            image[x][y] = newColor;
            for(int i=0;i<4;i++){
                int x_i = x+X[i];
                int y_i = y+Y[i];
                if(x_i<n && x_i>=0 && y_i<m && y_i>=0 && image[x_i][y_i]==oldColor && !visited[x_i][y_i]){
                    q.push({x_i,y_i});
                }
            }
        }
        return image;
    }
};
```