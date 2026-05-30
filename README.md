# AdGuard Home 安装与配置指南

AdGuard Home 是一个全网广告跟踪拦截 DNS 服务器，支持自定义规则、家庭控制。

## 为什么需要 AdGuard Home

- 拦截全网广告（App/网站/视频）
- 保护隐私（阻止追踪器）
- 家长控制（屏蔽成人内容）
- 加速访问（DNS 缓存）
- 全设备覆盖（路由器级别）

## Docker 安装（推荐）

```bash
docker run --name adguardhome \
  -v /opt/adguardhome/work:/opt/adguardhome/work \
  -v /opt/adguardhome/conf:/opt/adguardhome/conf \
  -p 53:53/tcp -p 53:53/udp \
  -p 3000:3000/tcp \
  --restart always \
  adguard/adguardhome
```

## 初始配置

1. 访问 `http://your-ip:3000`
2. 设置管理员账号密码
3. 配置上游 DNS（推荐）：`https://dns.alidns.com/dns-query`
4. 设置过滤规则

## 推荐过滤规则

```
https://adguardteam.github.io/AdGuardSDNSFilter/Filters/filter.txt
https://raw.githubusercontent.com/privacy-protection-tools/anti-AD/master/anti-ad.txt
```

## 对接 Clash

AdGuard Home 可与 Clash 配合：AdGuard Home 作为 DNS 服务器，非广告流量转发至 Clash 代理。

## 常见问题

**DNS 冲突？** 确保 53 端口未被占用。

**内网无法访问？** 检查防火墙放行 53 和 3000 端口。

---

推荐工具：

- [Clash for Windows](https://clashforwindows.site/) - Clash 桌面客户端
- [ClashMI](https://clashmi.site/) - 移动端代理
- [FlClash](https://flclash.us/) - 全平台代理工具
