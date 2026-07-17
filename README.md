# Gitea for fnOS

使用 Gitea 官方二进制原生运行的飞牛 fnOS 第三方应用包，不依赖 Docker。

## 安全特性

- 内置 Gitea 版本：**1.22.0**（不受 CVE-2026-27771 影响）
- 默认关闭 `packages`（容器注册表）功能
- 默认关闭公开注册

## 数据库支持

- **SQLite（默认）**：零配置，推荐个人/小团队使用
- **PostgreSQL**：安装向导中填写外部数据库连接
- **MySQL / MariaDB**：安装向导中填写外部数据库连接

## 使用方法

1. Fork 本仓库
2. 修改 `.github/workflows/main.yml` 中的版本号
3. 在 Actions 中运行 `Build fpk` 工作流
4. 下载生成的 `gitea-1.22.0-1.amd64.fpk` 或 `gitea-1.22.0-1.arm64.fpk`
5. 在飞牛应用中心选择「本地安装」导入，或 SSH 执行：
   ```bash
   appcenter-cli install-fpk gitea-1.22.0-1.amd64.fpk
   ```
6. 安装向导中按需选择数据库类型

## 目录结构

```
gitea/
├── app/
│   └── ui/
│       ├── images/
│       │   ├── icon_64.png
│       │   └── icon_256.png
│       ├── config
│       └── index.html
├── cmd/
│   ├── main
│   ├── install_callback
│   ├── install_init
│   ├── upgrade_callback
│   ├── upgrade_init
│   ├── uninstall_callback
│   └── uninstall_init
├── config/
│   ├── privilege
│   └── resource
├── wizard/
│   ├── install
│   ├── uninstall
│   └── upgrade
├── manifest
├── ICON.PNG
├── ICON_256.PNG
└── LICENSE
```

## 升级

修改 `main.yml` 中的 `target_version` 和 `this_pack_manifest_version`，重新运行 Actions 即可。
