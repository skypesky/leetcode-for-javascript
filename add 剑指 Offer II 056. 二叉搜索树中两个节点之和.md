
# [剑指 Offer II 056. 二叉搜索树中两个节点之和](https://leetcode-cn.com/problems/opLdQZ/)

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
 * @param {(TreeNode | null)} root
 * @param {number} k
 * @return {*}  {boolean}
 */
function findTarget(root: TreeNode | null, k: number): boolean {
    return find(root, k, new Set<number>());
};

function find(
    root: TreeNode | null,
    target: number,
    sets: Set<number>,
): boolean {

    if (root === null) {
        return false;
    }

    if (sets.has(target - root.val)) {
        return true;
    }
    sets.add(root.val);

    return find(root.left, target, sets)
        || find(root.right, target, sets);
}
```

- 迭代器

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
 * @see https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/yield
 * @param {(TreeNode | null)} root
 * @param {number} k
 * @return {*}  {boolean}
 */
function findTarget(root: TreeNode | null, k: number): boolean {

    if (!root) {
        return false;
    }

    let left$ = inOrder(root),
        right$ = inOrderReverse(root),
        left = left$.next(),
        right = right$.next();

    while (left.value < right.value) {
        const sum = left.value + right.value;
        if (sum === k) {
            return true;
        } else if (sum > k) {
            right = right$.next();
        } else {
            left = left$.next();
        }
    }

    return false;
};

function* inOrder(root: TreeNode | null) {
    root.left && (yield* inOrder(root.left));
    yield root.val;
    root.right && (yield* inOrder(root.right));
}

function* inOrderReverse(root: TreeNode | null) {
    root.right && (yield* inOrderReverse(root.right));
    yield root.val;
    root.left && (yield* inOrderReverse(root.left));
}
```
