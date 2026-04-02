# Client Setup

This document includes manual MCP setup examples for clients that do not support MCP registration by prompt.

## Recommended first try

Before doing any manual setup, try asking your AI client:

```text
Register the bundled mcp_server from this plugin as an MCP server and connect it to my running Unreal Editor.
```

If your client can manage MCP servers by prompt, that is the easiest path.

## MCP server location

The plugin package includes the MCP server here:

- `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server`

Bundled launchers:

- `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.cmd`
- `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.ps1`
- `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.sh`
- `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server_from_cwd.cmd`
- `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server_from_cwd.ps1`

You can also call the scripts directly from:

- `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server.cmd`
- `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server.ps1`
- `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server.sh`
- `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server_from_cwd.cmd`
- `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server_from_cwd.ps1`
- `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server_from_cwd.sh`

## Launcher modes

### Fixed-project launcher

Use the standard `run_mcp_server.*` launchers when the client configuration is already project-local and should always point to one Unreal project.

### Workspace-aware launcher

Use `run_mcp_server_from_cwd.*` when you want one global `ue-mcp` entry to follow the current client workspace and resolve the matching Unreal project automatically.

This is especially useful for:

- Codex CLI global MCP config
- Claude Code global MCP config
- GitHub Copilot CLI user config
- Gemini CLI user config

Current limitation:

- if multiple Unreal Editor instances of the same project are open at the same time, project-based routing can still be ambiguous
- if your client already uses per-project config files such as `.cursor/mcp.json` or `.vscode/mcp.json`, the fixed-project launcher is usually sufficient

## Codex on Windows

```powershell
codex mcp remove ue-mcp
codex mcp add ue-mcp -- D:\path\to\YourProject\Plugins\GameDevMCPPlugin\run_mcp_server_from_cwd.cmd
codex mcp get ue-mcp --json
```

## Codex on WSL / Linux

```bash
codex mcp remove ue-mcp
codex mcp add ue-mcp -- /path/to/YourProject/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server_from_cwd.sh
codex mcp get ue-mcp --json
```

## Optional Codex timeout setting

If Unreal startup or tool catalog sync is slow, add this to `~/.codex/config.toml`:

```toml
[mcp_servers.ue-mcp]
startup_timeout_sec = 60
```

## Claude Code on Windows

```powershell
claude mcp remove ue-mcp
claude mcp add --transport stdio ue-mcp -- cmd /c D:\path\to\YourProject\Plugins\GameDevMCPPlugin\run_mcp_server_from_cwd.cmd
claude mcp get ue-mcp
```

## Claude Code on WSL / Linux / macOS

```bash
claude mcp remove ue-mcp
claude mcp add --transport stdio ue-mcp -- bash /path/to/YourProject/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server_from_cwd.sh
claude mcp get ue-mcp
```

## Cursor on Windows

Create `.cursor/mcp.json` in your project:

```json
{
  "mcpServers": {
    "ue-mcp": {
      "command": "cmd",
      "args": [
        "/c",
        "${workspaceFolder}\\Plugins\\GameDevMCPPlugin\\run_mcp_server.cmd"
      ]
    }
  }
}
```

## Cursor on WSL / Linux / macOS

Create `.cursor/mcp.json` in your project:

```json
{
  "mcpServers": {
    "ue-mcp": {
      "command": "bash",
      "args": [
        "${workspaceFolder}/Plugins/GameDevMCPPlugin/run_mcp_server.sh"
      ]
    }
  }
}
```

## GitHub Copilot in VS Code on Windows

Create `.vscode/mcp.json` in your project:

```json
{
  "servers": {
    "ue-mcp": {
      "command": "cmd",
      "args": [
        "/c",
        "${workspaceFolder}\\Plugins\\GameDevMCPPlugin\\run_mcp_server.cmd"
      ]
    }
  }
}
```

After saving the file, use the **Start** button in `mcp.json`, then open Copilot Chat in **Agent** mode.

## GitHub Copilot in VS Code on WSL / Linux / macOS

Create `.vscode/mcp.json` in your project:

```json
{
  "servers": {
    "ue-mcp": {
      "command": "bash",
      "args": [
        "${workspaceFolder}/Plugins/GameDevMCPPlugin/run_mcp_server.sh"
      ]
    }
  }
}
```

After saving the file, use the **Start** button in `mcp.json`, then open Copilot Chat in **Agent** mode.

## GitHub Copilot CLI

You can add the server interactively with `/mcp add`, or define it directly in `~/.copilot/mcp-config.json`.

Example for Windows:

```json
{
  "mcpServers": {
    "ue-mcp": {
      "type": "local",
      "command": "cmd",
      "args": [
        "/c",
        "D:\\path\\to\\YourProject\\Plugins\\GameDevMCPPlugin\\run_mcp_server_from_cwd.cmd"
      ],
      "env": {},
      "tools": ["*"]
    }
  }
}
```

Example for WSL / Linux / macOS:

```json
{
  "mcpServers": {
    "ue-mcp": {
      "type": "local",
      "command": "bash",
      "args": [
        "/path/to/YourProject/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server_from_cwd.sh"
      ],
      "env": {},
      "tools": ["*"]
    }
  }
}
```

## Gemini CLI

Add the MCP server to `~/.gemini/settings.json` for a user-wide setup, or `.gemini/settings.json` for a project-local setup.

Example for Windows:

```json
{
  "mcpServers": {
    "ue-mcp": {
      "command": "cmd",
      "args": [
        "/c",
        "D:\\path\\to\\YourProject\\Plugins\\GameDevMCPPlugin\\run_mcp_server_from_cwd.cmd"
      ],
      "trust": false
    }
  }
}
```

Example for WSL / Linux / macOS:

```json
{
  "mcpServers": {
    "ue-mcp": {
      "command": "bash",
      "args": [
        "/path/to/YourProject/Plugins/GameDevMCPPlugin/mcp_server/scripts/run_mcp_server_from_cwd.sh"
      ],
      "trust": false
    }
  }
}
```

After configuring the file, start Gemini CLI and run `/mcp` to confirm that the server is connected.

## After setup

Once the MCP server is registered, these prompts are a good first test:

```text
Connect to my current Unreal Editor through MCP.
List the available tools from ue-mcp.
```

## Other MCP clients

Any MCP client that supports stdio MCP servers can use the same bundled launcher.

Use the launcher that matches the client environment:

- Windows client: `run_mcp_server.cmd`
- PowerShell-based client: `run_mcp_server.ps1`
- WSL / Linux / macOS client: `run_mcp_server.sh`
- Global multi-project setup: `run_mcp_server_from_cwd.cmd` / `run_mcp_server_from_cwd.ps1` / `mcp_server/scripts/run_mcp_server_from_cwd.sh`

In general, configure the client to launch the bundled script as a stdio MCP server, then ask the agent to connect to your running Unreal Editor.
