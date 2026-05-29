# 隐私保护与安全工具集 c0ag2y

[中文版] 保护你的网络隐私：广告拦截、DNS 加密、防追踪全攻略。

## 隐私保护金字塔

- 基础层：广告拦截 + DNS 防污染
- 进阶层：浏览器指纹防护 + 隐私搜索引擎
- 高级层：洋葱路由 + 端到端加密通讯

## 推荐工具清单

### 广告拦截
- AdGuard Home - DNS 层面拦截，开箱即用
- Pi-hole - 轻量级 DNS 广告拦截
- uBlock Origin - 浏览器级广告屏蔽

### 隐私浏览器
- Firefox + arkenfox - 高度可定制隐私配置
- Brave - 内置广告拦截和 Tor 窗口
- LibreWolf - Firefox 隐私增强版

### 密码管理
- Bitwarden - 开源、自托管、云同步
- KeePassXC - 本地存储、永不联网

## DNS 广告拦截配置

### AdGuard Home 安装
docker run --name adguardhome \
    --restart always \
    -v /opt/adguardhome/work:/opt/adguardhome/work \
    -v /opt/adguardhome/conf:/opt/adguardhome/conf \
    -p 53:53/tcp -p 53:53/udp \
    -p 3000:3000/tcp \
    -d adguard/adguardhome

## 隐私搜索引擎推荐

- DuckDuckGo: https://duckduckgo.com/ - 不追踪、隐私优先
- Startpage: https://startpage.com/ - Google 结果、匿名访问
- Searx: https://searx.be/ - 开源、可自托管

## 密码安全最佳实践

1. 每个网站使用独立密码，绝不重复
2. 使用密码管理器（推荐 Bitwarden）
3. 启用双因素认证（2FA）
4. 定期检查密码泄露

## 许可证

MIT License

推荐工具

- [Clash for Windows](https://clashforwindows.site/) - Windows 最流行的 Clash 图形化客户端
- [ClashMI](https://clashmi.site/) - 轻量级 Clash 客户端，支持多平台
- [FlClash](https://flclash.us/) - 现代代理工具，支持多种协议