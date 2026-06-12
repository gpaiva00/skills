# pt-prompt

A Claude Code skill that goes far beyond translation — it interprets colloquial Brazilian Portuguese requests, resolves ambiguities, gathers minimal project context, and structures precise English prompts that any AI agent can execute flawlessly.

Brazilian Portuguese prompts are often context-heavy, colloquial, and assume shared understanding. English prompts for AI agents require explicit requirements, scope, and constraints. This skill bridges that gap by **thinking** about what the user really means, not just translating words.

## What It Does

1. **Interprets Intent** — Reads between the lines of colloquial Portuguese (e.g., *"ta lento"* -> *"improve render performance"*, not just "is slow").
2. **Resolves Ambiguities** — Identifies vague terms and forces clarification before the agent acts.
3. **Gathers Minimal Context** — Performs 1-2 targeted lookups (project memory, `CLAUDE.md`) to fill gaps without over-exploring.
4. **Preserves Urgency & Emotion** — Maps cultural signals like *"pra ontem"* to explicit deadlines or urgency flags.
5. **Structures for Action** — Formats the final prompt into a clean, actionable structure: `Purpose → Requirements → Constraints → Expected Deliverable → Edge Cases`.

> **Result:** The agent receives a prompt it can execute without guessing, not just a translated version of what the user said.

## Installation

You can install this skill directly into Claude Code using the following command:

```bash
npx skills@latest add gpaiva00/skills
```

Or select just this skill from the repo:
```bash
npx skills@latest add gpaiva00/skills --skill pt-prompt
```

## Usage

Simply type your request in Brazilian Portuguese within Claude Code. The skill will:

1. **Analyze** your message for colloquialisms, implicit requirements, and ambiguities
2. **Look up** minimal project context if needed (stack, conventions, existing patterns)
3. **Structure** a precise English prompt in a code block
4. **Wait** for your confirmation before the agent executes

This means you get a prompt that the agent truly understands — not just a translated guess.

**Example Input:**
> "me ajude a implementar tags nas tarefas, precisa funcionar offline, usar localStorage, cores customizáveis, máximo 12 cores, pra ontem"

**Example Skill Output:**
```markdown
Implement a tag system for tasks with:

**Purpose:** Categorize tasks with persistent tags across offline/online states

**Requirements:**
- Create Tag interface with id, name, color
- Assign tags to tasks
- Color picker: 12 predefined swatches
- All data persists to localStorage
- Offline-first: changes sync when connection restored

**Constraints:**
- Max 12 colors per tag system
- localStorage as data source (no API calls)
- [URGENT] Needed ASAP

**Edge Cases:**
- What happens when colors conflict with theme?
- Can users delete tags if tasks reference them?

**Expected Deliverable:** Tag interface, storage adapter, UI component
```
