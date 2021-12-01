
# [剑指 Offer 28. 对称的二叉树](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)

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

function isSymmetric(root: TreeNode | null): boolean {
    return is(root?.left, root?.right);
};

function is(
    leftRoot: TreeNode | null,
    rightRoot: TreeNode | null,
): boolean {

    if (!leftRoot || !rightRoot) {
        return !leftRoot && !rightRoot;
    }

    if (leftRoot.val !== rightRoot.val) {
        return false;
    }

    return is(leftRoot.left, rightRoot.right)
        && is(leftRoot.right, rightRoot.left);
}
```
