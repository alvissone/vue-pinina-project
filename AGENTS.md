# AGENTS.md

Vue 3 + Vite + Pinia + Vue Router 项目，使用 Element Plus UI 组件库。

## 常用命令

| 任务 | 命令 |
|------|------|
| 启动开发服务器 | `pnpm dev` |
| 构建（类型检查 + 打包） | `pnpm build` |
| 仅类型检查 | `pnpm type-check` |
| 单元测试（监视模式） | `pnpm test:unit` |
| 代码检查（oxlint → eslint，顺序执行） | `pnpm lint` |
| 格式化代码 | `pnpm format` |

**构建会先执行类型检查**，通过 `npm-run-all2` 实现。`pnpm build-only` 可跳过类型检查直接打包。

## 代码风格

- **Prettier 配置**：无分号、单引号、每行最多 100 字符
- **缩进**：2 空格（所有文件类型）
- Lint 执行顺序：oxlint 先运行（自动修复模式），然后 eslint（自动修复模式）

## 路径别名

`@/` 映射到 `src/` 目录 — 在 vite 和 tsconfig 中均有配置。

## 自动导入

Element Plus 组件通过 `unplugin-vue-components` 自动导入 — 模板中无需手动导入 Element Plus 组件。

## 测试

- 测试文件位置：`src/**/__tests__/`
- 测试运行器：vitest，使用 jsdom 环境
- 排除 `e2e/**` 目录
- 使用 `@vue/test-utils` 进行组件测试

## 类型检查

使用 `vue-tsc`（而非 `tsc`）— TypeScript 原生无法处理 `.vue` 文件的类型信息。

## 项目结构

```
src/
  main.ts          # 应用入口，注册 Pinia 和路由
  App.vue          # 根组件
  router/index.ts  # 路由配置（首页、关于页）
  stores/          # Pinia 状态管理
  views/           # 页面组件
  components/      # 可复用组件
```
