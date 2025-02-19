# Cherry Studio Renderer 架构

## 0. 目录
src/renderer/

## 1. 概述

Renderer（渲染进程）是 Cherry Studio 的前端展示层，负责用户界面渲染、状态管理、事件处理和数据展示等核心功能。基于 React + TypeScript 技术栈实现。

## 2. 核心功能

1. **用户界面渲染**
   - 明暗主题支持
   - 透明窗口效果
   - Markdown 渲染
   - 代码高亮
   - 拖拽排序

2. **状态管理**
   - 全局状态
   - 主题配置
   - 用户设置
   - 数据缓存

3. **事件处理**
   - 用户交互
   - IPC 通信
   - 文件操作
   - 快捷键绑定

4. **数据展示**
   - 文件预览
   - 知识库内容
   - AI 对话
   - 搜索结果

## 3. 技术实现

### 3.1 核心技术栈

- React
- TypeScript
- Styled-components
- Electron IPC

### 3.2 状态管理

- Context API
- 自定义 Hooks
- 本地存储

### 3.3 UI 组件

- 布局组件
  - Box：基础容器
  - Stack：弹性布局
  - Container：页面容器

- 交互组件
  - 按钮
  - 输入框
  - 下拉菜单
  - 对话框

- 展示组件
  - Typography：文字排版
  - 图标
  - 列表
  - 卡片

## 4. 目录结构

```
src/renderer/
├── src/                # 源代码目录
│   ├── components/     # React 组件
│   ├── hooks/         # 自定义 Hooks
│   ├── pages/         # 页面组件
│   ├── context/       # React Context
│   ├── store/         # 状态管理
│   ├── services/      # 服务层
│   ├── utils/         # 工具函数
│   ├── types/         # TypeScript 类型
│   ├── assets/        # 静态资源
│   ├── i18n/          # 国际化
│   ├── config/        # 配置文件
│   ├── windows/       # 窗口管理
│   ├── queue/         # 任务队列
│   ├── providers/     # 全局 Provider
│   └── databases/     # 数据库操作
├── index.html         # 入口 HTML
└── env.d.ts           # 环境变量类型
```

## 5. 核心模块说明

### 5.1 组件系统

- **Layout**: 布局组件，提供基础的页面结构
- **UI**: 可复用的界面组件
- **Business**: 业务相关组件

### 5.2 状态管理

- **Context**: 全局状态管理
- **Store**: 持久化数据存储
- **Queue**: 任务队列管理

### 5.3 服务层

- **API**: 与主进程通信
- **Utils**: 工具函数集
- **Hooks**: 可复用的业务逻辑

### 5.4 国际化

- 多语言支持
- 文案管理
- 动态切换

## 6. 开发规范

### 6.1 组件开发

- 使用 TypeScript
- 遵循 React Hooks 规范
- 组件文档化
- 单元测试

### 6.2 样式管理

- Styled-components
- 主题系统
- 响应式设计
- CSS-in-JS

### 6.3 状态管理

- 合理使用 Context
- 避免状态提升
- 性能优化
- 状态持久化

## 7. 性能优化

- 组件懒加载
- 虚拟列表
- 缓存策略
- 按需加载
- 代码分割