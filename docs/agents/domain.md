# Domain docs

Use a multi-context layout.

## Before exploring

Read the root `CONTEXT-MAP.md` and follow its links to the `CONTEXT.md`
files relevant to the task.

Read relevant ADRs in root `docs/adr/` for system-wide decisions.
Also read `docs/adr/` within each relevant context directory.

If the map does not yet exist, read any relevant `CONTEXT.md` files
that already exist.

If these files are absent, proceed silently. Do not flag their absence
or suggest creating them upfront. Domain-modeling creates them when
domain terms or decisions are resolved.

## Layout

- `CONTEXT-MAP.md` at the repo root maps domain contexts to their docs.
- Root `docs/adr/` contains system-wide decisions.
- Each context has its own `CONTEXT.md` and `docs/adr/`.

Contexts may live under `apps/`, `packages/`, or another directory
identified by the map. A workspace package does not automatically
need a separate domain context.

## Vocabulary

Use the terms defined in the relevant `CONTEXT.md` when naming concepts
in issues, proposals, hypotheses, and tests. Respect any synonyms the
glossary explicitly excludes.

If a needed concept is missing, reconsider whether it belongs in the
domain or note the gap for domain-modeling.

## ADR conflicts

If a proposal contradicts an existing ADR, identify the ADR and explain
why the decision should be reconsidered.
