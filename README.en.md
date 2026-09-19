# Guided Discovery Interview

[简体中文](README.md) | [English](README.en.md)

An Agent Skill that uses professional deep-interview capabilities in service of the interviewee's self-discovery. It starts from concrete experience and uses sustained probing, judgment, counterevidence, and perspective shifts to help users form a fuller and more accurate understanding of themselves.

It is not a fixed questionnaire, nor does it dress up plain language as grand theory. It focuses on whether:

- each probe follows the user's latest answer;
- interpretations are grounded in concrete events and observable behavior;
- the Agent makes clear judgments while remaining open to correction;
- the conversation reveals an actual change in understanding, not merely better wording;
- side branches are tracked without losing the main thread;
- probing stops once enough relevant evidence has been obtained.

When an agreed interview topic is complete, the Skill delivers an evidence-grounded, correctable final report by default, with a small number of high-density action and pitfall recommendations when the evidence supports them.

> Current version: `v0.1.1`. This is a public experimental release awaiting real-world testing, not a finished product.

## Use cases

- Review work experience and uncover professional abilities that have become habitual and invisible.
- Distill tacit knowledge from projects, journals, conversations, and lived events.
- Clarify a broad claim such as “I am bad at selling.”
- Elicit the cues, goals, options, and uncertainty behind a professional decision.
- Identify value the user may underestimate by looking through a customer lens.
- Preserve the main thread, shifts in understanding, and unresolved questions across long conversations.

Not intended for: quick text summaries, one-off advice, or situations where the user does not want sustained questioning and challenge.

## Design

```text
guided-discovery-interview/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── probing-toolkit.md
    ├── final-interview-report.md
    └── session-ledger.md
```

- `SKILL.md`: interview stance, core loop, standards of judgment, main-thread control, and action boundaries.
- `references/probing-toolkit.md`: probe selection using DICE, laddered probing, critical-decision elicitation, and anti-leading checks.
- `references/final-interview-report.md`: the client-facing report for a completed topic, covering evidence, changes in understanding, blind spots, and focused action guidance.
- `references/session-ledger.md`: continuity state for paused or multi-session interviews, while keeping summaries distinct from raw evidence.
- `agents/openai.yaml`: display metadata and default invocation for Codex.

See [SKILL.md](SKILL.md) for the complete operating instructions.

## Installation

| Host | User-level directory | Explicit invocation | Current validation status |
| --- | --- | --- | --- |
| Codex local | `~/.agents/skills/guided-discovery-interview/` | `$guided-discovery-interview` | Paths and syntax aligned with official docs; host behavior not yet tested |
| Claude Code local | `~/.claude/skills/guided-discovery-interview/` | `/guided-discovery-interview` | Paths and syntax aligned with official docs; host behavior not yet tested |
| Other Agents | Follow the host's documentation | Host-specific | Not verified |

Directory and invocation syntax follow the [OpenAI Codex Skills documentation](https://developers.openai.com/zh-Hans/docs/build-skills) and [Claude Code Skills documentation](https://code.claude.com/docs/en/skills).

Confirm that the destination does not already exist before installing. If it does, inspect its source, version, and uncommitted changes instead of overwriting it. The commands below only clone the Skill; they do not read journals, project files, or conversation history.

### Codex

```bash
git clone https://github.com/yangliangyl/guided-discovery-interview.git \
  ~/.agents/skills/guided-discovery-interview
```

### Claude Code

```bash
git clone https://github.com/yangliangyl/guided-discovery-interview.git \
  ~/.claude/skills/guided-discovery-interview
```

If you use several Agent frameworks, consider keeping one physical copy and exposing it to each framework with symbolic links. This prevents multiple versions of the Skill from drifting apart.

## Permissions and output

- An ordinary interview can remain inside the conversation and does not require local file writes.
- The Agent should read projects, journals, or history only after you authorize the specific material; access to one directory does not imply access to others.
- Saving a continuation ledger when pausing requires separate authorization. When an agreed topic is complete, the Skill produces a correctable interview report under its existing rules.
- This is a reflection and interviewing tool, not a mental-health diagnostic tool, and provisional interpretations are not authoritative conclusions.

## Usage examples

Direct invocation in Codex:

```text
Use $guided-discovery-interview to interview me.
Begin with concrete experience, ask one main question at a time, do not rush to summarize, and make judgments that I can correct.
```

With a topic:

```text
Use $guided-discovery-interview to help me uncover methods and abilities I have developed in data analysis but may not recognize clearly.
```

With source material:

```text
Use $guided-discovery-interview to interview me using the project files and journals I authorize you to read.
Treat the files as evidence rather than merely summarizing them.
```

In Claude Code, invoke `/guided-discovery-interview`; the rest of the instruction can stay the same.

## Inspectable examples

- [Minimal synthetic interview](examples/minimal-interview.md) shows a short path from a broad claim to a concrete event, counterexample, and bounded conclusion.
- [Human evaluation scenarios](evals/scenarios.md) and the [manual scoring rubric](evals/rubric.md) define expected, disqualifying, and observable grading behavior. They are proposed evaluation specifications, not evidence that a model has passed them.

## How to test it

Bring one real question that still feels unclear and complete a sustained interview. Afterward, report specific moments rather than giving a general rating:

- Which probe helped you articulate something you had not noticed before?
- Where did the Agent impose an explanation or sound falsely profound?
- Where did it probe too far, become repetitive, or lose the main thread?
- Which judgment changed your understanding, and which merely improved the wording?
- Did you leave with a more accurate judgment or an observable next test?

Real examples are welcome through GitHub Issues. Remove personal information, company data, and sensitive material; include only the minimum context needed to understand the failure or useful behavior.

## Iteration principles

- Prefer narrow corrections based on real failures over rules for imagined edge cases.
- Use professional interview methods to strengthen probing, not to replace judgment, counterevidence, or main-thread control.
- Do not treat likes, praise, or “it felt good” as evidence of cognitive change.
- Preserve uncertainty and do not generalize one person's experience into a universal rule.

## License

[MIT](LICENSE)
