
# [LCP 44. 开幕式焰火](https://leetcode-cn.com/problems/sZ59z6/)

- 递归 + 哈希

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

function numColor(root: TreeNode | null): number {
    return sum(root, new Set<number>());
};

function sum(
    root: TreeNode,
    sets: Set<number>,
): number {

    // 先访问根节点
    sets.add(root.val);

    // 先访问左节点
    root.left && sum(root.left, sets);

    // 再访问右节点
    root.right && sum(root.right, sets);

    return sets.size;
}
```
