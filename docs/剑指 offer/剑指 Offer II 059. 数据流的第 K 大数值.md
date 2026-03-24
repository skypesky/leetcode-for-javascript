
# [剑指 Offer II 059. 数据流的第 K 大数值](https://leetcode-cn.com/problems/jBjn9C/)

- 插入排序

```typescript
class KthLargest {

    private k: number;
    private nums: number[];

    constructor(k: number, nums: number[]) {
        this.k = k;
        this.nums = nums.sort((a: number, b: number) => b - a);
    }

    add(val: number): number {

        let lastIndex = this.k;

        while (lastIndex >= 0 && (val > this.nums[lastIndex] || this.nums[lastIndex] === undefined)) {
            this.nums[lastIndex + 1] = this.nums[lastIndex];
            --lastIndex;
        }
        
        this.nums[lastIndex + 1] = val;

        return this.nums[this.k - 1];
    }
}

/**
 * Your KthLargest object will be instantiated and called as such:
 * var obj = new KthLargest(k, nums)
 * var param_1 = obj.add(val)
 */
```

```typescript
// TODO: 加入堆排序的解法
```
