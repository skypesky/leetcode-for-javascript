
# [剑指 Offer 42. 连续子数组的最大和](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

- 动态规划

```typescript
function maxSubArray(nums: number[]): number {

    let max: number = -100;
    const dp: number[] = new Array(nums.length);

    for (let i = 0; i < nums.length; ++i) {
        const last = dp[i - 1] || 0;
        if (last > 0) {
            dp[i] = last + nums[i];
        } else {
            dp[i] = nums[i];
        }
        max = Math.max(max, dp[i]);
    }

    return max;

}
```

- 动态规划(升级版)

```typescript
function maxSubArray(nums: number[]): number {

    let max: number = nums[0],
        sum: number = 0;

    for (let i = 0; i < nums.length; ++i) {
        sum = Math.max(sum, 0) + nums[i];
        max = Math.max(max, sum);
    }

    return max;

}
```
