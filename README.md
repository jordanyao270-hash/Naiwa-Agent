# Naiwa Agent

<p align="center">
  <img src="assets/naiwa-agent.png" width="280" alt="Naiwa Agent 欢乐奶娃徽标">
</p>

Naiwa Agent 是基于 [LibreChat](https://github.com/LibreChat-AI/LibreChat) 的 Windows x64 个人 AI 助手。你可以在自己的电脑上运行聊天服务，接入兼容 OpenAI Chat Completions 接口的云端或本地模型。选择支持工具调用的模型后，还可以在对话中让助手做算术或查询不同时区的当前时间。

## 首次使用只需三步

1. **启动 Docker Desktop。** 在 Windows x64 电脑上安装并启动 Docker Desktop，启用 Linux 容器。[Docker 官方安装说明](https://docs.docker.com/desktop/setup/install/windows-install/)
2. **配置模型和本机密码。** 完整解压发行包 `Naiwa-Agent-Personal-1.1-Windows-x64.zip`，让 `Naiwa Agent.exe` 和 `naiwa-runtime.tar` 保持在同一目录。双击 EXE，填写服务商提供的 API 根地址和模型 ID，设置至少 12 个字符的本机登录密码，然后点击「进入 Naiwa Agent」。API 地址一般以 `/v1` 结尾，填写时省略 `/chat/completions`。
3. **登录并填写自己的 API Key。** 在聊天窗口使用 `owner@naiwa.local` 和刚设置的密码登录。打开模型选择器，找到以 `Naiwa-` 开头的模型接口，在密钥设置里填写自己的 API Key，选择保存期限后即可开始聊天。

第一次使用工具时，可以试着问：“请调用计算器，把 127 箱、每箱 36 件换算成总件数。”

## 数据存在哪里

| 项目 | 运行或保存位置 |
| --- | --- |
| 聊天服务 | 在你的电脑上运行，只监听本机回环地址 `127.0.0.1`。网页公开注册已关闭。 |
| 账户与聊天记录 | 保存在本机 Docker 数据卷中。每台电脑独立生成数据卷和加密密钥，数据库不向宿主机开放端口。 |
| 模型 API Key | 按本机账户和模型接口保存，可设置有效期，也可随时在密钥设置中撤销。切换 API 根地址后，需要为新地址单独配置 Key。 |
| 模型请求 | 使用云模型时，发送给模型的对话内容和工具结果会传给所选服务商。使用本机模型时，请把 API 地址指向本机运行的模型服务。 |

关闭聊天窗口后，服务会继续运行。在启动器点击「停止服务」可停止本机实例，并保留对话供下次使用。
