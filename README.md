# Llama.cpp Desktop

一个用于 Windows 的 llama.cpp 桌面端控制面板。它可以直接启动本地 `llama-server.exe`，提供 OpenAI Compatible 接口、聊天窗口、终端日志、历史对话、参数配置和托盘后台运行。

## 功能

- 直接启动 llama.cpp 原版目录里的 `llama-server.exe`
- 支持 OpenAI Compatible 接口，默认地址为 `http://127.0.0.1:8080/v1`
- 内置聊天页面，支持流式回复、历史对话、搜索和消息操作
- 支持图片、文本、PDF 等附件入口
- 支持模型信息弹窗、代码块复制和预览
- 支持终端日志查看，方便排查 llama.cpp 启动和推理问题
- 支持关闭窗口后隐藏到系统托盘，服务继续后台运行
- 支持配置模型路径、上下文、采样、GPU 层数、线程和批处理参数

## 运行环境

- Windows 10/11
- Node.js 18 或更高版本
- 一个可用的 llama.cpp Windows 构建目录，例如包含 `llama-server.exe` 的目录

## 开发运行

```powershell
npm install
npm start
```

## 打包

```powershell
npm run dist
```

打包产物会生成在 `dist/`，该目录不会提交到 Git。

## 使用方式

1. 打开桌面端。
2. 在设置里选择 llama.cpp 原文件目录，或直接选择 `llama-server.exe`。
3. 选择 GGUF 模型文件。
4. 保存配置并启动服务。
5. 使用内置聊天，或把 `http://127.0.0.1:8080/v1` 接入 OpenClaw、Claude Code 或其他 OpenAI 兼容客户端。

## 开源说明

本项目只包含桌面端源码，不包含 llama.cpp 二进制文件、模型文件、打包生成的 exe 或本地配置文件。

## License

MIT
