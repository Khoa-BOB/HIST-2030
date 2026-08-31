---
name: lecture-summary
description: Turns a raw HIST-2030 lecture transcript into a structured study summary (Key Entities, Relationships diagram, Lecture Summary narrative). Use this whenever the user asks to "summarize", "do the summary for", "add the summary section to", or "fill in" a lecture markdown file in this repo that has a '## Script' section — especially files under Week*/ containing messy, unpunctuated speech-to-text transcripts of Tennessee history lectures. Also trigger if the user pastes/points to a new transcript and asks for notes, an outline, or the "usual format" for it.
---

# HIST-2030 Lecture Summary

Converts a messy, unpunctuated speech-to-text lecture transcript (in a file's `## Script` section) into a polished, structured summary appended under that file's `## Summary` (or `## summary`) heading. The target format was established across `Week1/#2 The first Tennesseans.md`, `Week1/#3 Firt Tennesseans, pt2.md`, and `Week2/European empires and Tennesee History.md` — treat those three as the canonical reference examples if you need to double-check tone or structure.

## Why this matters

The transcripts are raw dictation: no punctuation, run-on sentences, homophone errors, and garbled proper nouns (e.g. a historian's name transcribed phonetically, a Cherokee leader's name spelled inconsistently). The value of this skill is doing the interpretive work — figuring out what the lecturer actually said and meant despite the noise — and turning it into something the user can actually study from. Don't just clean up punctuation; reconstruct the argument.

## Workflow

1. **Find the target file(s).** The user will usually name a file or a week. If they just say "do the summary," look for lecture `.md` files (typically under `Week*/`) that have a `## Script` section but an empty or missing `## Summary` section — those are the ones needing work. Confirm with the user if it's ambiguous which file(s) they mean.

2. **Read the whole `## Script` section.** Don't skim — the transcript is one long unpunctuated block and important details (dates, names, causal claims) are easy to lose in the run-on text. Read it carefully enough to reconstruct the lecture's actual argument and chronology.

3. **Resolve the noise.** Speech-to-text garbles proper nouns and terms. Use historical knowledge and context clues to recover them — e.g., "Robbie Etheridge" (historian), "Oconostota" (Cherokee leader), "Fort Loudoun," "Yamasee War," "Daniel Tortora." When a name is genuinely ambiguous, make your best-supported inference rather than leaving the garbled version in — a polished summary with a wrong guess is more useful to check against than a summary that just echoes transcription noise, but flag any low-confidence guesses to the user in your reply (not in the file itself).

4. **Write the summary using the exact structure below**, then insert it under the file's `## Summary` heading (replacing any placeholder/empty content there, without touching the `## Script` section above it).

## Output structure

Use this exact skeleton. Section headers and ordering are fixed; the `###` subsection groupings inside Part 1 and the number of narrative points in Part 3 should flex to match what the lecture actually covers.

```markdown
# Lecture N[, Part M]: <Descriptive Title> — Entities, Relationships & Summary

## 1. Key Keyword Entities in Tennessee History

### <Thematic grouping, e.g. "Chronological Eras & Cultural Traditions">
* **<Entity name>:** <one to two sentence description — what it is, when, why it matters>
* **<Entity name>:** <description>

### <Another thematic grouping, e.g. "Key Figures" / "Places & Geographic Entities" / "Major Events & Conflicts" / "Historiographical Frameworks">
* **<Entity name>:** <description>

(3-5 thematic groupings total, chosen to fit the lecture's actual content — don't force categories that have nothing in them.)

---

## 2. Relationships Between Entities

\`\`\`text
[Earliest/Root Entity] (date or date range)
      │  • <driver/cause bullet>
      ▼
[Next Entity] (date range)
      │  • <driver/cause bullet>
      ▼
[Next Entity] (date range)
      │
      ├──────────────┬──────────────┐   (use branches when the lecture describes
      ▼               ▼              ▼    parallel/simultaneous causes or effects)
[Branch A]      [Branch B]      [Branch C]
      │               │              │
      └───────┬───────┴──────────────┘
              ▼
[Convergence / Outcome Entity]
\`\`\`

### Key Dynamics & Evolutionary Drivers
1. **<Throughline name>:** <1-2 sentence synthesis of a major causal chain running through the lecture>
2. **<Throughline name>:** <...>
3. **<Throughline name>:** <...>
(3-4 total)

---

## 3. Lecture Summary

<One-sentence framing of what the lecture covers overall.>

1. **<Phase title> (<date range>):** <3-5 sentences of clean prose narrating this phase, with **bolded** key names/terms/dates pulled from Part 1.>
2. **<Phase title> (<date range>):** <...>
3. **<Phase title> (<date range>):** <...>
(as many numbered phases as the lecture naturally breaks into — usually 3-5)
```

## Style notes

- Bold entity/person/place names and key dates the first time they appear in each section, matching how a textbook glossary would emphasize terms.
- The relationship diagram uses box-drawing characters (`│ ▼ ├ └ ┌ ┐ ─`) — keep it as a chronological/causal flow, not a static list. Branch (`├`/`└`) when the lecture presents parallel causes or simultaneous developments, and converge back when they combine into one outcome.
- Write Part 3 as connected historical narrative in your own words — not a bullet-point rehash of Part 1. It should read like study notes a student could learn the lecture from without watching it.
- Keep terminology consistent across all three parts (don't call something "the Shatter Zone" in Part 1 and "period of instability" in Part 3 without tying them together).
- If the lecture is explicitly a "pt. 2" / continuation of a previous file, mirror that in the title (see `Week1/#3 Firt Tennesseans, pt2.md` for the pattern) and feel free to reference the prior lecture's entities where the transcript does.

## After writing

Briefly tell the user which file(s) you updated and flag any proper nouns or facts you had to infer with lower confidence from the garbled transcript, so they can double check against the actual lecture if needed.
