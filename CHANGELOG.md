# Changelog

All notable changes for this repository will be documented in this file.

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
