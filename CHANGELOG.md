# Changelog

All notable changes for this repository will be documented in this file.

## v0.8.4 - 2026-04-06

Stability and validation coverage release.

### Added

- Broader runtime validation coverage for UMG, animation asset, landscape/foliage, and widget reflector workflows
- Representative smoke and contract coverage across Blueprint, Animation Blueprint, Material, and Niagara refactor paths

### Improved

- Public preview validation depth for Blueprint, UMG, animation asset, material, Niagara, and world authoring workflows on UE `5.7` / `Win64`
- Internal editor handler and automation layout for safer follow-up preview releases

### Fixed

- Anim Montage section cleanup now clears stale next-section links when a referenced section is removed
- Runtime-added UMG widgets now preserve variable exposure more reliably during follow-up editing flows

### Compatibility

- Unreal Engine: `5.7`
- Platform: `Win64`
- Distribution: `Binary-only`

## v0.8.3 - 2026-04-02

Blueprint reroute coverage release.

### Added

- Public docs for Blueprint `K2Node_Knot` / reroute authoring coverage
- Runtime validation coverage for Blueprint reroute node creation and round-trip inspection

### Improved

- Blueprint graph authoring now supports `reroute`, `knot`, and `/Script/BlueprintGraph.K2Node_Knot` aliases in `blueprint.graph.node.add`
- Blueprint node inspection now reports canonical `node_type` values for comment box and knot nodes

### Fixed

- Removed the gap between changelog messaging and actual Blueprint reroute support
- `blueprint.graph.node.add` no longer rejects Blueprint reroute requests as unsupported node types

### Compatibility

- Unreal Engine: `5.7`
- Platform: `Win64`
- Distribution: `Binary-only`

## v0.8.2 - 2026-04-02

Authoring and launcher update release.

### Added

- Workspace-aware MCP launchers for WSL, PowerShell, and CMD workflows
- Codex registration helpers for switching one global `ue-mcp` entry across multiple Unreal projects
- Public docs for Blueprint comment box authoring and Material reroute / named reroute coverage

### Improved

- Blueprint graph authoring now includes comment box creation, configuration, and round-trip inspection
- Material graph authoring now includes reroute and named reroute declaration / usage flows
- `material_workflow` smoke coverage now validates named reroute material and material-function paths

### Fixed

- Reduced wrong-project connection issues when one global `ue-mcp` entry is reused across multiple Unreal projects
- Removed a named reroute Live Coding link-time failure caused by direct engine-method linkage

### Compatibility

- Unreal Engine: `5.7`
- Platform: `Win64`
- Distribution: `Binary-only`

## v0.8.1 - 2026-04-02

Packaging fix release.

### Fixed

- Fixed the binary plugin package so it works correctly as a precompiled Unreal plugin
- Kept only the required precompiled module definitions in `Source`
- Added `bUsePrecompiled = true;` to packaged module build files

### Notes

- This release supersedes `v0.8.0`
- `v0.8.0` is being withdrawn because of packaging/link errors in packaged project use

## v0.8.0 - 2026-03-31

First public release.

### Included

- Binary-only plugin package for `Unreal Engine 5.7`
- Win64 plugin build
- Embedded MCP server inside the plugin package
- MCP launch scripts and server files included in the release package
- Initial public distribution package for Unreal Editor workflow validation

### Coverage

- Core MCP bridge workflows
- Unreal Editor integration package
- Initial AI-driven workflow validation package

### Packaging Notes

- Distribution package is provided as a binary-only plugin release
- Source code is not included in this repository

### Compatibility

- Unreal Engine: `5.7`
- Platform: `Win64`
