# Sing-Box 配置完全指南

Sing-Box 是新一代通用代理客户端，支持 VLESS、VMess、Trojan、Shadowsocks、Hysteria2、TUIC 等所有主流协议。

## 为什么选择 Sing-Box

- 全协议支持: 一个客户端搞定所有协议
- 高性能: Go 语言实现，效率高
- 灵活配置: JSON 配置文件，功能丰富
- 多平台: Windows/macOS/Linux/Android/iOS

## 安装

### Windows

从 [Sing-Box Releases](https://github.com/SagerNet/sing-box/releases) 下载。

### Android

下载 APK：Google Play 或 [GitHub](https://github.com/SagerNet/sing-box/releases)。

## 配置文件

```json
{
  "log": {"level": "info"},
  "inbounds": [
    {
      "type": "mixed",
      "listen": "127.0.0.1",
      "listen_port": 7890
    }
  ],
  "outbounds": [
    {
      "type": "vless",
      "tag": "proxy",
      "server": "your-server.com",
      "server_port": 443,
      "uuid": "your-uuid",
      "tls": {"enabled": true, "server_name": "your-server.com"}
    },
    {"type": "direct", "tag": "direct"}
  ]
}
```

## 支持的协议

| 协议 | Sing-Box | 说明 |
|------|----------|------|
| VLESS+Reality | Yes | 最强抗封锁 |
| Trojan | Yes | HTTPS 伪装 |
| Hysteria2 | Yes | QUIC 高性能 |
| TUIC | Yes | 最新协议 |

---

推荐工具：

- [Clash for Windows](https://clashforwindows.site/)
- [ClashMI](https://clashmi.site/)
- [FlClash](https://flclash.us/)
