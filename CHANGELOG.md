# Changelog

All notable changes to this skill are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Because this is a prose skill rather than code, versioning is read as follows:

- **MAJOR** — the centre of gravity, workflow, or governing stance changes; existing prompts may be answered in a materially different shape.
- **MINOR** — a reference file is added, or new diagnostic material extends what the skill can catch.
- **PATCH** — corrections, clarifications, tightened wording, no behavioural change.

## [Unreleased]

## [1.0.0] — 2026-07-22

First public release.

### Added

- `SKILL.md` — the advisor: four-move taxonomy, five-stage workflow (frame → map → interrogate → find the joint → state the conclusion), tool-routing table, output register, anti-patterns.
- `references/move-taxonomy.md` — the diagnostic core. Recognition cues, standards of contest, and characteristic failures for each of the four moves; fusion-spotting; locating the load-bearing joint; three worked diagnoses (practice, scholarship, client problem).
- `references/common-law-method.md` — the governing stance, from Coke: artificial reason, earned classification, materiality as a finding, naming openness.
- `references/hohfeld-toolkit.md` — the relational drill and the catalogue of equivocations to catch, from Hohfeld (1913).
- `references/precedent-method.md` — precedent as rebuttable presumption rather than rule-machine, from Duxbury: ratio vs. dictum, material similarity, level of generality, the repertoire of moves, diagnostic checklist.
- `references/precedent-extraction.md` — the full judgment-digestion pipeline, output template, and optional JSON schema.

### Changed

- Supersedes and absorbs the earlier `precedent-engineer` skill. The centre of gravity moved from **archival extraction** to **live diagnosis of arguments in progress**; extraction survives as a Stage-4 tool invoked on request.
- Two common-law amendments applied throughout the inherited extraction pipeline: a clean ratio is no longer forced (candidates and blur are reported instead), and openness is recorded as a first-class output rather than an afterthought.

[Unreleased]: https://github.com/ariel-lee-1023/legal-reasoning-advisor/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/ariel-lee-1023/legal-reasoning-advisor/releases/tag/v1.0.0
