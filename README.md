# EasyConnect VPN GUI Launcher

深信服 EasyConnect VPN 的 Docker + GUI 启动器

## 功能

- Zenity 弹窗交互：输入服务器地址、用户名、密码
- 自动在 Docker 中运行 EasyConnect CLI
- 连接后提供 socks5 (1080) 和 HTTP (8888) 代理
- 已连接状态下可查看状态、复制代理地址、查看日志、断开连接

## 安装

```bash
# 从 deb 包安装
sudo dpkg -i ec-connect_1.0.0_amd64.deb

# 如有依赖问题
sudo apt install -f
```

## 使用

1. 应用菜单搜索 "EasyConnect VPN" 点击启动
2. 或终端运行: `ec-connect`

## 前置依赖

- Docker (docker-ce 或 docker.io)
- Zenity (弹窗交互)
- xclip 或 xsel (可选，用于复制代理地址)

## 项目结构

```
ec-connect/
├── src/
│   └── ec-connect       # 主程序脚本
├── debian/
│   ├── DEBIAN/
│   │   ├── control       # deb 包元信息
│   │   ├── postinst      # 安装后脚本
│   │   └── prerm         # 卸载前脚本
│   └── usr/
│       ├── bin/
│       │   └── ec-connect
│       └── share/
│           └── applications/
│               └── ec-connect.desktop
└── ec-connect_*.deb      # 构建产物
```

## 构建 deb 包

```bash
dpkg-deb --root-owner-group --build debian ec-connect_1.0.0_amd64.deb
```

## 技术栈

- Docker + hagb/docker-easyconnect:cli
- Zenity GUI 弹窗
- Bash 脚本

## License

WTFPL
