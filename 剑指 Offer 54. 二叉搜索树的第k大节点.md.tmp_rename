
# [剑指 Offer 54. 二叉搜索树的第k大节点](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

- 递归(右根左)

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


export type Store = {
    times: number;
    answer: number;
}

function kthLargest(root: TreeNode | null, k: number): number {
    const store: Store = {
        times: 0,
        answer: 0,
    }
    searchOrderK(root, k, store);
    return store.answer;
};

function searchOrderK(root: TreeNode, k: number, store: Store): void {

    if (root.right) {
        searchOrderK(root.right, k, store);
    }

    if (store.times >= k) {
        return;
    }

    store.answer = root.val;
    ++store.times;

    if (root.left) {
        searchOrderK(root.left, k, store);
    }
}
```
