# v2Go

基于 Flutter 构建的跨平台代理客户端，由 [Xray-core](https://github.com/XTLS/Xray-core) 和 [sing-box](https://github.com/SagerNet/sing-box) 驱动。

<img width="884" height="639" alt="image" src="https://github.com/user-attachments/assets/ce58cbe6-233a-4f13-bcdd-ab539831e2a8" />

<img width="884" height="639" alt="image" src="https://github.com/user-attachments/assets/3e105c42-37f4-453f-9b5a-bd18187c36a7" />

<img width="884" height="639" alt="image" src="https://github.com/user-attachments/assets/9f6ef3c3-b372-4983-8c06-16e5d36d5fd5" />

## 功能特性

- **多种代理模式**：系统代理、TUN 模式或无代理
- **Xray-core 集成**：支持 VMess 及其他 Xray 协议
- **TUN 模式**：通过 sing-box 实现全流量路由
- **实时统计**：实时流量速度图表，上传/下载监控
- **延迟测试**：逐服务器延迟测量，支持自动刷新
- **IP 位置检测**：连接后显示当前出口 IP 及地理位置
- **服务器管理**：添加、编辑并在多个服务器配置间切换
- **自动连接**：启动时记忆并重连上次选择的服务器
- **路由规则**：可配置路由规则（代理 / 直连 / 拦截）
- **系统托盘**：最小化到托盘，快速连接/断开
- **Fluent UI**：使用 fluent_ui 实现 Windows 原生风格界面

## 支持平台

| 平台     | 状态 |
|----------|--------|
| Windows  | ✅ 已支持 |
| Linux    | ✅ 已支持 |
| macOS    | 🚧 计划中 |
| Android  | 🚧 计划中 |

## 快速开始

### 前置条件

- [Flutter SDK](https://docs.flutter.dev/get-started/install) >= 3.10
- Windows 10/11（完整功能支持）

### 构建

```bash
flutter pub get
flutter run -d windows
```

### 内置二进制文件

`bin/` 目录包含所需的运行时二进制文件：

- `xray.exe` — Xray-core 代理引擎
- `sing-box.exe` — 用于 TUN 模式的 sing-box
- `geoip.dat` / `geosite.dat` — 路由规则数据文件

## 项目架构

```
lib/
├── core/           # 数据库与配置模型
├── features/       # UI 页面（主页、服务器、路由、设置、日志）
├── managers/       # 业务逻辑（ConnectManager、LogManager 等）
├── models/         # 数据模型（V2RayConfig、SingboxConfig 等）
├── services/       # 系统代理、延迟测试、流量统计、IP 位置
├── utils/          # 配置生成器与工具函数
└── widgets/        # 可复用 UI 组件
```

## 配置说明

服务器配置存储在本地 SQLite 数据库（`v2ray_servers.db`）中。每次连接前，当前运行配置会写入 `config/config-running.json`。

## 许可证

MIT
