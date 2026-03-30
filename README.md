# GameDev MCP Plugin

MCP bridge plugin for AI-driven Unreal Editor and game development workflows.

Unreal Engine • MCP • AI agents • UMG • Blueprint • Animation Blueprint • Niagara • Landscape

Connect Codex, Claude Code, Cursor, and other MCP-compatible clients to real Unreal Engine workflows, including UMG, Blueprint, Animation Blueprint, Niagara, Landscape, materials, settings, and world operations.

## Overview

Most AI tools stop at code. GameDev MCP Plugin is built to let AI agents do real work inside Unreal Editor.

Core goals:

- let AI agents do real Unreal Editor work
- expose Unreal Editor workflows through MCP-oriented tooling
- make asset authoring and editor automation more accessible
- reduce the gap between prompting an agent and making actual changes in Unreal

## Features

- Asset query and lifecycle workflows
- UMG inspection and editing workflows
- Blueprint authoring and graph workflows
- Animation Blueprint and animation workflows
- Niagara and material workflows
- Settings and object inspection workflows
- Landscape, foliage, and world authoring workflows
- Editor automation helpers and MCP bridge integration

## Quick Start

1. Download the latest release ZIP.
2. Extract the plugin folder.
3. Copy `GameDevMCPPlugin/` into your Unreal project:
   - `<YourProject>/Plugins/GameDevMCPPlugin`
4. Restart Unreal Editor if needed.

## Clients

- Codex CLI
- Claude Code
- Cursor
- VS Code MCP-compatible clients
- other MCP-capable agent clients

## Use Cases

- create or inspect assets
- edit UMG widget trees
- build or patch Blueprints
- work with Animation Blueprints and animation assets
- inspect or modify Niagara and materials
- adjust editor settings and object properties
- author or automate world and landscape workflows

Useful for teams looking to:

- use an Unreal Engine MCP plugin
- build AI agent workflows for Unreal Editor
- automate Unreal Editor tasks with Codex or Claude
- explore AI-assisted UMG and Blueprint editing
- work with Animation Blueprint, Niagara, and Landscape authoring workflows
- connect MCP clients to real Unreal Editor operations

## Download

Download the latest package from the **Releases** page.

Always verify the included SHA256 checksum before installation.

## Included

This repository includes:

- binary plugin release packages
- release notes
- installation guidance
- known issues

Source code is not included in this repository.

## Included MCP Server

The package includes the embedded MCP server inside the plugin folder.

- Server root:
  - `<YourProject>/Plugins/GameDevMCPPlugin/mcp_server`
- Launchers:
  - `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.cmd`
  - `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.ps1`
  - `<YourProject>/Plugins/GameDevMCPPlugin/run_mcp_server.sh`

## Supported Setup

- Unreal Engine `5.7`
- Windows `Win64`
- Local Unreal Editor workflow validation

## Feedback

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

## Known Issues

For current limitations, compatibility notes, and workflow caveats, see `KNOWN_ISSUES.md`.

## Why Star This Project

If you care about:

- AI agents that can work with Unreal Editor
- practical MCP tooling for game development
- UMG, Blueprint, Niagara, animation, and landscape workflows through AI
- the future of AI-assisted Unreal development

If this is useful for your Unreal workflow, a star helps more developers find the project.
