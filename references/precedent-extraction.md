# Precedent Extraction — digesting one judgment (a tool, not the center)

This is the full extraction pipeline inherited from the earlier `precedent-engineer` skill, preserved intact and re-tasked as a **Stage-4 tool**. Invoke it when — and only when — the user wants a *specific judgment fully digested* into a citable, scope-marked, relation-mapped record: a case note, digest entry, precedent-database row, memo rule, or archival item. For "help me reason through this argument," you usually do **not** need this; you need the diagnosis in the main workflow. Do not run the full template on every case that comes up.

Two common-law amendments to the original pipeline (from `common-law-method.md` and `precedent-method.md`), applied throughout:
- **Do not force a clean ratio.** If ratio and dictum blur, say so and give the candidates; a defended split, not an assumed one.
- **Materiality is a finding.** Mark each material fact as express / implied / inferred, and record *which differences a later court could seize to distinguish*.
- **Mark openness.** Record what the decision leaves unresolved as a first-class output, not an afterthought.

---

## When to use vs. not

**Use when the request is:** "digest this case," "make a case note / digest entry / rule card," "extract the holding and scope," "map the relations in this judgment," "make this citable / machine-readable," "what is this case authority for," "turn this judgment into reusable guidance."

**Do not use for:** stress-testing an argument, finding a brief's weak joint, sorting the logic of a claim, answering a client problem, or explaining doctrine — those stay in the main diagnostic workflow. Extraction is archival; diagnosis is the center.

**Output:** produce the record as a file/artifact when the user wants something reusable; inline is fine for a quick single digest.

---

## Input contract

- **Ideal:** full judgment text; procedural posture; parties, court, date, jurisdiction; majority/concurrence/dissent separated; citations preserved; the target issue or doctrinal area; known subsequent treatment if chain-placement is wanted.
- **Minimum viable:** a case identifier (or provisional one); text enough to identify issue, material facts, conclusion, and reasoning; court level and jurisdiction *if precedential force is requested*.
- **If incomplete:** proceed only with explicit uncertainty markers. If only a headnote is supplied, mark all extraction as headnote-based and do not treat the headnote as the court's own ratio. If jurisdiction/hierarchy is absent, do not assert binding force — write "precedential force not determined from supplied materials."

---

## Pipeline

1. **Posture and issue.** Extract court, level, procedural posture, claim type, procedural vehicle, disposition, and the issue *actually decided*. Split multiple issues before extracting any rule; do not merge procedural, factual, and substantive issues.
2. **Material facts.** Identify the facts the court treated as operative; separate them from background narrative; mark materiality express / implied / inferred; note which facts a later court could use to distinguish.
3. **Conclusion and necessary reasoning.** State the disposition and the legal conclusion; isolate the reasoning necessary to it; separate the deciding majority's reasoning from concurrence, dissent, and background.
4. **Ratio vs. obiter.** Treat ratio as the proposition(s) tied to material facts and necessary to the disposition. Treat as obiter what is unnecessary, hypothetical, unargued, or beyond the decided issue — but record weighty dicta separately with a note on persuasive value (do not discard as worthless). If ratio and dicta blur, present candidates and mark the ambiguity. If independent grounds each support the outcome, list multiple rationes rather than discarding one.
5. **Hohfeld mapping** (see `hohfeld-toolkit.md`). For each operative legal consequence, classify the relation — right/duty, privilege/no-right, power/liability, immunity/disability. Do not use "right" generically. Preserve the court's original term in a note where the mapping is a translation.
6. **Who against whom.** For each relation: holder; bearer (specific party, class, official, body, or the world); the act, thing, event, or *legal change* at issue; the trigger; the defeater.
7. **Precedent-network position** (see `precedent-method.md`). For each visible authority, classify treatment: follows / distinguishes / limits / extends / departs / overrules / applies / analogizes / questions / reserves / leaves unresolved. Distinguish express from inferred treatment. Do not infer overruling from mere non-application. State authority force only after checking hierarchy, jurisdiction, and publication status.
8. **Scope conditions.** Jurisdictional, procedural, factual, institutional, temporal, remedial. Note the facts needed to extend and the facts that would support a distinction.
9. **Black-letter rule.** Compressed, conditional where possible: "Where [conditions], [legal consequence], unless [exception / defeater]." Only propositions supported by the judgment; no rhetoric.
10. **Comment.** Brief: why the rule follows from the material facts and holding; what it does *not* decide; authority limits; open questions. Subordinate to the rule.
11. **Illustrations (optional).** Short apply / does-not-apply fact patterns that track the stated scope; labelled derived applications, not holdings. Omit for archival purity if the user prefers.
12. **Confidence and uncertainty.** Separately for issue, material facts, holding, ratio, dicta classification, Hohfeld mapping, authority treatment, scope. Name the source of any uncertainty (incomplete text, ambiguous reasoning, fragmented opinions, missing metadata, uncertain hierarchy, conflicting authorities).

---

## Output template (Markdown)

```markdown
## Case Identifier
- Case name / Citation / Court / Jurisdiction / Date:
- Procedural posture:
- Source completeness:

## Issue
- Issue decided:
- Issue classification:
- Issues excluded / not reached:

## Material Facts
- Fact — Materiality (express/implied/inferred) — Function in rule — Distinguishable on?:

## Holding
- Disposition:
- Holding:
- Holding level: narrow / intermediate / broad

## Ratio
- Ratio proposition — Necessary to outcome (yes/no/uncertain) — Based on which material facts — Reasoning link — Confidence:
- (list multiple if independent grounds; mark blur where present)

## Obiter
- Statement — Reason classified obiter — Persuasive value:

## Hohfeld Mapping
| Relation | Holder | Right/Privilege/Power/Immunity | Correlative | Bearer | Object / Conduct / Legal change | Trigger | Defeater | Confidence |
|---|---|---|---|---|---|---|---|---|

## Precedent Network Position
- Followed / Distinguished / Limited / Extended / Departed / Overruled / Questioned / Left unresolved:
- Authority force — Hierarchy note:

## Scope Conditions
- Jurisdictional / Procedural / Factual / Institutional / Temporal / Remedial:

## Exceptions / Open Questions
- Exceptions — Open questions — Conflicts or tensions — Missing information:

## Black-Letter Rule
Where [conditions], [legal consequence], unless [exception / defeater].

## Comment
- Scope — Rationale — Limits — Relation to prior authorities — Uncertainty:

## Illustration (optional)
- Applies: facts / result / reason
- Does not apply: facts / result / reason

## Confidence Note
- Overall — Issue — Ratio — Hohfeld — Network — Principal uncertainty:
```

---

## Optional JSON schema

```json
{
  "case_identifier": {"case_name":"","citation":"","court":"","jurisdiction":"","date":"","procedural_posture":"","source_completeness":""},
  "issue": {"decided":"","classification":"","excluded_or_not_reached":[]},
  "material_facts": [{"fact":"","materiality":"express|implied|inferred","function_in_rule":"","distinguishable_on":""}],
  "holding": {"disposition":"","statement":"","level":"narrow|intermediate|broad"},
  "ratio": [{"proposition":"","necessary_to_outcome":"yes|no|uncertain","material_facts":[],"reasoning_link":"","blur":"","confidence":""}],
  "obiter": [{"statement":"","classification_reason":"","persuasive_value":""}],
  "hohfeld_mapping": [{"holder":"","relation":"right|privilege|power|immunity","correlative":"duty|no-right|liability|disability","bearer":"","object_or_change":"","trigger":"","defeater":"","original_term":"","confidence":""}],
  "precedent_network_position": {"followed":[],"distinguished":[],"limited":[],"extended":[],"departed_from":[],"overruled":[],"questioned":[],"left_unresolved":[],"authority_force":"","hierarchy_note":""},
  "scope_conditions": {"jurisdictional":"","procedural":"","factual":"","institutional":"","temporal":"","remedial":""},
  "exceptions_open_questions": {"exceptions":[],"open_questions":[],"conflicts_or_tensions":[],"missing_information":[]},
  "black_letter_rule": "",
  "comment": {"scope":"","rationale":"","limits":"","relation_to_prior_authorities":"","uncertainty_notes":""},
  "illustrations": [{"type":"applies|does_not_apply|uncertain","facts":"","result":"","reason":""}],
  "confidence_note": {"overall":"","issue":"","ratio":"","hohfeld_mapping":"","precedent_network":"","principal_uncertainty":""}
}
```

---

## Style and guardrails

Impersonal, neutral, compressed, citable; no rhetoric, no advocacy, no emotional characterization unless the court itself reasoned that way and it is material. Do not: treat all judicial language as holding; treat broad rhetoric as ratio without material-fact linkage; collapse relations into a generic "right"; assert binding force without hierarchy and jurisdiction; silently harmonize conflicting authorities; erase uncertainty to look clean; supply missing doctrine from memory when the task requires grounding in the supplied case. When the judgment's categories run out, mark the opening rather than inventing closure.

---

## Configurable choices (ask or default)

Narrow vs. broad holding (default: narrowest defensible, with broader formulations at lower confidence on request) · Hohfeld aggressiveness (default: map only where the relation type is reasonably clear) · single vs. multiple rules for multi-issue cases · fragmented-opinion handling (narrowest-ground vs. separate-opinion mapping vs. uncertainty-first) · persuasive-dicta as a separate field · authority-hierarchy from visible text only vs. external research (only if authorized) · illustrations always / on request / omitted · output format Markdown / JSON / YAML / table · confidence scale high-med-low / numeric / narrative · subsequent-treatment in scope only if supplied vs. researched on request · comparative-law mode for non-common-law judgments with modified precedent-force assumptions.
