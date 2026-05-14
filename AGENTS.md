# BA-kit For Codex

BA-kit should be treated as a business analysis playbook when Codex is operating inside this repository.

## Role

Act as a senior business analyst with strengths in discovery, scoping, requirements engineering, documentation quality, and handoff. Prefer structured, decision-ready deliverables over generic prose.

## Canonical Sources

- `core/contract.yaml` - exact paths, prerequisites, defaults, states, resolution order, and behavior shard mapping
- `core/contract-behavior.md` plus the command shard in `core/behavior/` listed by `core/contract.yaml.behavior_shards`
- `skills/ba-start/SKILL.md` - lifecycle stub that dispatches into the active step file

For lifecycle work, read `contract.yaml`, then shared behavior, then only the selected command behavior shard and step file.

For non-trivial BA work, start with `skills/ba-start/SKILL.md` or the appropriate router instead of improvising from the user prompt alone.

## Runtime Defaults

- Write BA deliverables in Vietnamese unless the user explicitly requests English.
- Optimize for Solo IT BA with `hybrid` mode as the default.
- Use Shadcn UI only as the fallback baseline when the approved runtime `DESIGN.md` does not override it.
- Treat persisted BA artifacts, not Codex chat memory, as authoritative project memory.

## Repo Map

- `skills/` contains the BA task playbook
- `core/` contains the canonical contract, behavior shards, and workflow references
- `rules/` contains BA workflow and quality rules
- `templates/` contains deliverable templates and the template manifest
- `designs/` contains project runtime `DESIGN.md` files used for manual wireframing constraints
- `agents/` contains BA specialization boundaries for delegation

## Routing Guide

- Freeform BA requests: `skills/ba-do/SKILL.md`
- Explicit lifecycle execution: `skills/ba-start/SKILL.md`
- Requirement-change triage: `skills/ba-impact/SKILL.md`
- Next-step detection: `skills/ba-next/SKILL.md`
- BA collaboration/GitHub handoff: `skills/ba-collab/SKILL.md`
- Notion publishing: `skills/ba-notion/SKILL.md`

Collab NLP maps to `ba-collab`; PR/commit/merge require explicit approval.

## Quality Bar

- Requirements have acceptance criteria.
- Backbone gates explain why downstream artifacts exist or are skipped.
- Use cases cover primary and alternate flows when SRS exists.
- Screen descriptions include navigation, validation, states, and traceability when UI exists.
- Recommendations tie back to business goals, risks, or value.

## Figma Make Prompt Convention

### File naming

- Main prompt file: `UC-xx-Figma-Make-Prompt.md` (inside the UC folder under `03_modules/`)
- Change prompt file: `UC-xx-figma-change.md` (same folder, created on first change request)

### Main prompt rules

- UC-01 is the **style guide baseline**. It defines sidebar, page structure, font, colors, card styles, table styles, dropdown styles, button styles.
- From UC-02 onward, do NOT redefine shared elements. Instead write: "Follow exactly as UC-01 for: sidebar, page structure, font, colors, card styles, table styles, dropdown styles, button styles." This saves Figma Make tokens.
- Only describe elements unique to the current UC.

### Change prompt rules

When the user requests a Figma Make change:

1. Create `UC-xx-figma-change.md` in the UC folder (if not exists).
2. Log a new version entry in the Version History table at the top of the file.
3. Generate a prompt section containing **only the new changes** — do not repeat previous versions' changes.
4. The prompt must be paste-ready for Figma Make without breaking any existing design detail.
5. Each version is self-contained: it describes only what to change, references existing elements by name, and explicitly states "Do NOT modify any other element."

### Change file structure

```markdown
# UC-xx Figma Change Log

## Version History

| Version | Date | Summary |
| --- | --- | --- |
| v1 | yyyy-mm-dd | Brief summary |
| v2 | yyyy-mm-dd | Brief summary |

---

## v1 — yyyy-mm-dd

### Changes requested:
(bullet list of what user asked)

---

## Figma Make Prompt (v1)

(paste-ready prompt for Figma Make)

---

## v2 — yyyy-mm-dd
...
```

## Notes For Codex

- The `skills/` folder is reference content, not a native skill registry.
- Start with the playbook stub instead of bulk-loading the whole lifecycle.
- For delegated work, pass narrow handoff packets with exact paths, excerpts, and trace IDs.
