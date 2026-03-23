
# [剑指 Offer 57 - II. 和为s的连续正数序列](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

- 滑动窗口

```ts
/**
 *
 * @complex T(n)/S(1)
 * @param {number} target
 * @return {*}  {number[][]}
 */
function findContinuousSequence(target: number): number[][] {

    const results: number[][] = [];

    let left: number = 1,
        right: number = 1,
        current: number = 0,
        bound: number = (target + 1) >>> 1;

    while (right <= bound + 1) {

        while (right <= bound + 1 && current < target) {
            current += right;
            ++right;
        }

        current === target && results.push(build(left, right));

        current -= left;
        ++left;

    }

    return results;
};

function build(left: number, right: number): number[] {
    const results: number[] = [];
    while (left < right) {
        results.push(left++);
    }
    return results;
}
```

- 数学法(等差数列求和 + 一元二次方程)
```ts
// 选做,不要求
```
