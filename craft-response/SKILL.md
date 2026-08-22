---
name: craft-response
description: Read the message the user needs to answer (clipboard, pasted text, or this conversation), draft their response in their voice, and copy it to the macOS clipboard so they can paste it anywhere. Trigger: /craft-response, or when the user says "craft my response", "draft my reply", "write my response and copy it", or "stopslop".
---

# Craft Response

Draft the response the user would send, in their voice, and put it on the clipboard.

## Customization

Before drafting, check for a `customization.md` file in the same directory as this skill. If it exists, read it and follow its voice, sign-off, and context rules.

If there is no `customization.md`, infer the user's voice from their rules, prior messages in the session, and the defaults in step 3 below.

See `customization.example.md` in this directory for a template you can copy to `customization.md`.

## Steps

1. **Find the source material**, in this order:
   1. Text the user pasted or described in this conversation.
   2. The clipboard: run `pbpaste`. Users often copy a thread (LinkedIn, email, chat) right before invoking this skill.
   3. If neither yields anything to respond to, ask the user to paste the message. Do not invent context.

   Arguments (e.g. `/craft-response short and firm`) are tone/length direction.

2. **Read the thread, not just the last message.** Identify who is asking what of the user, what the user has already said, and what the reply needs to accomplish (shut it down, put the burden back on them, accept, redirect). Cold outreach and vendor pitches usually deserve the burden-shift treatment: no call until they show something specific and concrete.

3. **Draft in the user's voice.** Apply rules from `customization.md` when present. Otherwise use these defaults:
   - Clear and direct. Match the user's usual tone from the session or their rules.
   - No marketing polish. If it sounds like a copywriter wrote it, cut it.
   - Match the medium: email gets a greeting and sign-off; chat/SMS gets neither. LinkedIn and similar platforms get a first-name greeting and the user's name on sign-off unless their rules say otherwise.
   - Keep it tight. Say the thing, stop.

   **stopslop mode.** If the user invokes with "stopslop" (or `/craft-response stopslop`), skip diplomacy. The reply's whole job is to call out AI slop, tell them to clean it up and resend, and share any fix link from `customization.md`. A few lines max. No engagement with the pitch content itself. If no customization defines stopslop behavior, name the slop plainly, ask them to rewrite and resend, and keep it short.

4. **Copy to clipboard.** Write the draft to a file in the scratchpad, then:
   ```bash
   pbcopy < <draft-file>
   ```
   Always use the file, never echo/pipe the text inline; quotes and backticks in the draft break escaping.

5. **Show it.** Print the exact draft in a fenced block, confirm it is on the clipboard, and say in one line what the draft does (e.g. "puts the burden back on them"). If the user asks for edits, revise, re-copy, and confirm again.

## Notes

- Never send the response anywhere (email, Slack, LinkedIn, etc.). Clipboard only. The user pastes it themselves.
- Copying the draft overwrites the source thread on the clipboard; keep the thread text in the conversation so it isn't lost.
- If `customization.md` defines business or company context, stay consistent with it but do not slip into pitch language.
