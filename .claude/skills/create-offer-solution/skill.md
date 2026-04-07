---
name: create-offer-solution
description: 根据 LeetCode 链接自动创建《剑指 Offer》题解文件。需要传入题目链接。
---

# 创建剑指 Offer 题解 Skill

## 输入

- **必填**：LeetCode 题目链接（如 `https://leetcode.cn/problems/powx-n/`）
- **可选**：用户的解题代码（TypeScript/JavaScript）

## 执行流程

### 1. 解析链接并搜索确认题号

**重要**：LeetCode 题号与剑指 Offer 题号可能不同！

例如：
- `powx-n` 是 LeetCode 第 50 题，但对应**剑指 Offer 第 16 题**"数值的整数次方"
- 必须搜索确认实际对应关系

解析步骤：
1. 提取题目 slug（如 `powx-n`）
2. 搜索确认该 LeetCode 题目对应剑指 Offer 的第几题
3. 确定正确的题号和标题

### 2. 创建/更新题解文件

**文件命名格式**：`{序号}. {标题}.md`（如 `16. 数值的整数次方.md`）

**场景一：用户提供了解题代码**
```markdown
# [17. 打印从1到最大的 n 位数](LeetCode链接)

## 解法名称

```typescript
/**
 * @description 算法思路描述：解释核心原理和关键步骤
 *
 * 时间复杂度 O(n) 推导：
 * - ...
 *
 * 空间复杂度 O(1) 推导：
 * - ...
 */
function solution() {
    // 代码
}
```
```

**场景二：用户只提供了链接**
- 创建仅包含题目框架的文件：
```markdown
# [17. 打印从1到最大的 n 位数](LeetCode链接)

```

### 3. 更新侧边栏

自动调用 `algorithm-review` skill 确保侧边栏正确。

## 题目类型判断

| URL 特征 | 题目类型 | 存放目录 |
|----------|----------|----------|
| `lcof` | 剑指 Offer | `docs/剑指 offer/` |
| `lcp` | LCP | `docs/` |
| `lcr` | LCR | `docs/` |
| `面试题` 相关 | 面试题 | `docs/面试题/` |
| 其他 LeetCode 链接 | 需搜索确认对应题号 | `docs/剑指 offer/` |

## 剑指 Offer 文件命名参考

- 文件名格式：`{序号}. {标题}.md`（如 `17. 打印从1到最大的 n 位数.md`）
- 存放目录：`docs/剑指 offer/`
- **注意**：标题中的变量（如 `n`、`m` 等）周围应有空格环绕

## 注意事项

- LeetCode 题号 ≠ 剑指 Offer 题号，必须搜索确认
- 如果同一题存在多种解法，添加新的解法部分（保留原有解法）
- @description 必须包含：算法逻辑、时间复杂度（含推导）、空间复杂度（含推导）
- **用户只提供一个解法时，只创建该解法，不要自动添加其他解法**
