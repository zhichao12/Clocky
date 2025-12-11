# 签到助手 (Check-in Assistant)

轻量级 Chrome 扩展，帮你管理需要定期访问/签到的网站，支持提醒、标记状态与快捷跳转。

## 快速开始

### 环境要求
- Node.js 18+
- npm

### 安装与启动
```bash
npm install
npm run dev
```
`npm run dev` 会启动 Vite 开发服务器并构建到 `dist`，用于在 Chrome 的“加载已解压的扩展程序”中调试。

### 生产构建
```bash
npm run build
```
输出在 `dist`，直接用于打包/上架。

### 在 Chrome 加载
1. 打开 `chrome://extensions/`，开启“开发者模式”
2. 点击“加载已解压的扩展程序”，选择 `dist` 目录
3. 需要时点击扩展卡片的刷新按钮同步最新代码

## 项目结构
```
src/
  background/     # Service Worker
  popup/          # 弹窗 React 应用
  options/        # 设置页 React 应用
  content/        # 内容脚本
  shared/         # 公共类型与工具
  lib/            # 存储与业务逻辑
  styles/         # 全局样式
  __tests__/      # 测试
  manifest.ts     # MV3 清单入口
public/           # 静态资源与图标
docs/             # 规格与说明
dist/             # 构建输出（忽略提交）
```

## 常用脚本
| 命令 | 说明 |
| --- | --- |
| `npm run dev` | 开发模式，HMR |
| `npm run build` | 生产构建 |
| `npm run preview` | 本地预览生产包 |
| `npm run lint` / `lint:fix` | ESLint 检查/修复 |
| `npm run format` / `format:check` | Prettier 格式化/校验 |
| `npm run typecheck` | TypeScript 类型检查 |
| `npm run test` / `test:watch` | Vitest 单测/监听 |

## 技术栈
- React 18 + TypeScript + Vite（@crxjs/vite-plugin）
- Tailwind CSS
- Zustand 状态管理
- Vitest + jsdom 测试
- ESLint + Prettier 规范

## 功能概览
- 添加/管理待签到网站，自动提取 favicon/hostname
- 标记“已访问”“已签到”，支持一键重置今日状态
- 扩展角标显示待签到数量
- 定时提醒（Chrome Alarms + Notifications），可稍后提醒
- 自动检测访问（内容脚本）并提示标记
- 主题切换（浅色/深色/跟随系统）

## 开发者提示
- Node 版本≥18，避免提交 `dist` 与临时文件
- 修改 `manifest.ts` 权限时遵循最小权限原则
- 提交前至少运行 `npm run lint && npm run test`

## 贡献
欢迎提交 Issue/PR。推荐使用类似 Conventional Commits 的提交信息（如 `feat: ...`、`fix: ...`），PR 请说明改动内容、动机与测试结果。 ***!
