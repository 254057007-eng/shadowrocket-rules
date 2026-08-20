# Shadowrocket Rules

个人 Shadowrocket 的**规则、策略组与 DNS/General 配置**。节点订阅与节点凭据完全独立，由客户端自行维护；本仓库不含节点、订阅地址、Token、UUID 或账号信息。

## 导入地址

优先使用 jsDelivr：

```text
https://cdn.jsdelivr.net/gh/254057007-eng/shadowrocket-rules@main/shadowrocket.conf
```

Raw GitHub 备用：

```text
https://raw.githubusercontent.com/254057007-eng/shadowrocket-rules/main/shadowrocket.conf
```

在 Shadowrocket：**配置 → 右上角 + → 从 URL 下载**，粘贴地址、下载后选择“使用配置”。首页全局路由应设为“配置”。

## 更新与节点

- `shadowrocket.conf` 的 `update-url` 指向 jsDelivr；后续在客户端更新该远程配置即可同步规则。
- 节点订阅须在 Shadowrocket 中独立保留/更新。该规则文件没有 `[Proxy]` 节点段；策略组用动态正则筛选客户端已有节点。
- 更新后先检查：地区策略组是否有节点、`🚀 策略选择`/`🐟 漏网之鱼` 是否可用，再进行日常连接。

## 规则特点

- 国内直连、漏网代理优先；AI、视频/流媒体、Telegram、Google/GitHub 等独立分流。
- 保留 TikTok UA 前置，避免与抖音/字节共享域名产生错误命中。
- Emby Cloudflare 与直连线路精确分流。
- `💼 公司内容` 默认直连；在公司网络受拦时可手动切换到 `🌐 代理访问`。
- **不内置广告拦截**：未包含广告策略组、`REJECT` 规则或 AdvertisingLite 远程规则；广告由用户在 Shadowrocket 模块中独立维护。
- 依赖 Blackmatrix7 的业务分流远程规则集；GitHub Raw 在部分网络可能超时属于上游连通性问题。

## 独立维护路线

1. **Shadowrocket 规则**：本仓库。
2. **Clash Mi JS / Mihomo 规则**：独立仓库与独立验证，节点独立导入。

不得将节点订阅、账户凭据或个人密钥提交到任何规则仓库。

## 发布前静态验证

本次首次发布版本基于本地 V3 测试规则生成，仅新增 `update-url`：

- SHA-256：`ea769266ba40b4fa7fa508319d497357e081d8655ca59e29e35ab2fde67a96ed`
- 结构：`[General]`、`[Proxy Group]`、`[Rule]`
- 第三方远程规则依赖：20 条

发布不替代客户端实机验证。
