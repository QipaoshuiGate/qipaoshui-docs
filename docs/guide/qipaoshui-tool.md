# 气泡水客户端

**气泡水客户端**（qipaoshui-tool）是官方桌面应用。登录账号、创建 API Key、把本机的 **Codex** 和 **Claude Code** 接入气泡水，全部在一个窗口里完成，随时可以一键恢复官方配置。

::: tip 都推荐用气泡水客户端
无论你用 **Codex**（命令行或桌面应用）、**Claude Code**，还是 **ChatGPT 桌面应用**，都推荐用本页的气泡水客户端接入：登录账号后一键写好配置，不必手动复制粘贴。

其中 Codex 桌面应用与命令行共用 `~/.codex/config.toml`，客户端写入一次，两者同时生效。

如果你更习惯手动导入，也可以参考 [CC Switch 的三步教程](/guide/getting-started)。
:::

## 一、下载安装

👉 **[前往 Releases 页面下载最新版](https://github.com/QipaoshuiGate/qipaoshui-tool/releases/latest)**（此链接始终指向最新版本）

也可以直接用下面的加速直链，当前版本 **v0.1.1**：

| 系统 | 架构 | 下载链接 | 安装方式 |
| :--- | :---: | :--- | :--- |
| Windows | x64 | [qipaoshui-tool_x64-setup.exe](https://v4.gh-proxy.org/https://github.com/QipaoshuiGate/qipaoshui-tool/releases/download/v0.1.1/qipaoshui-tool_0.1.1_x64-setup.exe) | 双击安装 |
| Windows | x64（MSI） | [qipaoshui-tool_x64_en-US.msi](https://v4.gh-proxy.org/https://github.com/QipaoshuiGate/qipaoshui-tool/releases/download/v0.1.1/qipaoshui-tool_0.1.1_x64_en-US.msi) | 双击安装 |
| macOS | Apple Silicon (M1/M2/M3/M4) | [qipaoshui-tool_aarch64.dmg](https://v4.gh-proxy.org/https://github.com/QipaoshuiGate/qipaoshui-tool/releases/download/v0.1.1/qipaoshui-tool_0.1.1_aarch64.dmg) | 拖入「应用程序」 |
| macOS | Intel | [qipaoshui-tool_x64.dmg](https://v4.gh-proxy.org/https://github.com/QipaoshuiGate/qipaoshui-tool/releases/download/v0.1.1/qipaoshui-tool_0.1.1_x64.dmg) | 拖入「应用程序」 |
| Linux | x64 | [.deb](https://v4.gh-proxy.org/https://github.com/QipaoshuiGate/qipaoshui-tool/releases/download/v0.1.1/qipaoshui-tool_0.1.1_amd64.deb) · [.rpm](https://v4.gh-proxy.org/https://github.com/QipaoshuiGate/qipaoshui-tool/releases/download/v0.1.1/qipaoshui-tool-0.1.1-1.x86_64.rpm) · [.AppImage](https://v4.gh-proxy.org/https://github.com/QipaoshuiGate/qipaoshui-tool/releases/download/v0.1.1/qipaoshui-tool_0.1.1_amd64.AppImage) | 按包管理器安装 |

::: tip
表格中的直链固定指向 v0.1.1。发布新版本后直链不会自动更新，请以上方的 [Releases 页面](https://github.com/QipaoshuiGate/qipaoshui-tool/releases/latest) 为准。
:::

### macOS 首次打开提示「无法验证开发者」

安装包尚未经过 Apple 公证，首次打开会被系统拦截。二选一：

- 打开「**系统设置 → 隐私与安全性**」，在底部点击「**仍要打开**」；
- 或在终端执行：

```bash
xattr -cr /Applications/qipaoshui-tool.app
```

## 二、登录或注册

首次打开进入登录页。

**已有气泡水账号**：填入邮箱和密码，点「登录」。

**还没有账号**：点底部「去注册」，然后：

1. 填写邮箱，点「**发送**」获取验证码（60 秒内不能重复发送）；
2. 填入收到的 6 位验证码；
3. 设置密码（至少 6 位）；
4. 邀请码选填；
5. 若页面出现人机验证，需先勾选通过，「注册」按钮才可点击。

::: info 开启了两步验证
登录后会多一步「TOTP 动态码」，输入验证器 App 上的 6 位数字即可。
:::

登录状态会保存在本机，下次打开应用直接进入控制台。左下角可以看到当前账号邮箱与余额，点右侧图标登出。

## 三、创建 API Key

在左侧边栏进入「**API Keys**」页面，点右上角「**新建 Key**」，填一个便于识别的名称（例如 `工作机`），点「创建」。

列表中每个 Key 会显示：

- **名称**与**状态**（启用 / 停用），设置了有效期的还会显示过期日期；
- **掩码后的 Key**，点眼睛图标显示完整内容，点复制图标复制到剪贴板；
- **已用额度**，设置了配额的会显示用量进度条（超过 90% 变红）。

::: warning 删除不可撤销
删除某个 Key 后，正在使用它的客户端会立即失效，请先确认没有设备在用。
:::

## 四、一键接入 Codex 与 Claude Code

回到「**控制台**」。顶部两张卡片显示本机当前状态：

| 标识 | 含义 |
| :--- | :--- |
| 🟢 已接入 qipaoshui | 该工具已指向气泡水 |
| ⚪ 官方配置 | 仍在使用官方服务 |
| 🟡 未知状态 | Codex 配置文件为空或不存在 |

在下方「一键切换」区域确认参数：

| 字段 | 默认值 | 说明 |
| :--- | :--- | :--- |
| API Key | 你的第一个 Key | 下拉选择要写入的 Key |
| 模型 | `gpt-5.5` | 写入 Codex 的默认模型 |
| 接口协议（wire_api） | `responses` | 可切换为 `chat` |
| Codex Base URL | `https://qipaoshui.buzz/v1` | **带** `/v1` |
| Claude Base URL | `https://qipaoshui.buzz` | **不带** `/v1` |

点「**应用 qipaoshui**」，提示「已切换到 qipaoshui」即写入成功，两张状态卡片会变成绿色。

::: warning 需要重开客户端
Codex 和 Claude Code 只在启动时读取配置文件：

- **命令行**：结束正在运行的会话，新开一个终端；
- **Codex 桌面应用**：完全退出后重新打开（macOS 需在程序坞上右键「退出」，仅关闭窗口无效）。
:::

想换 Key 或换模型时，改完表单再点一次「应用 qipaoshui」即可，不需要先恢复。

## 五、工具改了哪些文件

| 工具 | 文件 | 写入内容 |
| :--- | :--- | :--- |
| Codex | `~/.codex/config.toml` | `model`、`model_provider`、`[model_providers.qipaoshui]` |
| Codex | `~/.codex/auth.json` | `OPENAI_API_KEY` |
| Claude Code | `~/.claude/settings.json` | `env.ANTHROPIC_BASE_URL`、`env.ANTHROPIC_AUTH_TOKEN` |

写入 `~/.codex/config.toml` 的内容形如：

```toml
model = "gpt-5.5"
model_provider = "qipaoshui"

[model_providers.qipaoshui]
name = "Qipaoshui"
base_url = "https://qipaoshui.buzz/v1"
wire_api = "responses"
experimental_bearer_token = "sk-..."
```

写入 `~/.claude/settings.json` 的内容形如：

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://qipaoshui.buzz",
    "ANTHROPIC_AUTH_TOKEN": "sk-..."
  }
}
```

::: info 原有配置会保留
写入采用合并方式：`config.toml` 里的其他配置段、`settings.json` 里的其他字段、`auth.json` 里已有的 ChatGPT 登录信息，都会原样保留，只增改上面列出的这几项。
:::

## 六、恢复官方配置

应用之前，工具会自动把当前的 Codex 与 Claude Code 配置存成快照，放在 `~/.qipaoshui-tool/snapshots/`，保留最近 10 份。

需要切回官方服务时，点控制台底部的「**恢复官方配置**」，即可回滚到接入气泡水之前的状态。同样需要重开终端才生效。

::: tip 按钮是灰的？
说明本机还没有可用的快照，通常是因为从未通过本工具应用过配置。此时不需要恢复，本工具也没有改动过你的配置。
:::

::: info 重复应用不会覆盖快照
只有在当前处于官方配置状态时，工具才会新建快照。已经接入气泡水后再次点「应用」（例如换个 Key），不会把气泡水的配置存成"官方"快照。
:::

## 常见问题

### 控制台提示「暂无可用的 API Key」

还没有创建 Key。点提示右侧的「去创建 →」，或从侧边栏进入「API Keys」页面新建一个。

### 应用之后还是走官方服务

配置只在启动时读取。命令行请新开一个终端窗口，Codex 桌面应用请完全退出后重新打开，再试一次。

### 用 GPT 5.6 系列模型生图失败

客户端写入的配置不含生图所需的两项参数，需要手动补进 `~/.codex/config.toml` 的 `[model_providers.qipaoshui]` 配置段，详见 [常见问题 · GPT 5.6 生图失败](/guide/faq#gpt-5-6-系列模型对话时生图失败)。

注意每次重新点「应用 qipaoshui」都会重建该配置段，补的内容会被覆盖。

### 状态卡片显示「未知状态」

表示 `~/.codex/config.toml` 为空或不存在，即本机还没有任何 Codex 配置。点「应用 qipaoshui」会自动创建。

### 遇到其他问题

请到 [qipaoshui-tool Issues](https://github.com/QipaoshuiGate/qipaoshui-tool/issues) 反馈，并附上客户端版本号与操作步骤。
