# Contributing

Thanks for helping grow the catalog — or improve the skill itself.

## Ways to help

1. **Add a filler pattern** — the most common contribution
2. **Improve an existing entry** — clearer example, sharper reason, better fix
3. **Improve the skill** — `solid/SKILL.md` workflow, tests, or output format

## Adding a pattern

Edit [`solid/references/patterns.md`](./solid/references/patterns.md).

**Rules:**
- Use the template at the top of the file
- Three parts, in order: what it looks like, why it is air, the fix
- Real examples beat invented ones. Anonymize if the source would be embarrassed
- Keep it to five lines. An entry that violates the skill's own standard gets cut
- No overlap with an existing pattern. If it is a variant, improve that entry instead

**A pattern qualifies if** deleting it from a draft loses no information, and a writer who knows its name will catch it in their own writing.

**A pattern does not qualify if** it is a style preference. "Passive voice" and "adverbs" are taste. "Manufactured pause" is a void.

## Improving the skill

`solid/SKILL.md` is the workflow. The four tests, the refusal condition, and the two-cut output are load-bearing — see [`solid/references/braintrailz.md`](./solid/references/braintrailz.md) for why before proposing changes to them.

The skill must obey its own standard. A PR that makes any file longer without making it more useful will be rejected on the merits it exists to enforce.

## PRs

- One pattern or one change per PR
- Say what you cut and why in the description
- If you changed `solid/`, note it so the packaged `solid.skill` can be rebuilt

## Rebuilding the packaged skill

```bash
zip -r solid.skill solid -x "*.DS_Store"
```
