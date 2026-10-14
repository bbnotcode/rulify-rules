# Rulify Rules · 个人网络规则仓库

> 状态：**仓库已初始化，尚无真实分流规则。** 本项目专门存放经过检查的 Rulify 导出结果，供 Shadowrocket（小火箭）和 Quantumult X（圈叉）使用。不会更改现有节点订阅或代理配置。

## 仓库地址
https://github.com/bbnotcode/rulify-rules

## 目录与预留订阅地址

| 软件 | 文件 | Raw 网址 |
| --- | --- | --- |
| Shadowrocket | `shadowrocket/rulify.list` | https://raw.githubusercontent.com/bbnotcode/rulify-rules/main/shadowrocket/rulify.list |
| Quantumult X | `quantumult-x/rulify.list` | https://raw.githubusercontent.com/bbnotcode/rulify-rules/main/quantumult-x/rulify.list |

**重要**：这两个文件目前只有注释（无实际规则），**请勿将它们作为正式规则订阅启用**。导入并审核隐私报告、由 Rulify 生成适配对应软件的规则并成功上传之后，再在代理软件中启用正确的 Raw URL。

## 在 Rulify 里连接 GitHub

1. 前往 GitHub 设置创建 fine-grained Personal Access Token（细粒度访问令牌），仅给本仓库 `Contents: Read and write` 权限；不要发送给他人或提交到仓库。
2. 打开 Rulify 的 GitHub 设置（具体标签依 App 版本而异），填写你的账号 `bbnotcode`、仓库 `rulify-rules`、分支 `main`，以及令牌。
3. 如果 App 有目录字段：按导出目标分开，例如 Shadowrocket 用 `shadowrocket/`、Quantumult X 用 `quantumult-x/`；如果只能设一个目录，可以先使用 `generated/`，以 Rulify 实际创建的文件为准。
4. 先手动上传一份小规模、**经过检查**的规则文件。查看远程文件列表并复制其 Raw 地址；确认后再考虑打开“生成后自动上传”。
5. 如果 Rulify 新建了以 App 名称命名的文件，请订阅**它实际上传的文件**；不要认为预留的 `rulify.list` 会自动被更新。

详细步骤见 [SETUP.md](SETUP.md)。

## 推荐用法

- **隐私报告只是联网记录，不等于恶意软件/广告清单**。不能仅凭访问次数判断域名用途。
- 根据需要用 Rulify 导出 **Shadowrocket 格式** 或 **Quantumult X 格式**，两者分别订阅，避免直接混用。
- 规则发布前检查目标域名、动作（DIRECT / PROXY / REJECT）及匹配范围，避免误伤登录、支付或消息推送。
- 默认不公开原始 `.ndjson` 报告、Cookie、订阅地址、节点、Token 或其他隐私资料。此仓库为 **Public**，上传的规则文件也会被公开访问。

## 设备兼容与注意事项

- Rulify 是规则**生成器**，不是实时网络监控工具；不替代 Shadowrocket、Quantumult X。
- 现有 Shadowrocket/Quantumult X 配置不自动改变；只有你在对应 App 内正确添加且启用新规则后才会生效。
- 订阅规则匹配顺序、覆盖优先级取决于你当前配置；建议先备份配置并少量验证。

## 文件

- `shadowrocket/rulify.list`：小火箭规则占位（目前不含实际规则）
- `quantumult-x/rulify.list`：圈叉规则占位（目前不含实际规则）
- `.gitignore`：避免在 Git 操作中误添加敏感文件（**不能阻止 Rulify 直接通过 GitHub API 上传这些文件**）
- `SETUP.md`：手机端配置指引
