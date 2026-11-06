<div align="center">

# cursor-byok
cursor-byok is a local implementation of Cursor's backend.
<br>
<br>

[User Guide](https://docs.leokun.cn) · [中文版本说明](./README-CN.md)

[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](./LICENSE)
![Platforms](https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Linux-lightgrey?style=flat-square)

</div>

![Connect cursor-byok to a wide range of model APIs](./images/en-brand-1.png)

![cursor-byok dashboard](./images/en-home-1.png)

## About

cursor-byok is an open-source local model gateway for Cursor. It runs a service on your machine that connects Cursor to the model APIs you configure, routes model requests through your own providers, and preserves Cursor Agent capabilities such as tool calling, Skills, and MCP.

You can connect OpenAI- and Anthropic-compatible services, customize endpoints, model IDs, API keys, and request parameters, and use model channels beyond the options built into the platform.

> [!IMPORTANT]
> cursor-byok is free and open source, but the model APIs you connect may charge for usage. This is an independent project and is not affiliated with or endorsed by Cursor or its developers.

## Features

- **Bring your own model channels:** Configure your own API endpoint, credentials, and model IDs.
- **Multiple API protocols:** Use OpenAI- and Anthropic-compatible APIs or a custom endpoint.
- **Model management:** Add, duplicate, edit, reorder, and batch-test multiple model configurations.
- **Connection benchmarks:** Measure time to first token, generation speed, and inspect raw provider responses.
- **Agent workflows:** Keep tool calling, Skills, MCP, and multi-turn conversations available.
- **Session metrics:** Track token usage, cache hit rate, conversation turns, and estimated value.
- **Cross-platform:** Run on macOS, Windows, and Linux.

## Quick Start

1. Build cursor-byok from source (see [Development](#development)) or install a packaged build for your platform.
2. Launch cursor-byok, open **Model Settings**, and enter the endpoint, API key, and model ID.
3. Test the model configuration. Once it passes, return to the dashboard and start the service.
4. Test the model configuration. Once it passes, return to the dashboard and start the service.
5. After upgrading Cursor or configuring a model for the first time, quit Cursor completely and restart it, then start a new conversation and select the configured model.

For complete installation steps, system configuration, and Frequently Asked Questions, see the [User Guide](https://docs.leokun.cn).

## Model Management

Model configurations support both OpenAI and Anthropic API protocols. Each model channel can independently define its context window, maximum output tokens, reasoning effort, custom headers, and additional request parameters.

![cursor-byok model settings](./images/en-model-1.png)

## How It Works

```text
Cursor client
    │
    │ Agent requests and tool results
    ▼
cursor-byok local service
    │
    │ OpenAI- / Anthropic-compatible requests
    ▼
Your model API
```

cursor-byok handles protocol adaptation, model request forwarding, tool-call coordination, and conversation state on your machine. API keys and application settings are stored locally; requests are still sent to the model provider you configure.

## Why This Project

Many Agent products bundle their tool capabilities with a fixed set of models, subscriptions, and billing options, leaving users limited to the channels offered by the platform.

cursor-byok is built to return model choice to the user. Developers can make full use of the APIs and credits they already have, choose the models and providers that fit their needs, and self-host related services when required.

## Roadmap

The project will continue to improve model compatibility, Agent tooling, local runtime stability, and the self-hosting experience while exploring support for more IDE, chat, and Agent workflows.

## Community and Support

- [User Guide](https://docs.leokun.cn)
- [Telegram community](https://t.me/cursor_byok)
- QQ groups: `1095916242`, `1094411438`, `1095918002`, `1094419321`

## Development

Prerequisites: Rust toolchain with Cargo, Node.js with npm, the Tauri 2 system build dependencies, and Docker (only for the Docker image).

```bash
npm --prefix apps/desktop install   # install desktop dependencies

make dev-web                        # run the desktop frontend in the browser
make dev-desktop                    # run the Tauri desktop app

make check                          # format, lint, tests, and frontend build check

make build-web                      # build the desktop frontend
make build-server                   # build the Rust local service
make build-desktop                  # build the Tauri desktop installer
make build-docker                   # build the Docker image
```

Run `make check` before submitting changes.

## License

This project is open source under the [MIT License](./LICENSE).


