# Rulify GitHub 同步配置（iPhone / iPad）

以下仓库已创建：

- GitHub 用户：`bbnotcode`
- 仓库：`rulify-rules`
- 分支：`main`
- 地址：https://github.com/bbnotcode/rulify-rules
- 可见性：**Public**。仅在审核后上传不含个人信息的规则文件。

## 1. 创建专用 GitHub Token

1. 打开 https://github.com/settings/personal-access-tokens/new （如页面变化，进入 GitHub Settings → Developer settings → Personal access tokens → Fine-grained tokens）。
2. Token name 可填 `Rulify Rules Sync`，建议设置有效期（例如 90 天）。
3. Resource owner 选择 `bbnotcode`。
4. Repository access 选择 **Only select repositories**，只勾选 `rulify-rules`。
5. 在 Repository permissions 找到 **Contents**，设置 **Read and write**；Metadata 通常自动为 Read-only。其余保持不授权。
6. 创建并复制 Token，**只粘贴在手机 Rulify 的 GitHub 设置中**；不要发给聊天助手、仓库或其他人。

> Rulify 会读取这个 Token 才能推送文件；如果 App 的界面/所需权限不同，以实际提示为准。过期后需要换新的 Token。

## 2. 在 Rulify 填写 GitHub 设置

尝试在 App 内进入 GitHub / GitHub 同步设置，按实际页面填写：

| 项目 | 值 |
| --- | --- |
| GitHub Owner / Username | `bbnotcode` |
| Repository / Repo | `rulify-rules` |
| Branch | `main` |
| Token | **第 1 步自行创建的 Token** |
| Path / 目录（如果能选） | `generated/` 或按导出格式分目录 |

**注意**：不能预设 Rulify 会使用固定文件名。如果它自己决定保存路径，请先查看 App 的「远程文件列表」或 GitHub 仓库实际路径。优先使用 App 显示的真实 Raw 链接。

## 3. 首次使用

1. iPhone 设置 → 隐私与安全性 → App 隐私报告 → 开启（如尚未开启）。
2. 正常使用需要分析的 App 一段时间，然后在该报告页面导出 `.ndjson` 数据至本机文件。
3. 在 Rulify 导入报告、筛选需要的域名，人工确认规则动作。
4. 先选择一种代理格式（例如 **Shadowrocket**）生成规则，**手动上传到 GitHub**。
5. 打开 GitHub 仓库检查所上传内容、格式和文件路径；确认无敏感内容后再考虑启用自动同步。
6. 对 Quantumult X 单独生成匹配格式的规则，不要无审核地照搬小火箭文件。

## 4. 在代理工具订阅规则

预留链接（初始只有注释，并**未包含真正可用规则**）：

- Shadowrocket：https://raw.githubusercontent.com/bbnotcode/rulify-rules/main/shadowrocket/rulify.list
- Quantumult X：https://raw.githubusercontent.com/bbnotcode/rulify-rules/main/quantumult-x/rulify.list

当你确认 Rulify 已经把真实规则上传到这些文件时，可尝试用对应客户端的远程规则入口添加；**如果 Rulify 上传到了其他路径，请使用那个文件的 Raw URL**。

不要把规则文件 URL 当作节点订阅 URL；不同客户端还有不同的规则集引用语法。注意规则动作、位置、优先级和配置兼容性。

## 5. 安全与疑难排查

- **GitHub 公开仓库意味着上传的所有内容都可以被别人看到。** 只上传审核后的规则，**不上传原始隐私报告、订阅、机场地址、账号、Token 或个人数据**。
- `.gitignore` 对手动使用 git 的提交有帮助，**不限制 Rulify 通过 GitHub API 直接上传敏感文件**。
- 如果上传报 401：检查 Token 是否有效；报 403：检查仓库权限、资源 owner 或安全限制；报 404：确认仓库名、分支和授权范围。
- 规则链接返回 404：检查是否实际上传、分支是否 `main`、路径是否正确。
- 规则下载成功但未生效：检查是否启用了远程规则、匹配顺序，以及使用了正确客户端导出格式。
- 初次调试只使用少量非敏感域名，先确认登录、支付、通知、图片加载等没有受到影响。

## 关于自动同步

只有在 App 内看到并手动验证对应开关后，才能确认“生成后上传”和/或“导入报告后上传”能按你预期工作。本仓库只是接收与托管规则，**它本身不会定时分析你的手机联网信息或主动拉取隐私报告**。
