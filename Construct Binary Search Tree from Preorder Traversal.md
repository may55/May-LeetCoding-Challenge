# Construct Binary Search Tree from Preorder Traversal


Return the root node of a binary search tree that matches the given preorder traversal.

(Recall that a binary search tree is a binary tree where for every node, any descendant of node.left has a value < node.val, and any descendant of node.right has a value > node.val.  Also recall that a preorder traversal displays the value of the node first, then traverses node.left, then traverses node.right.)

It's guaranteed that for the given test cases there is always possible to find a binary search tree with the given requirements.

### Example 1:

    Input: [8,5,1,7,10,12]
    Output: [8,5,10,1,7,null,12]




## Explanation

1. Simply find the ranges of left and right child and do the insertion.

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
class Solution {
public:
    TreeNode *make(vector<int> &arr,int l,int r){
        if(l>r) return NULL;
        TreeNode *root = new TreeNode(arr[l]);
        if(l==r) return root;
        int i;
        for(i=l+1;i<=r;i++){
            if(arr[i]>arr[l]){
                // idx = i;
                break;
            }
        }
        root->left = make(arr,l+1,i-1);
        root->right = make(arr,i,r);
        return root;
    }
    
    TreeNode* bstFromPreorder(vector<int>& preorder) {
        return make(preorder,0,preorder.size()-1);
    }
};
```