
# [剑指 Offer 55 - II. 平衡二叉树](https://leetcode-cn.com/problems/ping-heng-er-cha-shu-lcof/)

- 递归(自顶向下) + 哈希表

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


function isBalanced(
    root: TreeNode | null,
    currentLevel: number = 1,
    map: Map<TreeNode, number> = new Map<TreeNode, number>(),
): boolean {

    if (!root) {
        return true;
    }
    if (!root.left && !root.right) {
        return true;
    }
    if (!root.left && root.right) {
        return getLevel(root.right, currentLevel + 1, map) - currentLevel <= 1 &&
            isBalanced(root.right, currentLevel + 1, map);
    }
    if (root.left && !root.right) {
        return getLevel(root.left, currentLevel + 1, map) - currentLevel <= 1 &&
            isBalanced(root.left, currentLevel + 1, map);
    }
    return Math.abs(getLevel(root.left, currentLevel + 1, map) -
        getLevel(root.right, currentLevel + 1, map)) <= 1 &&
        isBalanced(root.left, currentLevel + 1, map) &&
        isBalanced(root.right, currentLevel + 1, map);
};

function getLevel(
    root: TreeNode,
    currentLevel: number,
    map: Map<TreeNode, number>
): number {

    if (!root.left && !root.right) {
        map.set(root, currentLevel);
        return currentLevel;
    } else if (!root.left && root.right) {
        return getLevel(root.right, currentLevel + 1, map);
    } else if (root.left && !root.right) {
        return getLevel(root.left, currentLevel + 1, map);
    } else {
        return Math.max(
            getLevel(root.left, currentLevel + 1, map),
            getLevel(root.right, currentLevel + 1, map),
        );
    }

}
```

- 递归(自底向上)

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
function isBalanced(root: TreeNode | null): boolean {
    return height(root) >= 0;
};

/**
 *
 * @description 计算节点的高度
 * @param {(TreeNode | null)} root
 * @return {*}  {number} 返回值的取值范围: x >= -1
 */
function height(root: TreeNode | null): number {
    if (!root) { // 空节点直接返回0
        return 0;
    }

    const leftHeight = height(root.left), // 先计算左子树的高度
        rightHeight = height(root.right); // 接着计算右子树的高度

    if (
        leftHeight === -1 ||
        rightHeight === -1 ||
        Math.abs(leftHeight - rightHeight) > 1
    ) { // 左子树,右子树任意一个高度为-1,都表示不平衡.如果左右子树的高度相差大于1,也是不平衡的.
        return -1;
    }
    // 说明一直都是平衡的,此时返回的是树的高度
    return Math.max(leftHeight, rightHeight) + 1;
}
```
