# Hysteria2 代理协议配置教程

> 高速抗封锁代理协议 | Hysteria2 暴力加速配置 | BBR 优化 | QUIC 协议翻墙

[![Stars](https://img.shields.io/github/stars/flclash-us/hysteria2-proxy-guide?style=flat)](https://github.com/flclash-us/hysteria2-proxy-guide)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

---

## 📋 目录

- [什么是 Hysteria2](#什么是-hysteria2)
- [特点与优势](#特点与优势)
- [服务端安装](#服务端安装)
- [客户端配置](#客户端配置)
- [BBR 加速优化](#bbr-加速优化)
- [常见问题](#常见问题)

---

## 🚀 什么是 Hysteria2

Hysteria2 是基于 **QUIC 协议** 的高速代理工具，由 Hysteria 团队开发。相比传统代理协议，Hysteria2 具有以下优势：

- **暴力加速** - 利用 QUIC 的拥塞控制，在丢包网络中仍能保持高速
- **抗封锁** - QUIC 协议特征与正常 HTTPS 流量相似，难以识别
- **低延迟** - 基于 UDP，连接建立更快
- **多路复用** - 单连接支持多路数据传输

---

## ✨ 特点与优势

| 特性 | Hysteria2 | VLESS | Trojan |
|------|:---------:|:-----:|:------:|
| 传输协议 | QUIC/UDP | TCP/TLS | TCP/TLS |
| 抗丢包 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| 速度 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| 抗封锁 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| 配置难度 | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ |

---

## 🖥️ 服务端安装

### 一键安装脚本

```bash
# 安装 Hysteria2
bash <(curl -fsSL https://get.hy2.sh/)

# 生成配置
hysteria server --init

# 编辑配置
nano /etc/hysteria/config.yaml
```

### 服务端配置

```yaml
# /etc/hysteria/config.yaml
listen: :443

tls:
  cert: /path/to/cert.pem
  key: /path/to/key.pem

auth:
  type: password
  password: your-strong-password

masquerade:
  type: proxy
  proxy:
    url: https://www.bing.com
    rewriteHost: true

bandwidth:
  up: 100 mbps
  down: 100 mbps
```

### 启动服务

```bash
# 使用 systemd
systemctl enable hysteria-server
systemctl start hysteria-server
systemctl status hysteria-server
```

---

## 📱 客户端配置

### Clash.Meta 配置

```yaml
proxies:
  - name: "Hysteria2"
    type: hysteria2
    server: your-server.com
    port: 443
    password: your-strong-password
    sni: your-server.com
    skip-cert-verify: false
```

### Hysteria2 官方客户端

```yaml
# config.yaml
server: your-server.com:443
auth: your-strong-password
tls:
  sni: your-server.com
  insecure: false

bandwidth:
  up: 50 mbps
  down: 100 mbps

socks5:
  listen: 127.0.0.1:1080

http:
  listen: 127.0.0.1:8080
```

启动客户端：
```bash
hysteria client -c config.yaml
```

---

## ⚡ BBR 加速优化

### 检查当前拥塞控制算法

```bash
sysctl net.ipv4.tcp_congestion_control
```

### 启用 BBR

```bash
# 编辑 sysctl 配置
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf

# 应用配置
sysctl -p

# 验证
sysctl net.ipv4.tcp_congestion_control
# 应显示: net.ipv4.tcp_congestion_control = bbr
```

### 内核要求

- Linux 内核 4.9+ （原生支持 BBR）
- 建议内核 5.6+ （支持 BBRv2）

---

## ❓ 常见问题

### Q: Hysteria2 与 Hysteria1 有什么区别？

**A:** 
- Hysteria2 是全新重写版本
- 协议不兼容
- 性能更好，配置更简单
- 推荐新用户使用 Hysteria2

### Q: 为什么我的速度没有提升？

**A:**
1. 检查 BBR 是否启用
2. 确认带宽设置是否合理
3. 检查服务器网络质量
4. 尝试调整 QUIC 参数

### Q: 支持哪些客户端？

**A:**
- Clash.Meta (推荐)
- Hysteria2 官方客户端
- Shadowrocket (iOS)
- v2rayN (Windows)

---

## 🔗 相关资源

| 资源 | 链接 |
|------|------|
| Clash for Windows | [clashforwindows.site](https://clashforwindows.site) |
| Clash 资源站 | [flclash.us](https://flclash.us) |
| Android 教程 | [clashmi.site](https://clashmi.site) |
| Hysteria2 官方 | [v2.hysteria.network](https://v2.hysteria.network) |

---

<p align="center">
  暴力加速，畅享极速网络 ⚡
</p>