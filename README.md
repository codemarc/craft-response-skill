# The Craft Response Skill

An Agent Skill for Claude Code that reads the message you need to answer, drafts your reply in your voice, and puts it on the clipboard. You paste it wherever you want. The skill never sends anything.

A [Braintrailz](https://braintrailz.com) composition by [codemarc](https://github.com/codemarc).

## The idea

Most replies don't need a chat session. They need a draft that sounds like you, ready to paste. Copy the thread, say the word, paste the answer.

## What it does

- **Finds the source** — pasted text first, then the clipboard (`pbpaste`). Copy a LinkedIn thread, an email, a chat, then invoke.
- **Reads the whole thread** — who wants what, what you already said, what the reply has to accomplish.
- **Drafts in your voice** — punchy, short sentences, no filler, no em dashes, no copywriter polish.
- **Burden-shifts cold outreach** — vendor pitches get no call until they send something specific and concrete.
- **stopslop mode** — say "stopslop" and the reply's only job is to call out the AI slop, tell them to clean it up and resend, and drop the [solid](https://github.com/codemarc/solid-skill) link.
- **Copies to clipboard** — shows you the exact draft and confirms it's on the clipboard. Clipboard only. You send it.

## Install

**Claude Code:**

```bash
git clone https://github.com/codemarc/craft-response-skill.git
mkdir -p ~/.claude/skills
cp -r craft-response-skill/craft-response ~/.claude/skills/craft-response
```

**Optional: customize your voice**

```bash
cp ~/.claude/skills/craft-response/customization.example.md \
   ~/.claude/skills/craft-response/customization.md
# edit customization.md — name, sign-offs, tone rules, stopslop link, business context
```

The skill uses `customization.md` when present. Without it, the agent infers your voice from your rules and session context and falls back to sensible defaults.

## Use

Copy the thread you're answering, then:

```
/craft-response
```

Direction goes in as arguments:

```
/craft-response short and firm
/craft-response stopslop
```

Or just say "craft my response" or "stopslop" in any session.

## Update

```bash
cd /path/to/craft-response-skill
git pull
rm -rf ~/.claude/skills/craft-response
cp -r craft-response ~/.claude/skills/craft-response
# re-copy customization.md if you created one locally (it is not in the repo)
```

## Notes

- macOS only as written (`pbpaste`/`pbcopy`). Swap in `xclip` or `wl-copy` on Linux.
- Copying the draft overwrites the thread on your clipboard; the skill keeps the thread text in the conversation so nothing is lost.

## License

MIT. See [LICENSE](./LICENSE).
