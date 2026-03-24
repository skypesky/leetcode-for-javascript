
# [剑指 Offer 68 - II. 二叉树的最近公共祖先](https://leetcode-cn.com/problems/er-cha-shu-de-zui-jin-gong-gong-zu-xian-lcof/)

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

/**
 *
 * @see https://leetcode-cn.com/problems/er-cha-shu-de-zui-jin-gong-gong-zu-xian-lcof/solution/mian-shi-ti-68-ii-er-cha-shu-de-zui-jin-gong-gon-7/512814
 * @param {(TreeNode | null)} root
 * @param {(TreeNode | null)} p
 * @param {(TreeNode | null)} q
 * @return {*}  {(TreeNode | null)}
 */
function lowestCommonAncestor(root: TreeNode | null, p: TreeNode | null, q: TreeNode | null): TreeNode | null {

    if (root === null || root === p || root === q) {
        return root;
    }

    const leftNode = lowestCommonAncestor(root.left, p, q),
        rightNode = lowestCommonAncestor(root.right, p, q);

    if (!leftNode || !rightNode) {
        return leftNode || rightNode;
    }

    return root;
};
```
