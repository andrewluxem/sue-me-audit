# Report template

Produce the report in this order. Keep the headings.

```markdown
# Sue-Me Audit: <repo or app name>

This is a risk screen, not legal advice.

**Scope:** <one paragraph: what the app does, stack, who it serves, what it collects, third parties found>

**Result:** <n> PASS · <n> FAIL (<n> CRITICAL, <n> HIGH, <n> LOW) · <n> CAN'T TELL

## Privacy

| ID | Check | Verdict | Severity | Evidence | Fix |
|---|---|---|---|---|---|
| PRIV-01 | Privacy policy | FAIL | HIGH | `app/privacy/page.tsx:12` | <concrete fix> |

## Content

<same table>

## Sales

<same table>

## AI

<same table>

## Ranked by likelihood of harm

1. <ID> <short name>: <one line of reasoning>

## Fix order

Quick wins (S):
1. <ID> <fix> (S)

Then:
2. <ID> <fix> (M)

## Check outside the repo

- [ ] <CAN'T TELL item>: <what to check and where>

Ready to start fixing? Tell me which batch.
```

Rules:

- PASS rows cite evidence briefly. N/A rows say why in the Evidence column.
- CAN'T TELL rows leave Severity blank and put the instruction in the Fix column.
- Evidence is always `path:line` from a file actually read.
