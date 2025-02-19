# Cherry Studio Main 进程架构

## 0. 目录
src/main/

## 1. 概述

Main 进程是 Cherry Studio 的核心进程，负责管理应用程序的生命周期、系统资源、文件操作和进程间通信等底层功能。

## 2. 核心功能

1. **文件系统管理**
   - 多格式文件加载器
   - 文件读写操作
   - 文件监控和同步
   - 文件缓存管理

2. **数据库操作**
   - SQLite 数据库管理
   - 数据持久化
   - 数据备份和恢复

3. **IPC 通信**
   - 与渲染进程的消息传递
   - 事件处理和分发
   - 状态同步

4. **系统 API 集成**
   - 系统托盘
   - 快捷键管理
   - 窗口管理
   - 剪贴板监控

## 3. 目录结构

```
src/main/
├── config.ts           # 配置管理
├── constant.ts         # 常量定义
├── electron.d.ts       # Electron 类型定义
├── env.d.ts            # 环境变量类型定义
├── index.ts           # 主进程入口
├── ipc.ts             # IPC 通信管理
├── loader/            # 文件加载器
│   ├── draftsExportLoader.ts  # Drafts 导出文件加载器
│   ├── epubLoader.ts          # EPUB 文件加载器
│   ├── index.ts               # 加载器统一导出
│   └── odLoader.ts            # Office 文档加载器
├── services/          # 核心服务
│   ├── AppUpdater.ts         # 应用更新服务
│   ├── BackupManager.ts      # 备份管理服务
│   ├── CacheService.ts       # 缓存服务
│   ├── ClipboardMonitor.ts   # 剪贴板监控服务
│   ├── ConfigManager.ts      # 配置管理服务
│   ├── ExportService.ts      # 导出服务
│   ├── FileService.ts        # 文件服务
│   ├── FileStorage.ts        # 文件存储服务
│   ├── GeminiService.ts      # Gemini AI 服务
│   ├── KnowledgeService.ts   # 知识库服务
│   ├── ShortcutService.ts    # 快捷键服务
│   ├── TrayService.ts        # 系统托盘服务
│   ├── WebDav.ts            # WebDAV 服务
│   └── WindowService.ts      # 窗口管理服务
└── utils/             # 工具函数
    ├── aes.ts               # AES 加密工具
    ├── file.ts              # 文件操作工具
    ├── index.ts             # 工具函数导出
    ├── locales.ts           # 国际化工具
    ├── upgrade.ts           # 升级工具
    ├── windowUtil.ts        # 窗口工具
    └── zip.ts               # 压缩工具
```

## 4. 模块职责

### 4.1 配置管理

- **config.ts**: 应用全局配置管理
- **constant.ts**: 全局常量定义
- **ConfigManager**: 用户配置管理服务

### 4.2 文件加载系统

加载器模块支持多种文件格式的读取和解析：

- **draftsExportLoader**: Drafts 导出文件处理
- **epubLoader**: EPUB 电子书解析
- **odLoader**: Office 文档处理

### 4.3 核心服务

1. **文件管理服务**
   - FileService: 文件操作核心服务
   - FileStorage: 文件存储管理
   - BackupManager: 数据备份服务

2. **系统服务**
   - WindowService: 窗口管理
   - TrayService: 系统托盘
   - ShortcutService: 快捷键管理
   - ClipboardMonitor: 剪贴板监控

3. **功能服务**
   - KnowledgeService: 知识库管理
   - GeminiService: AI 服务集成
   - WebDav: WebDAV 同步服务
   - ExportService: 数据导出服务

4. **辅助服务**
   - CacheService: 缓存管理
   - AppUpdater: 应用更新

### 4.4 工具函数

- **aes.ts**: 数据加密解密
- **file.ts**: 文件操作辅助函数
- **locales.ts**: 国际化支持
- **upgrade.ts**: 版本升级工具
- **windowUtil.ts**: 窗口操作工具
- **zip.ts**: 文件压缩解压

## 5. 通信机制

### 5.1 IPC 通信

主进程通过 IPC 机制与渲染进程进行通信：

1. **消息类型**
   - 同步消息
   - 异步消息
   - 广播消息

2. **通信内容**
   - 文件操作请求
   - 配置更新
   - 状态同步
   - 系统事件

### 5.2 事件处理

- 系统事件监听
- 用户操作响应
- 错误处理机制
- 状态更新通知

## 6. 安全机制

1. **数据安全**
   - 配置文件加密
   - 敏感信息保护
   - 数据备份机制

2. **通信安全**
   - IPC 通信验证
   - WebDAV 安全传输
   - API 密钥管理

## 7. 性能优化

1. **资源管理**
   - 内存使用优化
   - 文件缓存策略
   - 进程资源控制

2. **响应优化**
   - 异步操作处理
   - 批量处理机制
   - 延迟加载策略