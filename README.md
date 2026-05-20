# EasyClick 项目热更新系统 - Skyaura 二开版

> 本项目是基于 **老鬼** 开源项目 [EasyClickupdateIecRust](https://gitee.com/Mr_laogui/EasyClickupdateIecRust) 的二次开发版本，专注于优化用户体验和修复已知问题。

***

## 🌟 项目简介

EasyClick 项目热更新系统是一个专为 EasyClick 自动化框架设计的 IEC 文件热更新管理平台，支持 Android/iOS 双平台项目的版本管理、自动更新和实时监控。

**二开改进亮点：**

| 改进项   | 描述                  |
| ----- | ------------------- |
| UI 重构 | 全新玻璃拟态设计风格，支持昼夜模式切换 |
| 性能优化  | 系统状态实时监控，资源使用率准确显示  |
| 交互优化  | 按钮操作自动刷新日志，实时反馈     |

***

## 🚀 功能特性

### 核心功能

- **📤 文件上传** - 支持 `.iec` 格式热更新包上传，自动计算 MD5 校验
- **📊 版本管理** - 版本列表管理、回滚、清理、删除等完整操作
- **🔍 实时日志** - 多级别日志筛选（INFO/ERROR/WARN/REQUEST/UPDATE）
- **💻 系统监控** - CPU、内存、磁盘实时状态监控

### 二开新增功能

- **🎨 玻璃拟态 UI** - 现代化视觉设计，支持明暗主题切换
- **🔄 自动刷新** - 操作后自动刷新日志，无需手动刷新
- **⚡ 响应式布局** - 适配不同屏幕尺寸
- **📱 移动端适配** - 支持移动设备访问

***

## 🛠️ 技术栈

| 分类   | 技术                        | 版本    |
| ---- | ------------------------- | ----- |
| 前端框架 | HTML5 + JavaScript (ES6+) | -     |
| 样式   | CSS3 (自定义属性、玻璃效果)         | -     |
| 图标   | SVG 内联图标                  | -     |
| 加密   | CryptoJS (MD5)            | 4.1.1 |
| 后端   | Rust (老鬼原项目)              | -     |

***

## 📁 项目结构

```
ecupdate-linux/
├── index.html          # 主控制面板（二开优化版）
├── upload.html         # 文件上传页面（原版本）
├── version-manager.html # 版本管理页面（原版本）
├── logs.html           # 日志监控页面（原版本）
├── static/
│   ├── css/            # 样式文件目录
│   ├── js/             # JavaScript 库
│   │   └── crypto-js.min.js
│   └── image/          # 图片资源
├── updateEC            # Rust 编译的后端服务
├── updateEC-service.sh # 服务管理脚本
└── config.toml         # 服务配置文件
```

***

## 🔧 快速开始

### 环境要求

- Linux 系统（推荐 Ubuntu 20.04+）
- 端口 3008 需对外开放

### 启动服务

```bash
# 启动服务
./updateEC-service.sh start

# 停止服务
./updateEC-service.sh stop

# 重启服务
./updateEC-service.sh restart

# 查看状态
./updateEC-service.sh status
```

### 访问地址

启动后访问 `http://localhost:3008` 即可进入管理控制台。

***

## 🌐 API 接口说明

### 系统状态

```
GET /api/get/system-stats
```

返回系统 CPU、内存、磁盘使用状态（小数格式 0.0-1.0）

### 日志获取

```
GET /api/get/log
```

返回实时系统日志列表

### 项目列表

```
GET /api/get/projects
```

返回所有项目名称列表

### 文件上传

```
POST /api/upload/file
Content-Type: multipart/form-data
```

上传 IEC 热更新包

***

## 📝 使用说明

### 上传热更新包

1. 填写项目名称（字母开头，3-50字符）
2. 输入版本号（如 `1` 或 `1.0.0`）
3. 选择项目类型（Android/iOS）
4. 上传 `.iec` 文件（自动计算 MD5）
5. 点击"上传并发布更新"

### 版本管理

1. 从下拉框选择项目
2. 查看版本列表（按时间倒序排列）
3. 支持下载、切换（回滚）、删除操作
4. 可清理旧版本（保留最新3个）

### 日志监控

1. 支持按级别筛选（全部/信息/错误/警告/请求/更新）
2. 支持关键词搜索
3. 可设置自动刷新间隔
4. 支持清空日志

***

## 🔄 与原项目差异

| 对比项    | 原版本             | 二开版本                |
| ------ | --------------- | ------------------- |
| UI 风格  | 传统卡片            | 玻璃拟态效果              |
| 主题     | 单一暗色            | 明暗主题切换              |
| CPU 显示 | 可能显示 0%         | 正确显示百分比             |
| 日志刷新   | 手动刷新            | 操作后自动刷新             |
| 布局     | 固定              | 响应式适配               |
| API 端点 | `/api/projects` | `/api/get/projects` |

***

## 📄 配置文件

`config.toml` 主要配置项：

```toml
[server]
port = 3008
workers = 8
upload_timeout = 300

[storage]
max_versions_per_project = 30
backup_count = 3

[logging]
level = "info"
max_size_mb = 100
```

***

## 🤝 贡献说明

本项目是基于老鬼开源项目的二次开发，欢迎提交 Issue 和 PR。

### 开发规范

- 代码遵循 ES6+ 标准
- 使用 `const`/`let` 而非 `var`
- 保持代码注释清晰
- 提交前确保功能完整

***

## 📜 许可证

本项目遵循 **MIT License**，与原项目保持一致。

***

## 🔗 相关链接

- **原项目**: [EasyClickupdateIecRust](https://gitee.com/Mr_laogui/EasyClickupdateIecRust)
- **EasyClick 官网**: [ieasyclick.com](https://ieasyclick.com)
- **老鬼编程学院**: [home.laoguicom.top](https://home.laoguicom.top)

***

**二创作者**: Skyaura\
**原作者**: 老鬼 <1156346325@qq.com>\
**版本**: v2.1 (二开优化版)\
**最后更新**: 2026-05-20
