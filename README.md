# Anti-Hallucinate Skills for Claude Code

> "Hallucinations are hard to anticipate, hard to catch, and the wrong answer often looks exactly like it could be the right one." — Anthropic

A set of behavioral guidelines to reduce AI hallucinations in Claude Code, derived from [Anthropic's official explanation](https://www.youtube.com/watch?v=005JLRt3gXI) of why AI models hallucinate and practical tactics to catch and prevent it.

## Why Hallucinations Happen

AI models work by predicting the next word based on patterns learned from massive text datasets — similar to how your phone suggests the next word as you type, but at a much larger scale. When asked about **obscure or niche topics**, there isn't enough training data to draw from — so the model takes a guess. Combined with the training objective to be **helpful**, the model would rather produce a plausible-sounding answer than admit ignorance. Think of it like a well-read friend who takes pride in knowing everything — they'd sometimes rather say something confidently wrong than say "I don't know."

The key insight: **being honest IS being helpful** — they reinforce each other, not compete. Saying "I don't know" is not a failure — it's the more helpful response.

Anthropic regularly tests Claude with thousands of trick questions — obscure facts, niche topics, questions where the truthful answer is "I don't know" — and measures how often it correctly expresses uncertainty, whether it fabricates citations, and how often it hedges appropriately vs. states something false with confidence. Each version improves, but this remains **an ongoing challenge for the entire AI field, not a solved problem**. And as hallucinations become rarer, users check less — making the remaining errors more dangerous, not less.

## Principles (for Claude)

1. **Honesty Over Helpfulness** — Say "I don't know" instead of guessing
2. **Source Verification** — Never fabricate citations, papers, or statistics
3. **Confidence Calibration** — Hedge when uncertain, don't fake certainty
4. **High-Risk Awareness** — Be extra careful with facts, dates, names, niche topics
5. **Self-Checking** — Pause and ask: "Do I actually know this?"

## Prompt Tactics (for Users)

These are strategies you can use in your prompts to reduce hallucinations:

### Ask for Sources and Verify Them

Tell the AI to back up its claims with sources. If it already gave sources, ask it to **check that those sources actually support what it's saying** — not just that they exist.

### Give Permission to Not Know

Tell the AI upfront: **"It's okay if you don't know."** This reduces the pressure to guess and makes honest responses more likely.

### Probe Confidence

Ask the AI: **"How confident are you? Is anything in your answer potentially wrong?"** Often the AI knows it's uncertain but presented the answer confidently anyway.

### Use a Fresh Chat for Verification

Start a **new conversation** and ask the AI to find errors in the previous answer and confirm that sources support the statements. A fresh context avoids confirmation bias.

### Cross-Reference Critical Claims

For important work, **never rely on AI alone**. Be skeptical of specific numbers, dates, and citations — cross-check them against trusted primary sources.

### Ask Follow-Up Questions

If something in the AI's response **sounds off or feels too convenient**, don't let it pass — ask follow-up questions to probe the claim. Hallucinations often unravel under targeted questioning.

## Install

**Option A: CLAUDE.md (Recommended)**

Because anti-hallucination is a guardrail that should apply to every factual claim, `CLAUDE.md` is preferred — it's always loaded into context, so there's no risk of the skill failing to trigger at the moment you need it most.

**A1: Global — one install, all projects (Recommended)**

Append to your user-level `~/.claude/CLAUDE.md`, which Claude Code loads for every project automatically:

```bash
mkdir -p ~/.claude
echo "" >> ~/.claude/CLAUDE.md
curl https://raw.githubusercontent.com/instantX-research/anthropic-anti-hallucinate-skills/main/CLAUDE.md >> ~/.claude/CLAUDE.md
```

**A2: Per-project — share with your team via git**

Install into the project root so teammates pulling the repo pick up the same guardrails automatically.

New project:
```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/instantX-research/anthropic-anti-hallucinate-skills/main/CLAUDE.md
```

Existing project (append):
```bash
echo "" >> CLAUDE.md
curl https://raw.githubusercontent.com/instantX-research/anthropic-anti-hallucinate-skills/main/CLAUDE.md >> CLAUDE.md
```

**Option B: Claude Code Plugin**

From within Claude Code, first add the marketplace:
```
/plugin marketplace add instantX-research/anthropic-anti-hallucinate-skills
```

Then install the plugin:
```
/plugin install anti-hallucinate@anthropic-anti-hallucinate-skills
```

And reload plugins to apply:
```
/reload-plugins
```

This installs the guidelines as a Claude Code plugin, making the skill available across all your projects. Note that skills are loaded on-demand based on the skill's description — which means there's a chance Claude won't recognize the current context as high-risk and skip loading it.

## File Structure

```
.
├── CLAUDE.md                              # Core guidelines (drop into any project)
├── EXAMPLES.md                            # Good vs bad examples for each principle
├── skills/
│   └── anti-hallucinate/
│       └── SKILL.md                       # Claude Code skill definition
├── LICENSE
└── README.md
```

## Customization

These guidelines are a starting point. You can:

- **Add domain-specific rules** — e.g., "Never guess medication dosages" for medical projects
- **Adjust strictness** — tighten for research work, relax for creative brainstorming
- **Combine with other skills** — these guidelines complement coding-style skills like [andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills)

## How to Judge Effectiveness

After applying these guidelines, Claude should:

- Say "I don't know" or "I'm not sure" more often (this is a feature, not a bug)
- Provide fewer fabricated citations and statistics
- Clearly distinguish facts from inferences
- Proactively suggest verification steps for high-risk claims
- Self-correct when challenged rather than doubling down

## Acknowledgments

- **Source**: [Why do AI models hallucinate?](https://www.youtube.com/watch?v=005JLRt3gXI) — Anthropic's official Claude channel
- **Reference**: [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) — project structure and formatting style inspired by this repo

## License

MIT
