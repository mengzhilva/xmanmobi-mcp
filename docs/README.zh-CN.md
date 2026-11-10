# Xmanmobi MCP 使用教程

Xmanmobi MCP 让 Codex 等兼容 MCP 的 AI 客户端读取您有权限查看的 Google Ads 和 Facebook Ads 数据，并完成广告表现分析。当前所有工具均为只读，不会创建、修改、暂停或删除广告。

## 使用前准备

您需要：

- 一个可正常登录的 Xmanmobi 账号。
- 账号已分配至少一个客户及其广告数据权限。
- 已安装支持远程 MCP 和 OAuth 的客户端。

## 在 Codex CLI 中连接

打开 Codex MCP 配置文件并添加：

```toml
[mcp_servers.xmanmobi]
url = "https://ai.xmanmobi.com/mcp"
auth = "oauth"
```

然后在安装了 Codex CLI 的终端执行：

```bash
codex mcp login xmanmobi
```

浏览器会自动打开 Xmanmobi 授权页。登录后确认只读权限并允许访问。不要把密码、Access Token、Refresh Token 或授权码发给 AI。

连接完成后可以执行：

```bash
codex mcp list
```

如果列表中能看到 `xmanmobi`，即可开始使用。

## 第一次测试

建议先发送：

```text
使用 Xmanmobi 列出我可以访问的客户。
```

确认客户后再发送：

```text
使用 Xmanmobi 分析最近 7 天 Google 广告表现，并列出需要关注的 Campaign。
```

当账号能访问多个客户时，请在提示词中写明客户名称。Xmanmobi 只会返回当前登录账号已分配的客户数据。

## 常用分析

```text
比较最近 7 天与此前 7 天的广告消耗、转化和 ROAS。
```

```text
分析最近 30 天的广告素材，列出表现最好和最差的素材，并说明判断依据。
```

```text
分析最近 30 天 Google 搜索词，标记高转化词和可能的否定关键词，但不要修改账户。
```

```text
检查广告数据质量，找出未绑定账户、同步延迟和缺失的转化价值。
```

更多提示词见 [examples.md](examples.md)。

## 常见问题

### 为什么没有数据？

先确认当前 Xmanmobi 用户已分配客户，并且客户已绑定广告账户。还应确认所选日期范围内已经同步报表。

### 为什么数据为 0？

零值可能是真实的零，也可能是报告尚未同步。可以让 Xmanmobi 执行数据质量检查，并查看数据更新时间。

### 能直接暂停或修改广告吗？

不能。公开 MCP 工具全部是只读工具。AI 可以给出分析建议，但不会执行广告账户写操作。

### 登录失败怎么办？

确认浏览器能访问 Xmanmobi 登录页，并重新执行 `codex mcp login xmanmobi`。仍然失败时请访问[支持页面](https://ai.xmanmobi.com/mcp-support.html)。
