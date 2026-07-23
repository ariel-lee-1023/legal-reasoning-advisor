# Legal Reasoning Advisor

An [Agent Skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) for diagnosing and clarifying the logic of legal arguments.

It sorts briefs, judgments, student notes, law-review claims, exam answers, statutory puzzles, and client problems into their **load-bearing moves** — factual, classificatory, precedent-application, and policy — tests each move by its own standard, finds the joint the conclusion actually turns on, and states what follows, on what conditions, and what stays open.

## What it is for

Most legal-reasoning work is not archival. It is working *inside* an argument while it is still being made: a brief you are drafting or answering, a note whose joints are still being tested, a client problem where the question is which way the law cuts. That live, diagnostic work is the centre of this skill.

Full precedent digestion — ratio/dicta separation, Hohfeldian relation-mapping, scope conditions, a citable record — is preserved here as **one tool among several**, invoked when a specific holding needs digesting, not run by reflex on every input.

## The governing spirit

The skill reasons the way the common law actually reasons, rather than imposing a top-down theory of rules:

- **Classifications are earned from the materials.** A category is legitimate only to the extent courts have actually sorted comparable fact-settings into it. Do not define the category and deduce the answer.
- **Materiality is a finding, not a definition.** Which facts matter is settled by what past courts treated as operative.
- **Name what is open.** Where the categories or precedents run out, say so plainly instead of manufacturing closure.
- **Law is a trained practice, not general reason** (Coke's "artificial reason").

## The four moves

| Move | What it asserts | Characteristic failure |
|---|---|---|
| Empirical / factual | What happened; what the record shows | A contested fact smuggled in as settled |
| Definitional / classificatory | Which legal category something falls in; which relation holds | An imposed definition dressed as an earned category; a word doing several jobs |
| Precedent application | That a decided case governs, on materially similar facts | Dictum treated as holding; wrong level of generality; an ignored distinction |
| Policy / normative | What result the law should reach | Speculative consequences asserted as fact; policy hiding a gap |

A single sentence often fuses several. *"The defendant, as owner, had the right to exclude"* packs a classificatory move, a relational one, and an unstated factual predicate. The fusions are where arguments hide their work.

## Repository structure

```
legal-reasoning-advisor/
├── SKILL.md                          # the skill: workflow, four moves, tool routing
├── references/
│   ├── move-taxonomy.md              # the diagnostic core; recognition cues, worked diagnoses
│   ├── common-law-method.md          # the governing stance (Coke)
│   ├── hohfeld-toolkit.md            # right / duty / privilege / power / immunity
│   ├── precedent-method.md           # how precedent actually constrains (Duxbury)
│   └── precedent-extraction.md       # full judgment-digestion pipeline (Stage-4 tool)
├── README.md
├── CHANGELOG.md
├── LICENSE
└── .gitignore
```

`SKILL.md` is loaded first; the files in `references/` are read on demand, only when a particular tangle calls for them.

## Installation

### Claude Code (personal — available across all projects)

```bash
git clone https://github.com/ariel-lee-1023/legal-reasoning-advisor.git \
  ~/.claude/skills/legal-reasoning-advisor
```

### Claude Code (project-scoped — committed with the repo that uses it)

```bash
git clone https://github.com/ariel-lee-1023/legal-reasoning-advisor.git \
  .claude/skills/legal-reasoning-advisor
```

The path must be `<skills-dir>/legal-reasoning-advisor/SKILL.md` — one level, not nested deeper. Claude discovers the skill automatically from its frontmatter and loads the body when the description matches what you are asking about.

### Claude.ai and the API

Custom skills can also be used on Claude.ai and through the Claude API. Because upload steps and limits change, follow the current instructions in the [Agent Skills documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) rather than a snapshot here.

## Usage

No command is needed; the skill triggers on the shape of the request. Representative prompts:

- "Sort the logic of this brief and tell me which step it really rides on."
- "Here's a passage from my note — where is it cheating?"
- "Is the 'right' in this argument a claim-right or a privilege?"
- "Does *X v. Y* actually hold what this paragraph says it holds?"
- "Digest this judgment into a case note with scope conditions." *(invokes the extraction pipeline)*
- "Build the strongest counter-argument from the same map."

The usual deliverable is a sorted map plus a clarified conclusion, inline. A file is produced only when you want one.

## Sources

The reference files synthesize, in the author's own words:

- Sir Edward Coke, *The First Part of the Institutes of the Laws of England* and *The Reports*, in *The Selected Writings and Speeches of Sir Edward Coke*, ed. Steve Sheppard (Liberty Fund, 2003).
- Wesley N. Hohfeld, "Some Fundamental Legal Conceptions as Applied in Judicial Reasoning," 23 Yale L.J. 16 (1913). *(Public domain; a small number of signature passages are quoted verbatim and cited by location.)*
- Neil Duxbury, *The Nature and Authority of Precedent* (Cambridge University Press, 2008).

## Disclaimer

This is a reasoning aid, not legal advice, and it does not create a lawyer–client relationship. It is designed to make the structure of an argument visible — including where the argument runs out — not to tell you the answer. Verify every authority against the primary sources for your jurisdiction, and have a qualified lawyer confirm anything that matters.

## Contributing

Issues and pull requests are welcome. The most useful contributions are worked diagnoses that expose a failure mode the taxonomy does not yet catch, and corrections where a reference file overstates a contested proposition. Please keep additions consistent with the governing stance: classifications earned from materials, uncertainty marked rather than smoothed.

## License

MIT © 2026 Ariel Lee. [See LICENSE](LICENSE).

This license covers the original text in this repository. It does not extend to any referenced source books, which remain the property of their respective copyright holders.

