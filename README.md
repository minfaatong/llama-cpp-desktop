<div align="center">
  <img src="assets/llama-cpp.png" width="88" alt="Llama.cpp Desktop logo" />

  <h1>Llama.cpp Desktop</h1>

  <p>
    A cross-platform desktop control panel for running and chatting with a local llama.cpp server.
    <br />
    Start the server, configure models, view logs, chat directly, or connect OpenAI-compatible clients — all in one window.
  </p>

  <p>
    <a href="README.md">English</a> · <a href="README.zh_CN.md">中文</a>
  </p>

  <p>
    <img alt="Windows" src="https://img.shields.io/badge/Windows-x64-506f51?style=flat-square" />
    <img alt="macOS" src="https://img.shields.io/badge/macOS-Apple_Silicon-506f51?style=flat-square" />
    <img alt="Linux" src="https://img.shields.io/badge/Linux-x64_%7C_ARM64-506f51?style=flat-square" />
    <img alt="Electron" src="https://img.shields.io/badge/Electron-41-506f51?style=flat-square" />
    <img alt="llama.cpp" src="https://img.shields.io/badge/llama.cpp-local-506f51?style=flat-square" />
    <img alt="License" src="https://img.shields.io/badge/license-MIT-151713?style=flat-square" />
  </p>
</div>

![Llama.cpp Desktop preview](docs/desktop-preview.svg)

## Features

| Feature | Description |
| --- | --- |
| Local connection | Directly launch `llama-server` from your llama.cpp directory — no extra launcher required |
| OpenAI compatible | Serves at `http://127.0.0.1:8080/v1`, compatible with OpenClaw, Claude Code, and any OpenAI client |
| Built-in chat | Web-style chat with streaming replies, conversation history, search, and message actions |
| Attachments | Upload images, text files, and PDFs; images preview inline in chat |
| Model info | Click the model badge to inspect current model, context, GPU layers, and runtime parameters |
| Terminal logs | View llama.cpp output inside the app for easy troubleshooting |
| System tray | Minimize to tray — server keeps running in the background |
| Configuration | Model path, context size, sampling, GPU layers, threads, and batch parameters |

## Downloads

> **Note**: This app does **not** include llama.cpp binaries, model files, or GPU drivers. You need to have a working llama.cpp build on your machine.

Check the [Releases](https://github.com/minfaatong/llama-cpp-desktop/releases) page for the latest version. Choose the file for your platform:

| Platform | Architecture | File |
|----------|-------------|------|
| Windows | x64 | `Llama.cpp-Desktop-{version}-win-x64.exe` |
| macOS | Apple Silicon (M1+) | `Llama.cpp-Desktop-{version}-mac-arm64.dmg` |
| Linux | x64 | `Llama.cpp-Desktop-{version}-linux-x64.AppImage` |
| Linux | ARM64 | `Llama.cpp-Desktop-{version}-linux-arm64.AppImage` |

## Quick Start

1. Download and run the appropriate file for your OS.
2. In the settings, point to your llama.cpp directory (select `llama-server.exe` on Windows, or `llama-server` on macOS/Linux).
3. Select a GGUF model file from your machine.
4. Save the config and start the server.
5. Use the built-in chat, or connect `http://127.0.0.1:8080/v1` to any OpenAI-compatible client.

## Development

```bash
npm install
npm start
```

## Packaging

```bash
npm run dist
```

Build artifacts go to `dist/` (not committed to Git).

## Limitations / Roadmap

- The app does **not** bundle llama.cpp, model files, GPU drivers, or CUDA/Vulkan runtimes — your machine needs a working llama.cpp environment.
- Image attachments can be uploaded and previewed, but understanding image content requires a vision model with a corresponding `mmproj` multimodal projection file.
- A text-only model won't gain vision capabilities just because an image was uploaded. Video understanding is not currently supported.
- Advanced features (ngram, multi-GPU, speculative decoding) can be passed via "Custom additional arguments" — whether they work depends on your local llama.cpp version.
- If desktop speed differs noticeably from the command line, copy the "Final launch command" and compare GPU layers, context, batch, ubatch, and threads settings.
- For Qwen and similar thinking models, `<think>` output depends on the model, template, and `chat_template_kwargs`. The desktop UI parses and folds `<think>...</think>` blocks.

## Project Structure

```text
assets/      Icons and tray icons
desktop/     Electron main process and preload scripts
renderer/    Desktop UI
scripts/     Icon generation scripts
```

## Open Source Notes

This repository contains only the desktop app source code. It does **not** include:

- llama.cpp binaries
- GGUF / GGML model files
- Packaged executables
- Local config files and logs

## License

MIT
