# Contributing

Thanks for helping make this audit sharper. The goal is a checklist that catches what actually gets small teams sued, with as few false alarms as possible.

## Ground rules

- **No secrets or private data.** Never paste API keys, env files, customer data, or private source into an issue or pull request. Reduce examples to a minimal snippet you wrote yourself.
- **Not legal advice, in either direction.** Contributions describe patterns of exposure and cite sources. They do not tell anyone they are or are not compliant.
- **Sources over opinions.** A new check or a legal-hooks change needs a link to a statute, regulation, agency guidance, or a reported case or enforcement action.
- **Stay static.** The skill must remain plain markdown and YAML: no scripts, dependencies, network calls, remote instructions, or auto-update. Pull requests that add any of these will be declined.
- **Plain language.** Short sentences, no em dashes, no hype.

## Kinds of contribution

### Report a false pass or false fail
Use the matching issue template. Include the check ID, the minimal code pattern, what the audit said, and what it should have said.

### Propose a new check
Use the "New check" template. A check needs:

1. The problem in one line.
2. Why it creates legal exposure, with at least one source link.
3. What evidence in code proves PASS and what proves FAIL.
4. When it is N/A.
5. A suggested default severity.

New checks take the next unused ID in their section (for example `SALE-07`). IDs are never renumbered or reused. To retire a check, mark it `Retired` and leave the ID in place.

### Improve evidence hints
Add vendors, SDK names, framework conventions, or file locations to a check's evidence hints in `references/checklist.md`.

### Add sources
Fill in the Source column in `references/legal-hooks.md` with primary sources.

## Pull request checklist

- [ ] Changes are markdown or YAML only.
- [ ] New or changed checks follow the format in `references/checklist.md`.
- [ ] Legal claims link a source.
- [ ] If behavior changed, a test prompt in `meta.yaml` covers it.
- [ ] Version bumped in `SKILL.md`, `meta.yaml`, `.claude-plugin/plugin.json`, and `.claude-plugin/marketplace.json`, with a `CHANGELOG.md` entry (maintainer can do this at merge).

## Versioning

- Patch (0.1.x): wording, evidence hints, sources.
- Minor (0.x.0): new checks, changed severity defaults, report format additions.
- Major (x.0.0): changes that break the report format or the meaning of an existing ID.
