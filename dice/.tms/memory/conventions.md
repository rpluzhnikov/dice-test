# Test case conventions

How cases are written in this project. The plugin reads this on every
session. Update it directly whenever conventions evolve.

> Seeded by /setup with sensible defaults — there were no existing cases
> to learn from. Revise these after the first /new-feature when real
> conventions emerge.

## Titles

**Form:** imperative starting with a verb (default)
**Example:** "Бросить кость и увидеть результат"
**Anti-example:** "Успешный бросок" (noun-phrase form — not used)

## Steps

**Verb form:** imperative ('Открыть', 'Нажать')
**Granularity:** atomic (one action per step)
**Numbering:** 1. 2. 3.

## Expected results

**Location:** per-step (right after the action, as an `- Expected:` line)
**Phrasing:** state observable facts; no 'должен'/'should', no
'проверить что'/'verify that' preamble

## Preconditions

**Style:** bullet list
**Common reusable preconditions:**
- (none yet — extract shared steps once a sequence repeats in 3+ cases)

## Frontmatter

**Always present:**
- `id` (auto-allocated by Kensa)
- `title`
- `priority` (allowed values: critical | high | medium | low)
- `status` (allowed values: draft | active | deprecated)
- `tags`
- `source_id` (SOT ref — Jira issue key or URL)
- `generated_by` (when written by plugin: `kensa-qa@<version>`)

**Sometimes present:**
- `preconditions` (when complex enough to be structured)
- `custom` (project-specific fields per schema)

## Tag taxonomy

See `learned/tags.md` for the live list.

## Shared step conventions

**When to extract:** sequence of 3+ steps appearing in 3+ cases.
**Location:** `.tms/shared-steps/<category>/<name>.md`
**Reference syntax:** `Use shared step: <path>`

## Language / phrasing

**Case body language:** ru
**Mixed content:** UI text in original language (Russian); frontmatter
keys and tags stay English.

## Anti-patterns we've banned

- **No "проверить что..." / "verify that..." preambles** — every step is
  a verification; the preamble adds nothing.
- **No selector / xpath in step text** — manual cases describe what the
  tester clicks, not what the automation finds.
- **No screenshot-as-expected-result** — describe the observable state
  in words; screenshots are auxiliary.
