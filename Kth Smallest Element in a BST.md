# Kth Smallest Element in a BST

Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.

Note:
You may assume k is always valid, 1 ≤ k ≤ BST's total elements.

### Example 1:

    Input: root = [3,1,4,null,2], k = 1
       3
      / \
     1   4
      \
       2
    Output: 1

### Example 2:

    Input: root = [5,3,6,2,4,null,null,1], k = 3
           5
          / \
         3   6
        / \
       2   4
      /
     1
    Output: 3

    Follow up:
    What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? How would you optimize the kthSmallest routine?


## Explanation

1. Check for the size of left node.
2. If k lies in left, pass it to there.
3. else pass it to right after adjusting k's value.


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
    int findSize(TreeNode *root){
        if(root==NULL) return 0;
        return 1+findSize(root->left)+findSize(root->right);
    }
    int kthSmallest(TreeNode* root, int k) {
        if(root==NULL) return -1;
        int left_size = findSize(root->left);
        cout << left_size << " " << root->val << "\n";
        if(left_size+1==k){
            return root->val;
        }
        else if(left_size+1<k){
            return kthSmallest(root->right,k-left_size-1);
        }
        return kthSmallest(root->left,k);
    }
};
```