# GameDev MCP Plugin

<p align="center">
  <a href="https://github.com/ddalkakgames/GameDevMCPPlugin/releases/latest">
    <img src="https://img.shields.io/github/v/release/ddalkakgames/GameDevMCPPlugin?label=release" alt="Latest Release">
  </a>
  <img src="https://img.shields.io/badge/UE-5.7-0E1128?logo=unrealengine" alt="UE 5.7">
  <img src="https://img.shields.io/badge/platform-Win64-1f6feb" alt="Win64">
  <img src="https://img.shields.io/badge/distribution-binary--only-f59e0b" alt="Binary Only">
  <img src="https://img.shields.io/badge/MCP-enabled-10b981" alt="MCP Enabled">
</p>

<p align="center">
  <strong>Enable AI agents to work inside Unreal Editor through MCP.</strong>
</p>

<p align="center">
  Build Unreal Editor workflows with Codex, Claude Code, Cursor, and other MCP-compatible clients.
</p>

> Unreal Engine • MCP • AI agents • UMG • Blueprint • Animation Blueprint • Niagara • Landscape • Materials • World workflows

## ✨ Overview

Most AI tools stop at code.  
GameDev MCP Plugin is built to help AI agents work with actual Unreal Editor workflows through an embedded MCP server and Unreal-side tooling.

This project is especially useful if you want to:

- connect Codex, Claude Code, Cursor, or other MCP clients to Unreal Editor
- inspect and edit Unreal assets with AI agents
- build AI-assisted workflows for UMG, Blueprint, Animation Blueprint, Niagara, materials, and world authoring
- reduce the gap between prompting an agent and making changes inside Unreal Editor

## 🔥 Features

- Asset query and lifecycle workflows
- UMG inspection and editing workflows
- Blueprint authoring and graph workflows
- Animation Blueprint and animation workflows
- Niagara and material workflows
- Settings and object inspection workflows
- Landscape, foliage, and world authoring workflows
- Embedded MCP server and Unreal Editor bridge tooling

## 🚀 Quick Start

### 1. Install the plugin

1. Download the latest release ZIP from the [Releases](https://github.com/ddalkakgames/GameDevMCPPlugin/releases/latest) page.
2. Extract the package.
3. Copy `GameDevMCPPlugin/` into your Unreal project:
   - `<YourProject>/Plugins/GameDevMCPPlugin`
4. Open your project in Unreal Editor.
5. Confirm the plugin is loaded and that this file exists:
   - `<YourProject>/Saved/UnrealMCP/connection.json`

### 2. Register the MCP server in your AI client

The plugin package includes the MCP server inside:

- `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server`

Use the included launcher that matches your client environment.

**Codex on Windows**

```powershell
codex mcp remove ue-mcp
codex mcp add ue-mcp -- D:\path\to\YourProject\Plugins\GameDevMCPPlugin\mcp_server\scripts\run_mcp_server.cmd
codex mcp get ue-mcp --json
```

**Codex on WSL / Linux**

```bash
codex mcp remove ue-mcp
codex mcp add ue-mcp -- /path/to/YourProject/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server.sh
codex mcp get ue-mcp --json
```

Other MCP clients can use the same launcher as a standard stdio MCP server.

### 3. Ask your AI agent to connect to Unreal

After the MCP server is registered, ask your agent to connect to the current Unreal Editor session.

**Example prompts**

```text
Connect to my current Unreal Editor through MCP.
List the available tools from ue-mcp.
```

If you prefer Korean prompts in Codex, this also works:

```text
현재 언리얼 에디터랑 MCP 연결해줘.
ue-mcp에서 사용할 수 있는 툴 목록 보여줘.
```

After that, you can ask for higher-level tasks such as:

```text
Create a UMG widget blueprint for a pause menu.
Inspect this Animation Blueprint and summarize its state machine.
Add trees and grass to the currently open level.
```

### 4. Optional Codex timeout setting

If Unreal startup or tool catalog sync is slow, add this to `~/.codex/config.toml`:

```toml
[mcp_servers.ue-mcp]
startup_timeout_sec = 60
```

## 🤖 Clients

- Codex CLI
- Claude Code
- Cursor
- VS Code MCP-compatible clients
- other MCP-capable agent clients

## 🧩 Use Cases

- create or inspect assets
- edit UMG widget trees
- build or patch Blueprints
- work with Animation Blueprints and animation assets
- inspect or modify Niagara and materials
- adjust editor settings and object properties
- author or automate world and landscape workflows

## 📦 Download

Download the latest package from the [Releases](https://github.com/ddalkakgames/GameDevMCPPlugin/releases/latest) page.

Always verify the included SHA256 checksum before installation.

## 🧰 Included

This repository includes:

- binary plugin release packages
- embedded MCP server files inside the plugin package
- release notes
- installation guidance
- known issues

The full Unreal plugin source repository is not included in this public repository.

## 🔌 Included MCP Server

The package includes the embedded MCP server inside the plugin folder.

- Server root:
  - `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server`
- Launchers:
  - `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.cmd`
  - `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.ps1`
  - `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.sh`

## 🖥️ Supported Setup

- Unreal Engine `5.7`
- Windows `Win64`
- Local Unreal Editor workflow validation

## 🐞 Feedback

Feedback is welcome for:

- installation experience
- editor stability
- workflow clarity
- missing authoring flows
- documentation gaps

When reporting issues, include:

- Unreal Engine version
- OS and platform
- exact release tag
- reproduction steps
- relevant logs or screenshots

## ⚠️ Known Issues

For current limitations, compatibility notes, and workflow caveats, see [KNOWN_ISSUES.md](./KNOWN_ISSUES.md).

## ⭐ Star This Project

If this is useful for your Unreal workflow, a star helps more developers find the project.
