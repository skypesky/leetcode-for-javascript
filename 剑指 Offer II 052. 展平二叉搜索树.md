
# [剑指 Offer II 052. 展平二叉搜索树](https://leetcode-cn.com/problems/NYBBNL/)

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
 * @see https://leetcode-cn.com/problems/increasing-order-search-tree/
 * @param {(TreeNode | null)} root
 * @return {*}  {(TreeNode | null)}
 */
function increasingBST(root: TreeNode | null): TreeNode | null {

    let newRoot: TreeNode | null = null;

    (function dfs(root: TreeNode): void {

        // 先保存左, 右节点
        const { left, right } = root;

        // 先访问右节点
        right && dfs(right);

        // 访问父节点
        newRoot && (root.right = newRoot);
        newRoot = root;
        newRoot.left = null;

        // 最后访问右节点
        left && dfs(left);

    })(root);

    return newRoot;
};
```
