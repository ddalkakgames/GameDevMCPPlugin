# Known Issues

This document tracks known limitations and issues for the public preview build of GameDev MCP Plugin.

## Current Preview Scope

- Target engine version: `Unreal Engine 5.7`
- Target platform: `Win64`
- Distribution type: `Binary-only public preview`

## Known Limitations

### 1. Limited Engine Coverage

This preview is currently validated only for `Unreal Engine 5.7`.

Other engine versions may work partially, but they are not part of the current preview support target.

### 2. Preview Stability

This build is intended for evaluation and workflow validation.

- stability is still being validated
- edge-case failures may still exist
- some workflows may need additional usability improvements

### 3. Incomplete Workflow Coverage

Not every intended Unreal Editor workflow is finalized yet.

Depending on your use case, some authoring paths may still feel incomplete, verbose, or inconsistent.

### 4. Breaking Changes Between Preview Releases

Backward compatibility between preview releases is not guaranteed.

- release packaging may change
- workflow shape may change
- command coverage may expand or shift

### 5. Production Use Is Not Recommended Yet

This preview should not yet be treated as a production-ready plugin release.

Use caution before testing it in active project branches.

### 6. Source Code Is Not Included

This public preview repository distributes binary packages only.

Source code is not included in this repository.

## Reporting Issues

When reporting issues, please include:

- Unreal Engine version
- OS and platform
- release tag
- reproduction steps
- relevant logs
- screenshots or short recordings when possible

## Validation Goals For Preview

This preview primarily exists to validate:

- installation success
- editor stability
- workflow clarity
- missing authoring flows
- documentation gaps
