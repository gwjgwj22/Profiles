# Rules

个人代理分流规则仓库。以 Surge 格式手动维护，由 GitHub Actions 自动转换并同步到 Clash、Quantumult X、Loon。

---

## 目录结构

```
Rules/
├── Surge/
│   ├── RULE-SET/       ← 在这里编辑规则（唯一需要手动维护的地方）
│   ├── Profile.conf    ← Surge 完整配置文件
│   └── Module/         ← Surge 模块（去广告等）
├── Clash/
│   ├── RuleSet/        ← 自动生成，不要手动编辑
│   └── Sample.yaml     ← 自动生成的 Clash 完整配置
├── Quantumult/
│   └── X/Filter/       ← 自动生成，不要手动编辑
└── .github/
    ├── scripts/        ← 转换脚本
    └── workflows/      ← 自动运行的 GitHub Actions
```

> **记住一件事**：只在 `Surge/RULE-SET/` 和 `Surge/Profile.conf` 里改内容，其余文件由 Actions 自动生成。

---

## 规则订阅地址

将下面的地址填入对应 App 即可。

### Surge

| 规则 | 订阅地址 |
|------|----------|
| Apple | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Apple/Apple.list` |
| Apple CN | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Apple/Apple%20CN.list` |
| Apple News | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Apple/Apple%20News.list` |
| APNS | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Apple/APNS.list` |
| Google | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Google.list` |
| Telegram | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Telegram.list` |
| Twitter | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Twitter.list` |
| Microsoft | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Microsoft.list` |
| Dropbox | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/Dropbox.list` |
| PayPal | `https://raw.githubusercontent.com/egwj/Rules/master/Surge/RULE-SET/PayPal.list` |

### Clash

| 规则 | 订阅地址 |
|------|----------|
| Apple | `https://raw.githubusercontent.com/egwj/Rules/master/Clash/RuleSet/Apple.yaml` |
| Google | `https://raw.githubusercontent.com/egwj/Rules/master/Clash/RuleSet/Google.yaml` |
| Telegram | `https://raw.githubusercontent.com/egwj/Rules/master/Clash/RuleSet/Telegram.yaml` |
| Twitter | `https://raw.githubusercontent.com/egwj/Rules/master/Clash/RuleSet/Twitter.yaml` |
| Microsoft | `https://raw.githubusercontent.com/egwj/Rules/master/Clash/RuleSet/Microsoft.yaml` |
| Dropbox | `https://raw.githubusercontent.com/egwj/Rules/master/Clash/RuleSet/Dropbox.yaml` |
| PayPal | `https://raw.githubusercontent.com/egwj/Rules/master/Clash/RuleSet/PayPal.yaml` |

### Quantumult X

| 规则 | 订阅地址 |
|------|----------|
| Apple | `https://raw.githubusercontent.com/egwj/Rules/master/Quantumult/X/Filter/Apple.list` |
| Google | `https://raw.githubusercontent.com/egwj/Rules/master/Quantumult/X/Filter/Google.list` |
| Telegram | `https://raw.githubusercontent.com/egwj/Rules/master/Quantumult/X/Filter/Telegram.list` |
| Twitter | `https://raw.githubusercontent.com/egwj/Rules/master/Quantumult/X/Filter/Twitter.list` |
| Microsoft | `https://raw.githubusercontent.com/egwj/Rules/master/Quantumult/X/Filter/Microsoft.list` |
| Dropbox | `https://raw.githubusercontent.com/egwj/Rules/master/Quantumult/X/Filter/Dropbox.list` |
| PayPal | `https://raw.githubusercontent.com/egwj/Rules/master/Quantumult/X/Filter/PayPal.list` |

---

## 如何添加或修改规则

1. 打开 `Surge/RULE-SET/` 下对应的 `.list` 文件
2. 按 Surge 规则格式添加一行，例如：
   ```
   DOMAIN-SUFFIX,example.com
   DOMAIN-KEYWORD,example
   IP-CIDR,1.2.3.4/24
   ```
3. 保存文件，commit 并 push 到 GitHub
4. Actions 会在几分钟内自动将改动同步到 Clash 和 QX 格式

---

## 自动同步说明

| Workflow | 触发条件 | 生成内容 |
|----------|----------|----------|
| Sync Rules | `Surge/RULE-SET/` 有改动，或每天 UTC 00:00 | `Clash/RuleSet/`、`Quantumult/X/Filter/` |
| Sync Config | `Surge/Profile.conf` 有改动 | `Clash/Sample.yaml`、`Surge/Balloon.lcf`（Loon）、`Quantumult/Sample.conf` |
| Sync Modules | 定时或手动触发 | `Surge/Module/` |
