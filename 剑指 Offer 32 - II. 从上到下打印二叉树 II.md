
# [剑指 Offer 32 - II. 从上到下打印二叉树 II](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

- 队列

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

function levelOrder(root: TreeNode | null): number[][] {

    if (!root) {
        return [];
    }

    const queue: TreeNode[] = [root],
        answer: number[][] = [];

    while (queue.length) {
        let { length: size } = queue;
        const answerOfLevel: number[] = [];

        while (size-- > 0) {
            const node = queue.shift();
            answerOfLevel.push(node.val);

            node.left && queue.push(node.left);
            node.right && queue.push(node.right);
        }

        answer.push(answerOfLevel);
    }

    return answer;
};
```
