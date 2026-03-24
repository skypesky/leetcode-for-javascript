
# [剑指 Offer 27. 二叉树的镜像](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/)

- 递归

```typescript
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *     val: number
 *     left: TreeNode | null
 *     right: TreeNode | null
 *     constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.left = (left===undefined ? null : left)
 *         this.right = (right===undefined ? null : right)
 *     }
 * }
 */

function mirrorTree(root: TreeNode | null): TreeNode | null {
    return mirror(root);
};

function mirror(root: TreeNode | null): TreeNode | null {
    if(!root) {
        return null;
    }

    [root.left, root.right] = [root.right, root.left];
    mirror(root.left);
    mirror(root.right);
    
    return root;
}
```
