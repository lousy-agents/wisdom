---
source_url: "internal://teams-discussion/agentic-coding-harness-instructions"
type: notes
title: "Agentic Coding Harness Instructions — Aggregated Mental Model"
captured_at: 2026-06-28T21:23:36+00:00
author: "zpratt"
contributor: "zpratt"
---

# Agentic Coding Harness Instructions — Aggregated Mental Model

Aggregation of Teams discussions (grounded where possible) plus broader ecosystem context to fill gaps consistently. Practical, opinionated, and aligned with how it was explained — not generic docs.

## Core idea

> **The model is not the product — the harness is.**

A coding agent is:

```
Agent = Model + Harness
```

* The **model** generates code
* The **harness** defines:
  * what it knows
  * what it is allowed to do
  * how it behaves
  * how it composes instructions

## What "coding harness instructions" actually are

Coding harness instructions are **persistent, repo-level configuration files** that every agent reads before doing work. Examples:

* `AGENTS.md` → Codex, cross-tool standard
* `CLAUDE.md` → Claude Code
* `.github/copilot-instructions.md` → Copilot
* `.github/instructions/*.instructions.md` → scoped Copilot rules

These files:

* act as **agent-facing operating manuals**
* provide **persistent context** (since models start stateless every session)
* define **rules, architecture, workflows, and constraints**

## Key insight: Harness differences matter more than models

* Harnesses are **not just thin wrappers**
* Differences in behavior come from:
  * instruction loading
  * composition model
  * scoping system
  * runtime behavior

## Instruction models by harness

### 1. GitHub Copilot → Glob-scoped instruction model

**Mechanism**

* Uses `.github/copilot-instructions.md` (global) and `.github/instructions/*.instructions.md` (scoped)
* Scoped via `applyTo`

**Observation**

* `applyTo` is unique to Copilot
* Copilot partially supports `AGENTS.md` but does not consistently apply it (e.g., not during code review)

**Mental model**

```
Instructions = global + glob-scoped overlays
```

**Strengths**: fine-grained targeting (by file patterns); familiar for GitHub-native workflows.
**Limitations**: fragmented instruction sources; weaker composition model.

### 2. Claude Code → Hierarchical composition model

**Mechanism**

* Reads `CLAUDE.md` (global + repo + subdirs), optionally `AGENTS.md` fallback
* Merges instructions recursively

**Behavior**: all relevant instruction files are concatenated and hierarchically layered.

**Observation**: strong support for `@` imports and nested instruction files. Designed for instruction composition, not targeting.

**Mental model**

```
Instructions = layered composition (root → directory → local)
```

**Key property**: encourages modular rules; avoids monolithic files.

### 3. Codex → AGENTS.md-first composition model

**Mechanism**

* Primary file `AGENTS.md`
* Loads global → project → nested directories; later files override earlier ones

**Observation**: similar to Claude in philosophy (hierarchical composition, nested instruction model), but likely weaker support for `@` imports.

**Mental model**

```
Instructions = ordered merge chain (global → repo → local overrides)
```

### 4. Hermes → First-match model

**Behavior**: no `applyTo`, no `@` imports; uses "first match wins".

**Mental model**

```
Instructions = first applicable rule (no composition)
```

**Implication**: less expressive; harder to build scalable systems.

## Cross-harness comparison

| Capability | Copilot | Claude | Codex | Hermes |
| --- | --- | --- | --- | --- |
| Instruction model | Glob-based | Hierarchical | Hierarchical | First-match |
| `applyTo` | yes | no | no | no |
| `@` imports | yes | yes | no | no |
| Nested instructions | partial | yes | yes | no |
| AGENTS.md | partial | fallback | primary | no |
| Composition | Weak | Strong | Strong | None |

## Most important principle

> **Prefer instruction composition over monolithic instruction files**

* Large single files create confusion, contradictions, poor performance
* Better approach:

```
Break instructions into:
- small, focused files
- layered by directory
- composed at runtime
```

This aligns with broader guidance: agents load instructions every request, so large files waste context; nested files allow local overrides without duplication.

## Canonical structure

### Single source of truth

```
AGENTS.md → canonical shared contract
```

Then add per-harness adapters:

```
.github/copilot-instructions.md
CLAUDE.md
.github/instructions/*.instructions.md
```

Goal:

> **One set of rules, multiple harness adapters**

## Instruction layering pattern

```
Global (user-level)
  ↓
Repo root (AGENTS.md / CLAUDE.md)
  ↓
Subdirectory overrides
  ↓
Task-specific prompts
```

Key rule:

> **Closer to the code = stronger authority**

## Rules vs prompts

* **Rules (persistent)**: AGENTS.md, CLAUDE.md, Copilot instructions; stable constraints
* **Prompts (ephemeral)**: task-specific instructions; should reference rules; not duplicated

```
Rules  = "how we work"
Prompt = "what to do right now"
```

## What belongs in instructions (checklist)

Keep these in instruction files:

* Build/test commands
* Architecture constraints
* Directory boundaries
* Coding standards
* Tooling preferences
* "Do not do" rules

Avoid:

* Task-specific directions
* Large narrative explanations
* Frequently changing content

## Anti-patterns

1. **Monolithic instruction files** — hard to maintain, poor composition
2. **Duplicate rules across harnesses** — causes drift, different agents behave differently
3. **Overloading Copilot instructions** — context limits → ignored rules
4. **Treating all harnesses the same** — they are fundamentally different systems

## Recommended approach

1. **Design for composition first** — optimize for Claude/Codex model; treat Copilot as adapter
2. **Keep instructions modular** — split by architecture, testing, conventions
3. **Normalize on AGENTS.md** — cross-tool compatibility; canonical contract
4. **Use harness-specific features only when needed** — e.g., `applyTo` only when Copilot needs it; `@` imports only where supported

## Final distilled takeaway

```
Copilot       = targeting problem   (applyTo, globbing)
Claude / Codex = composition problem (layering, merging)

Best systems:
  → design for composition
  → add targeting as a thin layer
```

## References

* aruniyer.github.io — agents-md instruction files
* deployhq.com — AI coding config files guide
* developers.openai.com — Codex AGENTS.md guide
* aihero.dev — a complete guide to AGENTS.md
