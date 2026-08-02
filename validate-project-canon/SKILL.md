---
name: validate-project-canon
description: Validate dialogue, objectives, naming, state flags, and implementation details against a project's canon, glossary, and design guidelines. Raise contradictions, record unresolved decisions, and ask before editing authoritative design documents. Use when revising narrative content, quest logic, character names, terminology, or checking canon drift.
---

# Validate Project Canon

A canon and consistency guard for narrative games and other story-heavy projects.

Use this skill after editing dialogue data, narration, objectives, room or scene files, quest logic, or design documents.

## First-run setup

Before validating a project for the first time, ask the user where the following live:

1. **Canonical glossary / terminology file**
2. **Current project context or story bible**
3. **Design guidelines**
4. **Implemented runtime data and scene files**
5. **Chapter / quest / feature design drafts**
6. **Contradiction log**, if one already exists

Do not assume filenames or folder structure.

Once the user identifies them, treat those locations as the project's validation sources for the current task.

## Authority

Establish a clear source order with the user. A useful default is:

1. **Glossary / canon reference** - names, terms, item IDs, established facts
2. **Current project context / story bible** - current scope, narrative rules, player-facing language
3. **Design guidelines** - dialogue, quest, UX, and structural rules
4. **Implemented data and scenes** - current runtime behaviour
5. **Design drafts** - intent and planned changes

If two sources conflict, do not silently choose unless the authority order already resolves it.

Record the conflict and ask the user when necessary.

## Validation checklist

Adapt this checklist to the project.

### Naming and terminology

- [ ] Character display names match the canonical glossary
- [ ] Dialogue speaker IDs and display names are consistent
- [ ] The same concept is not referred to by multiple conflicting terms
- [ ] Internal IDs follow the project's naming convention
- [ ] Player-facing names are not replaced by implementation-only names

### Objectives and quest state

- [ ] Objectives activate only after the player can reasonably know what they say
- [ ] Objective text matches the intended narrative voice
- [ ] Objective chains hand off correctly
- [ ] No objective references removed or obsolete state flags
- [ ] State changes occur in the intended narrative order
- [ ] Optional and deferred branches remain optional unless explicitly resolved

### Dialogue

- [ ] Dialogue hubs follow the project's option-count rules
- [ ] One-time topics are marked correctly
- [ ] Conditional topics appear only when their prerequisites are known
- [ ] Dialogue does not reveal information before the player has learned it
- [ ] All referenced dialogue or narration IDs exist
- [ ] Character knowledge remains consistent across scenes

### Flags and side effects

- [ ] State flags have one clear meaning
- [ ] Duplicate systems do not set contradictory values for the same story beat
- [ ] Name-known, location-known, clue-known, and similar knowledge flags fire at the correct moment
- [ ] Removed flags are not still referenced
- [ ] Runtime side effects match the intended narrative consequence

### Canon drift

- [ ] Search for deprecated character names
- [ ] Search for renamed locations, factions, items, or mechanics
- [ ] Search for conflicting terminology
- [ ] Search for old quest or chapter names
- [ ] Check recent implementation changes against authoritative docs

## Contradiction workflow

1. **Detect** - search code, data, and docs for conflicting terms, facts, state order, or behaviour
2. **Record** - add the contradiction to the project's contradiction log
3. **Ask** - if authority does not resolve it, ask the user before changing canon
4. **Resolve** - update implementation and canonical references together
5. **Close** - mark the contradiction resolved and record the chosen decision

A contradiction entry should include:

- ID
- Short description
- Conflicting sources
- Current status
- Decision, once resolved
- Files that need updating

## Ask before editing

Ask the user before changing files they identify as authoritative, such as:

- glossary / terminology documents
- story bible or project context
- chapter or quest design documents
- master narrative plans

Implementation files may be safe to edit directly when carrying out an already-approved change, but follow the user's project rules.

## Search strategy

Use project-wide search before changing canon-sensitive content.

Typical searches include:

```bash
# Deprecated names
rg "OldName|OldLocation" .

# Objective or state drift
rg "old_flag|new_flag|quest_stage" data scripts scenes docs

# Conflicting terminology
rg -i "term_a|term_b" data docs scenes
```

Adjust paths and search terms to the project.

## Behaviour rules

- Do not invent canon to resolve missing information
- Do not silently rewrite authoritative documents
- Do not treat implementation accidents as canon unless the user confirms them
- Prefer explicit contradictions over hidden assumptions
- When uncertain, show the conflicting evidence and ask
- Keep player-facing terminology separate from internal IDs
- Preserve deferred decisions as deferred

## Output format

When reporting validation results, group findings into:

### Confirmed
Items consistent across authoritative sources and implementation.

### Contradictions
Conflicts that need a decision.

### Drift
Stale names, flags, IDs, or terminology that can be corrected without changing canon.

### Questions
Cases where the sources do not provide enough information to decide safely.
