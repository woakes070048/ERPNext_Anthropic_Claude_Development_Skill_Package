# DECISIONS - ERPNext Skills Package

> Architectural and design decisions log.
> All significant decisions documented with rationale for traceability.

---

## Decision Log

### D-001: English-Only Skills (No Bilingual Content)

**Date**: 2026-01-17 (Amendment 6)
**Status**: ACCEPTED
**Context**: Initial plan called for 56 skills (28 × 2 languages: NL + EN).
**Decision**: Create only 28 English-only skills. Eliminate all Dutch versions.
**Rationale**: Analysis of Anthropic's skill library showed no multilingual skills. Skills are instructions for Claude, not end users. Claude reads English instructions and responds in any language. 50% reduction in deliverables without loss of capability.
**Impact**: Skills reduced from 56 to 28 folders.

---

### D-002: Directory Structure — Anthropic Tooling Compliance

**Date**: 2026-01-17 (Amendment 5)
**Status**: ACCEPTED
**Context**: Original structure with NL/EN subfolders was NOT compatible with Anthropic's `package_skill.py`.
**Decision**: SKILL.md must be directly in skill folder root, never in subfolders. Naming: `erpnext-{type}-{name}` without language suffix. Reference files in `references/` subfolder.
**Rationale**: Official tooling expects `skill_path / "SKILL.md"` in root. Compliance enables official packaging and distribution.
**Impact**: Full directory restructure during mid-project.

---

### D-003: 28 Skills Across 5 Categories

**Date**: 2026-01-15 (Masterplan v2)
**Status**: ACCEPTED
**Context**: Research phase identified complete coverage requirements for ERPNext/Frappe.
**Decision**: 28 skills total — 8 syntax, 3 core, 8 implementation, 7 error handling, 2 agents.
**Rationale**: Research-driven approach identified these as complete API coverage. One skill per scripting mechanism.
**Impact**: Defines full project scope.

---

### D-004: Phase Splitting Based on Content Complexity

**Date**: 2026-01-13 (Amendment: Fase Opsplitsingen)
**Status**: ACCEPTED
**Context**: Claude's context window caused overflow during complex phases.
**Decision**: Split phases when: reference files > 4-5, sections > 8-10, or research doc > 700 lines.
**Rationale**: One-shot execution principle requires completable phases within single conversation.
**Impact**: Phases 2.6, 2.7, 2.8 split into sub-phases.

---

### D-005: Research-First Methodology

**Date**: 2026-01-12 (Project inception)
**Status**: ACCEPTED
**Context**: Creating deterministic skills requires deep understanding of the technology.
**Decision**: Mandatory deep research phase BEFORE any skill creation. 13 research documents covering all mechanisms.
**Rationale**: "You cannot create deterministic skills for something you don't deeply understand."
**Impact**: Phase 1 produced 13 comprehensive research documents before any skill work began.

---

### D-006: Deterministic Content Only

**Date**: 2026-01-12 (Masterplan v2)
**Status**: ACCEPTED
**Context**: AI-generated code often contains assumptions and vague suggestions.
**Decision**: Only verifiable facts from official sources. Clear instructions (ALWAYS/NEVER, not "consider/might/should"). Version-explicit markers (v14/v15/v16).
**Rationale**: Enables one-shot correct code generation. Eliminates ambiguity.
**Impact**: All skills follow strict deterministic language rules.

---

### D-007: V16 Compatibility Added to Scope

**Date**: 2026-01-17 (Masterplan v3)
**Status**: ACCEPTED
**Context**: ERPNext/Frappe v16 released during project development.
**Decision**: Support v14, v15, AND v16. Document breaking changes across all affected skills.
**Rationale**: Market requirement for version flexibility. Explicit version markers prevent compatibility issues.
**Impact**: 9 skills required V16-specific updates.

---

### D-008: Server Script Sandbox as Core Design Constraint

**Date**: 2026-01-13 (Research Phase)
**Status**: ACCEPTED
**Context**: Discovered that Server Scripts run in RestrictedPython sandbox with ALL import statements blocked.
**Decision**: This becomes the #1 design principle for code generation guidance. All server script examples must use `frappe` namespace exclusively.
**Rationale**: Root cause of ~80% of AI-generated ERPNext failures. Critical for deterministic code generation.
**Impact**: Shapes decision trees, error handling skills, and code examples across multiple skills.

---

### D-009: ROADMAP.md as Single Source of Truth

**Date**: 2026-01-14 (Mid-project lesson)
**Status**: ACCEPTED
**Context**: Claude's filesystem resets between sessions. Status tracked in multiple places caused inconsistency.
**Decision**: ROADMAP.md is the ONLY place for project status tracking. Never hardcode status elsewhere.
**Rationale**: GitHub is persistent. Prevents inconsistency between multiple status documents.
**Impact**: All phase completions update ROADMAP.md immediately.

---

### D-010: Skill Naming Convention

**Date**: 2026-01-17 (Amendment 5/6)
**Status**: ACCEPTED
**Context**: Need consistent, tooling-compatible naming across 28 skills.
**Decision**: Pattern: `erpnext-{type}-{name}`, kebab-case, max 64 characters. Types: syntax, core, impl, errors, agents.
**Rationale**: Follows Anthropic conventions. Validated by `quick_validate.py`.
**Impact**: All 28 skills follow this pattern.

---

### D-011: Progressive Disclosure Skill Structure

**Date**: 2026-01-15 (Masterplan v2)
**Status**: ACCEPTED
**Context**: Skills need both quick reference and comprehensive detail.
**Decision**: Lean SKILL.md (< 500 lines) with quick reference and decision trees. Detailed content in `references/` subfolder.
**Rationale**: Balances quick access with comprehensive detail. Follows Anthropic convention.
**Impact**: Every skill has SKILL.md + references/ structure.

---

### D-012: Completion Level Definitions

**Date**: 2026-01-18 (Masterplan v4 — Kritische Reflectie)
**Status**: ACCEPTED
**Context**: "28 skills complete" was ambiguous — structurally complete ≠ functionally tested.
**Decision**: Define 5 completion levels: (1) Structural, (2) Content Correct, (3) Technically Validated, (4) Functionally Tested, (5) Production Ready.
**Rationale**: Prevents false completion claims. Clarity about project maturity.
**Impact**: Package currently at Level 3. Level 4-5 planned for Phase 8.

---

### D-013: One-Shot Execution Principle

**Date**: 2026-01-12 (Project inception)
**Status**: ACCEPTED
**Context**: Claude context window limitations and session resets.
**Decision**: Each phase/skill must be completable in a single conversation without iteration. No "proof-of-concepts" or "we'll fix it later."
**Rationale**: Forces quality planning upfront. Prevents context loss between sessions.
**Impact**: Phase splitting (D-004) is a direct consequence of this principle.

---

### D-014: YAML Description Format — Folded Block Scalar

**Date**: 2026-01-18 (Masterplan v4 / Agent Skills migration)
**Status**: ACCEPTED
**Context**: 18 of 28 skills initially used quoted strings for YAML descriptions, causing validation issues.
**Decision**: All YAML descriptions MUST use folded block scalar (`>`) format. Never quoted strings.
**Rationale**: Consistent format, avoids YAML parser edge cases with colons and special characters.
**Impact**: All 28 skills migrated to `>` format.

---

### D-015: Topic Research — Inline via WebFetch

**Date**: 2026-01-15 (Implicit decision)
**Status**: ACCEPTED
**Context**: Workflow methodology expects `docs/research/topic-research/` directory with per-skill research.
**Decision**: Topic-specific research was conducted inline during skill creation phases, not as separate documents. The 13 research documents in `docs/research/` serve as both vooronderzoek and topic research.
**Rationale**: The 13 comprehensive research documents (500-1000+ lines each) already covered topic-level detail. Separate topic-research documents would have been redundant.
**Impact**: No `docs/research/topic-research/` directory exists. This is by design, not omission.
