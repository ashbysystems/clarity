# Clarity by Ashby

**Plain-language review of AI development work.** Clarity works in any language. Claude conducts reviews in your language automatically. This README is in English; visit [ashby.systems/clarity](https://ashby.systems/clarity) for other languages.

Clarity is a free, open-source plugin for Claude (Cowork and Claude Code) that translates what AI built into language a non-programmer can understand. It reviews sessions and projects, explains decisions, identifies risks, and gives you specific prompts for follow-up.

You build things with AI. Clarity helps you understand what was built and whether you should be worried about anything.

## What Clarity Does

1. Reads what Claude Code built, changed, or planned
2. Explains every change, decision, and dependency in plain language
3. Identifies risks and gaps with concrete consequences, not jargon
4. Tells you what is and is not tested
5. Gives you specific prompts to take into your next session
6. Teaches you one or two useful concepts along the way

Clarity does not judge code quality, suggest fixes, or tell you what to do. It translates and explains. You decide what happens next.

## Installation

### Claude Cowork (Desktop)

1. Download this repository (Code > Download ZIP, or clone it)
2. In Claude Cowork, go to Settings > Plugins > Upload Plugin
3. Select the `Clarity` folder
4. Clarity commands will appear in your command menu

### Claude Code (Terminal)

```bash
claude plugin install ashbysystems/clarity
```

Or install from a local directory:

```bash
claude plugin install ./path/to/Clarity
```

## Quick Start

1. Build something with Claude Code
2. Run `/clarity:explain` to understand something specific — a file, an error, or a concept
3. Run `/clarity:session` to understand what just happened
4. Or run `/clarity:project` to understand the whole project
5. Use the "What to Ask Claude Next" prompts in a new session

That is the full workflow. Your first review takes a few minutes. Project reviews take longer for large projects.

## Commands

| Command | What it does |
|---------|-------------|
| `/clarity:explain` | Explain one thing — a file, error, output, or concept |
| `/clarity:session` | Review what happened in the current session |
| `/clarity:project` | Review the full project |
| `/clarity:config` | Set where Clarity saves review files |
| `/clarity:help` | Show command reference |

## What Clarity Is Not

- **Not a code reviewer.** It does not judge whether code is good or bad.
- **Not a fixer.** It does not suggest or make code changes.
- **Not objective.** It is Claude reviewing Claude's work. It may miss things another reviewer would catch.
- **Not a substitute for a developer.** If something in a review concerns you, share it with a developer for a second opinion.

## Review Files

Reviews are saved as markdown files to your configured location (set via `/clarity:config`) or to a `clarity/` directory in your project. Session reviews are timestamped; project reviews are dated.

**An important note:** Clarity is Claude reviewing Claude's work. The reviews are best-effort translations, not authoritative audits. They are useful for understanding and asking better questions, not for making final safety or security determinations.

## Companion Plugin: Attest

Clarity explains what AI built. [Attest by Ashby](https://github.com/ashbysystems/attest) is the other half: a structured review workflow that surfaces questions about any AI-generated output, captures your decisions, and produces an auditable decision log. Different jobs. Same goal: keeping humans in control.

## Data Handling

All processing runs locally. No data is transmitted externally. Review files are stored in your configured save location. Apply your organisation's existing data handling and retention policies.

## Disclaimer

Clarity by Ashby translates AI development work into plain language. It does not assess code quality, security, or fitness for purpose. It does not provide technical, legal, or compliance advice. All explanations are best-effort. This is Claude reviewing Claude's work — treat it with appropriate scepticism.

## License

Apache 2.0. See [LICENSE](LICENSE).

## How Clarity Was Built

Clarity was designed by the Ashby team and built using Claude Code. The review methodology, explanation frameworks, and scope management rules are based on human experience explaining technical work to non-technical stakeholders. Claude was used as a development tool, not as a domain expert. All design decisions were made by humans.

## About Ashby

Ashby builds structured human oversight for AI operations. Clarity is our plain-language review plugin. Attest is our structured review workflow plugin. Requisite is our Article 14 (EU AI Act) compliance assessment tool.

Learn more at [ashby.systems](https://ashby.systems).
