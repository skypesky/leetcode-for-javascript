
# [剑指 Offer 48. 最长不含重复字符的子字符串](https://leetcode-cn.com/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/)

- 滑动窗口 + 哈希表

```ts
/**
 *
 * @complex T(n)/S(1) => 字符串的数量是一个常数,所以空间复杂度也是一个常数
 * @param {string} s
 * @return {*}  {number}
 */
function lengthOfLongestSubstring(s: string): number {

    const sets: Set<string> = new Set<string>(),
        length: number = s.length;

    let leftIndex: number = 0,
        rightIndex: number = 0,
        maxLen: number = 0;

    while (rightIndex < length) {

        while (rightIndex < s.length && !sets.has(s[rightIndex])) {
            sets.add(s[rightIndex]);
            ++rightIndex;
        }
        
        maxLen = Math.max(maxLen, rightIndex - leftIndex);

        if (rightIndex === s.length) {
            return maxLen;
        }

        // adjust leftIndex
        while (leftIndex < rightIndex && s[leftIndex] != s[rightIndex]) {
            sets.delete(s[leftIndex]);
            ++leftIndex;
        }
        ++leftIndex;
        ++rightIndex;
    }

    return maxLen;
};
```

- 直接遍历 + 哈希表

```ts
/**
 *
 * @complex T(n)/S(1) => 字符串的数量是一个常数,所以空间复杂度也是一个常数
 * @param {string} s
 * @return {*}  {number}
 */
function lengthOfLongestSubstring(s: string): number {

    const map: Map<string, number> = new Map<string, number>();

    let leftIndex: number = -1,
        maxLen: number = 0;

    for (let i = 0; i < s.length; ++i) {
        leftIndex = map.has(s[i])
            ? Math.max(map.get(s[i]), leftIndex)
            : leftIndex;
        map.set(s[i], i);
        maxLen = Math.max(
            maxLen,
            i - leftIndex,
        );
    }

    return maxLen;
};
```
