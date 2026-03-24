
# [剑指 Offer 50. 第一个只出现一次的字符](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

```ts
function firstUniqChar(s: string): string {
    const map: { [key: string]: number } = Object.create(null);
    for (const key of s) {
        map[key] = (map[key] || 0) + 1;
    }
    for (const key in map) {
        if (map[key] === 1) {
            return key;
        }
    }
    return ' ';
};
```
