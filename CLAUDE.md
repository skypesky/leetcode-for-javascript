# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个基于 docsify 的 LeetCode 题解仓库，使用 JavaScript/TypeScript 编写题解。

## 常用命令

```bash
# 本地开发预览
npm run dev

# 部署到 GitHub Pages（自动通过 GitHub Actions）
```

## 目录结构

- `docs/` - 所有文档和题解文件
- `docs/_sidebar.md` - docsify 侧边栏导航配置
- `docs/index.html` - docsify 主页面配置
- `docs/剑指 offer/` - 剑指 Offer 系列题解
- `docs/面试题/` - 面试题系列题解
- `docs/template/` - 题解模板

## 题解文件格式

题解文件名格式：
- LeetCode: `{序号}. {标题}.md`（如 `1. 两数之和.md`）
- 剑指 Offer: `剑指 Offer {序号}. {标题}.md`
- 面试题: `面试题 {序号}. {标题}.md`

题解内容格式：
```markdown
# [题号. 标题](题目链接)

- 递归 / 迭代 / 哈希表 等算法标签

```typescript
/**
 * @description 算法思路描述：解释核心原理和关键步骤
 */
function solution() {
    // 代码实现
}
```
```

注意：代码块前需要使用 `/** @description ... */` 注释来描述算法思路，类似 7. 重建二叉树的格式。
## 侧边栏自动更新规则

每当 `.md` 题解文件（新增、重命名、移动或删除）发生变化时，**必须立即自动更新** `docs/_sidebar.md`。不再要求用户执行脚本，AI 应主动确保侧边栏的完整性和正确排序。

### 分类排序规则

1. **剑指 Offer**（放在最前面）
   - 剑指 offer（小写/无空格）按数字排序：3, 4, 5, 6, 7, 8, 27, 64
   - 剑指 Offer 带题号按数字排序：28, 32-II, 42, 47, 48, 50, 54, 55-I, 55-II, 57-II, 68-I, 68-II
   - 剑指 Offer II 按数字排序：052, 056, 059
2. **LeetCode 题解** - 按题号数值大小排序
3. **LCP / LCR / 面试题** - LCP/LCR 按数字排序，面试题按数字排序
4. **其他** - 如各大排序算法、template 等

### 标题格式

sidebar 中的链接标题必须参考对应题解文件第一行 `# [XX. 题目标题](链接)` 的内容。例如：
- 文件第一行是 `# [64. 求1+2+…+n](链接)` → 标题为 `[64. 求1+2+…+n]`
- 文件第一行是 `# [剑指 Offer 27. 二叉树的镜像](链接)` → 标题为 `[剑指 Offer 27. 二叉树的镜像]`

### 文件存放规则

- 所有题解文件统一存放在 `docs/` 目录下
- 剑指 Offer 题解统一存放在 `docs/剑指 offer/` 目录下

## GitHub Actions

- `deploy.yml` - 推送 to `main` 分支时自动部署到 GitHub Pages
- `lint-pull-request.yml` - PR 标题必须符合 Angular 提交规范
