
# [剑指 Offer 47. 礼物的最大价值](https://leetcode-cn.com/problems/li-wu-de-zui-da-jie-zhi-lcof/)

- 动态规划

```typescript
function maxValue(grid: number[][]): number {

    if (!grid.length || !grid[0].length) {
        return 0;
    }

    const rows: number = grid.length,
        cols: number = grid[0].length;

    for (let row = 0; row < rows; ++row) {
        for (let col = 0; col < cols; ++col) {
            grid[row][col] = Math.max(
                grid[row][col] + (row ? grid[row - 1][col] : 0),
                grid[row][col] + (col ? grid[row][col - 1] : 0),
            );
        }
    }

    return grid[rows - 1][cols - 1];

};
```
