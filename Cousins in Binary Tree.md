#   Cousins in Binary Tree

In a binary tree, the root node is at depth 0, and children of each depth k node are at depth k+1.

Two nodes of a binary tree are cousins if they have the same depth, but have different parents.

We are given the root of a binary tree with unique values, and the values x and y of two different nodes in the tree.

Return true if and only if the nodes corresponding to the values x and y are cousins.


### Example 1:

>Input: root = [1,2,3,4], x = 4, y = 3
>Output: false

### Example 2:

>Input: root = [1,2,3,null,4,null,5], x = 5, y = 4
>Output: true

### Example 3:

>Input: root = [1,2,3,null,4], x = 2, y = 3
>Output: false
 


## Explanation

1. Do a dfs and store the parent and height of both x and y.
2. Check for given condition of the question.


## Code:

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */

int h1,h2,p1,p2;
class Solution {
public:
    void dfs(TreeNode *root, int x, int y, int h, int par){
        if(root==NULL) return;
        if(x==root->val){
            h1 = h;
            p1 = par;
        }
        if(y==root->val){
            h2 = h;
            p2 = par;
        }
        dfs(root->left,x,y,h+1,root->val);
        dfs(root->right,x,y,h+1,root->val);
    }
    
    bool isCousins(TreeNode* root, int x, int y) {
        if(x==root->val){
            h1 = 0,p1=-1;
        }
        if(y==root->val){
            h2=0,p2=-1;
        }
        dfs(root,x,y,0,-1);
        if(p1!=p2 && h1==h2)
            return true;
        return false;
    }
};
```