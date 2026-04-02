# Capability Matrix

This document summarizes the current public capability surface of GameDev MCP Plugin by Unreal Editor domain.

It is intentionally conservative.

`Advanced` means the domain already has multiple implemented tools and validated workflows. It does **not** mean one-to-one parity with every Unreal Editor panel or every human-facing tool mode.

## Support Levels

- **Advanced**: multiple tools and practical workflows are implemented and already useful in real editor sessions.
- **Partial**: meaningful workflows exist, but the domain is still narrower than full production authoring parity.
- **Read-only**: inspection and analysis are supported, but editing is not the main path.
- **Planned**: not something to rely on in the current public release.

## Scope Notes

- This matrix focuses on **editor-side MCP surfaces** exposed to AI agents through the bundled MCP server.
- Many higher-level workflows combine shared tools such as `asset.*`, `object.*`, `settings.*`, `job.*`, and `changeset.*`.
- Current public validation is strongest on **UE 5.7 / Win64 / local editor workflows**.

## Domain Matrix

| Domain | Current Level | Read / Inspect | Create | Edit / Author | Validate / Preview / Compile | Current Public Notes |
|---|---|---|---|---|---|---|
| MCP Runtime / Jobs / Health | Advanced | Yes | N/A | N/A | Yes | `tools.list`, `system.health`, `job.get`, and `job.cancel` are available for operational workflows and async follow-up. |
| Asset Lifecycle | Advanced | Yes | Yes | Yes | Partial | Asset create, find, load, duplicate, import, save, rename, and delete are available and reused across many domains. |
| Changesets / Rollback | Partial | Yes | N/A | Preview / rollback | N/A | Changeset listing and rollback preview are available. Rollback apply exists, but practical coverage still depends on domain and undoability. |
| Object Inspect / Patch | Advanced | Yes | No | Yes | N/A | `object.inspect`, `object.patch`, and `object.patch.v2` provide the shared property editing surface used by several authoring domains. |
| Project / GameMode Settings | Advanced | Yes | N/A | Yes | Apply | Project settings patch/apply and GameMode get/default/map override/compose workflows are available. |
| Editor / Live Coding | Partial | Yes | N/A | Compile trigger | Partial | `editor.livecoding.compile` exists with artifact capture and job requery, but self-patch safe mode is asynchronous and Windows/editor-session specific. |
| Blueprint | Advanced | Yes | Yes | Yes | Yes | Blueprint class, variable, function, graph node/pin, comment box, compose, stabilize, validate, and compile flows are implemented. |
| UMG / Widget Blueprint | Advanced | Yes | Yes | Yes | Yes | Widget Blueprint creation, widget tree edits, slot patching, bindings, events, animations, and UMG workflow helpers are available. |
| Runtime UI / Slate / Widget Reflector | Read-only | Yes | No | No | N/A | Live editor UI snapshots, hit tests, focus inspection, and snapshot diffing are supported for runtime introspection. |
| Material | Advanced | Yes | Yes | Yes | Yes | Material graph expression add/connect/configure, reroute and named reroute flows, property wiring, layout, and recompile flows are supported. |
| Niagara | Partial | Yes | Yes | Limited | Partial | System, emitter, module, renderer, param, template, preview, and validate flows exist, but public positioning should still stay conservative on full native parity. |
| Animation Blueprint | Advanced | Yes | Yes | Yes | Yes | Anim Blueprint create, summary, graph/state-machine authoring, transition rule editing, anim graph node insertion, and validate/compile flows are present. |
| Anim Montage | Advanced | Yes | Yes | Yes | Preview | Montage create, summary, section/slot/segment workflows, notify/branching point add, blend patch, and preview play are exposed. |
| Anim Notify / Anim Notify State | Advanced | Yes | Yes | Yes | Yes | Notify Blueprint and NotifyState Blueprint creation, summary, reparent, compile, and follow-up generic Blueprint graph editing are supported. |
| PoseAsset | Advanced | Yes | Yes | Yes | N/A | PoseAsset create, summary, pose listing, and additive/full pose space conversion are available. |
| BlendSpace | Advanced | Yes | Yes | Yes | Resample / validate | BlendSpace and BlendSpace1D create, summary, axis patch, and sample add/update/remove are supported. |
| AimOffset | Advanced | Yes | Yes | Yes | Resample / validate | AimOffset and AimOffset1D create, summary, axis patch, sample add/update/remove, and additive consistency validation are supported. |
| Anim Sequence Slicing | Advanced | Yes | No | Yes | N/A | AnimSequence summary plus single and batch slicing workflows are implemented. This is a focused authoring surface, not full raw animation editing. |
| Control Rig | Advanced | Yes | Yes | Yes | Yes | Control Rig asset lifecycle, hierarchy/control access, pose workflows, variables, compile/validate, and Sequencer integration are available. |
| Sequencer | Advanced | Yes | Yes | Yes | Partial | Sequence asset create/load, inspect, binding/track/section CRUD, key set/remove/bulk set, and compose workflows are supported. |
| Data Table | Advanced | Yes | Yes | Yes | Validation | DataTable create, summary, schema describe, row CRUD, row upsert/rename, and CSV/JSON export are available. |
| World / Actors | Advanced | Yes | Yes | Yes | Partial | Actor spawn, move, attach/detach, duplicate, tagging, selection, component add/remove/patch, and validation/build helpers are available. |
| PCG | Advanced | Yes | Yes | Yes | Generate / bake | PCG graph and component workflows include graph setup, binding, generation, bake, unbake, and orchestration helpers. |
| Landscape / Foliage | Advanced | Yes | Yes | Yes | Partial | Landscape create, inspect, sculpt, paint, preview-material helpers, foliage add/clear, and rollback-aware workflows are available through a focused stamp/scatter surface. |

## Details By Area

### Core Editor and Shared Infrastructure

#### MCP Runtime / Jobs / Health

- Discover available tools with `tools.list`
- Check server/editor connectivity with `system.health`
- Track long-running or async work with `job.get` and `job.cancel`
- Use this layer for client integration, observability, and follow-up polling

#### Asset Lifecycle

- Create new assets
- Load and find assets
- Duplicate, rename, save, import, and delete assets
- Reuse the same asset lifecycle surface across Blueprint, materials, animation assets, data tables, and more

#### Changesets / Rollback

- Inspect recorded changesets
- Preview rollback impact before applying it
- Apply rollback in supported cases

Current limitation:

- Rollback support is real, but not every write path should be marketed as equally rollback-complete yet.

#### Object Inspect / Patch

- Inspect arbitrary UObject properties
- Patch structured properties through shared generic tooling
- Reuse the same property patch path from higher-level domains such as materials, settings, and Sequencer object patch flows

#### Project / GameMode Settings

- Read and patch project settings
- Apply staged project setting changes
- Read and compose GameMode defaults and map overrides

#### Editor / Live Coding

- Trigger Live Coding compile from MCP
- Capture build artifacts and excerpts
- Requery final completion state through job tracking

Current limitation:

- In self-patch safe mode, compile completion is asynchronous. Treat this as a practical workflow surface, not instant synchronous compile parity.

### Blueprint and UI

#### Blueprint

- Create Blueprint classes
- Add variables and functions
- Add, remove, move, configure, and reconstruct graph nodes
- Create and configure Blueprint comment boxes
- Connect pins, disconnect pins, autowire exec paths, and set pin defaults
- Use compose/layout/stabilize/validate-and-compile workflows

#### UMG / Widget Blueprint

- Create Widget Blueprints
- Inspect widget trees and graph summaries
- Add, remove, reparent, inspect, and patch widgets
- Patch slot properties
- Manage bindings and widget events
- Inspect and work with UMG animations

#### Runtime UI / Slate / Widget Reflector

- Capture live UI snapshots from the current editor/game session
- Run hit tests
- Inspect focus state
- Diff snapshots

Current limitation:

- This is for runtime introspection, debugging, and agent visibility. It is not a direct widget authoring layer.

### Materials and VFX

#### Material

- Create or prepare material assets through shared asset workflows
- Add material expressions
- Add reroute and named reroute declaration / usage expressions
- Connect expression outputs and material properties
- Configure expression properties
- Layout the graph and recompile

#### Niagara

- Create or clone systems
- Inspect systems, emitters, stacks, modules, renderers, and parameters
- Add or remove emitters, modules, and renderers
- Set module parameters and user parameters
- Apply templates and recipe-style helpers
- Spawn preview instances and run validation

Current limitation:

- The Niagara surface is already useful, but public messaging should still avoid claiming full editor-native parity for every possible stack/module authoring case.

### Animation and Cinematics

#### Animation Blueprint

- Create, summarize, preview, reparent, and compile Anim Blueprints
- Inspect graphs and state machines
- Add state machines, states, transitions, conduits, state aliases, and AnimGraph nodes
- Edit transition rules and graph nodes
- Use workflow helpers for layout, repair, stabilize, and validate/compile

Current limitation:

- Some `state_graph` selector parity edge cases are still being tightened, so keep public claims practical rather than absolute.

#### Anim Montage

- Create and summarize montage assets
- Add and remove sections
- Set next-section links
- Add and remove slot tracks and segments
- Add montage notifies and branching points
- Patch blend settings
- Preview play

#### Anim Notify / Anim Notify State

- Create Notify and NotifyState Blueprint assets
- Summarize, reparent, and compile them
- Continue authoring logic through shared generic Blueprint graph tools

#### PoseAsset

- Create PoseAssets from source animations
- Summarize pose, track, and curve content
- List contained poses
- Convert between full-pose and additive-pose space

#### BlendSpace

- Create BlendSpace and BlendSpace1D assets
- Summarize axis and sample layouts
- Patch axis properties
- Add, update, and remove samples

#### AimOffset

- Create AimOffset and AimOffset1D assets
- Summarize axis semantics and sample validity
- Patch axis properties
- Add, update, and remove additive samples
- Enforce additive consistency rules

#### Anim Sequence Slicing

- Summarize AnimSequence metadata
- Create new sliced sequences from a frame range
- Run batch slicing into multiple outputs

Current limitation:

- This domain is intentionally focused on slicing and trimming workflows, not full raw animation-track editing.

#### Control Rig

- Create and load Control Rig assets
- Inspect hierarchy and controls
- Get, set, batch-set, and reset control values
- Capture, apply, and mirror poses
- Read and set variables
- Compile and validate rigs
- Bind Control Rigs into Sequencer and edit keys there

#### Sequencer

- Create and load sequence assets
- Inspect bindings, tracks, sections, channels, and linked objects
- Add and remove bindings, tracks, and sections
- Patch sections
- Set, remove, and bulk set keys
- Use compose-style orchestration helpers

Current limitation:

- Current public coverage is strongest on the supported section/channel models already exercised by tests and smoke scenarios.

### Data and World Authoring

#### Data Table

- Create DataTables with explicit row struct selection
- Summarize table shape and row counts
- Describe row schema
- List, get, add, patch, upsert, rename, and remove rows
- Export CSV and JSON

Current limitation:

- Import CSV/JSON and bulk patch flows are not part of the current public release surface yet.

#### World / Actors

- Spawn and manage actors in the current level
- Move, attach, detach, duplicate, and tag actors
- Add, remove, and patch components
- Use selection, validation, and build-oriented helpers

#### PCG

- Create and configure PCG graphs
- Bind PCG graphs to components
- Generate content
- Inspect status
- Bake and unbake outputs

#### Landscape / Foliage

- Create landscapes
- Inspect landscape state, layers, and preview material setup
- Apply sculpt stamps
- Apply paint stamps
- Add foliage instances
- Clear foliage instances
- Work with rollback-aware recent authoring flows

Current limitation:

- This is a focused AI-friendly stamp/scatter surface. It should not be described as total parity with every Landscape or Foliage editor mode.

## Recommended Public Summary

If you need one short public summary, use this:

> GameDev MCP Plugin currently has the strongest public authoring coverage in Blueprint, UMG, materials, animation/cinematics, data tables, and world workflows, plus focused landscape/foliage support and live runtime UI inspection.

## Related Docs

- For setup instructions by client, see [CLIENT_SETUP.md](./CLIENT_SETUP.md).
- For current limitations and caveats, see [KNOWN_ISSUES.md](./KNOWN_ISSUES.md).
