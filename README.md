# AI Crypto Wallet 远程提示词库

本仓库存放 AI Crypto Wallet 的默认提示词库（安全限制、获取信息方式等）。
App 每次启动及每 12 小时会自动检查本仓库，若 `version` 高于本地已生效版本，
则替换并持久化生效，即使用户不升级 App，也能实时获得最新的安全限制与信息获取方式。

## 更新流程

如需发布新版提示词：

1. 修改 `prompts.json` 中的 `security_rules` 与 `info_gathering` 内容。
2. 将 `version` 字段 +1（必须大于当前线上版本才会被 App 采纳）。
3. 提交并推送到 `main` 分支。

App 会自动通过下同意更新（无需修改 App）：

```
https://raw.githubusercontent.com/{owner}/AI-Crypto-Wallet-Prompts/main/prompts.json
```

## 字段说明

- `version`：提示词版本号（整数），仅当线上版本高于本地已生效版本时才更新。
- `security_rules`：安全限制，作为优先级最高的安全规则注入系统提示词。
- `info_gathering`：获取信息方式的准则，指导 AI 如何实时获取行情与核验数据。

更新提示词时请保持字段结构不变。