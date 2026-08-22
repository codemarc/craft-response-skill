---
name: craft-response
description: Read the message Marc needs to answer (clipboard, pasted text, or this conversation), draft his response in his voice, and copy it to the macOS clipboard so he can paste it anywhere. Trigger: /craft-response, or when Marc says "craft my response", "draft my reply", "write my response and copy it", or "dropslop".
---

# Craft Response

Draft the response Marc would send, in his voice, and put it on the clipboard.

## Steps

1. **Find the source material**, in this order:
   1. Text Marc pasted or described in this conversation.
   2. The clipboard: run `pbpaste`. Marc often copies a thread (LinkedIn, email, chat) right before invoking this skill.
   3. If neither yields anything to respond to, ask Marc to paste the message. Do not invent context.

   Arguments (e.g. `/craft-response short and firm`) are tone/length direction.

2. **Read the thread, not just the last message.** Identify who is asking what of Marc, what Marc has already said, and what the reply needs to accomplish (shut it down, put the burden back on them, accept, redirect). Cold outreach and vendor pitches get the burden-shift treatment: no call until they show something specific and concrete.

3. **Draft in Marc's voice.** Rules (non-negotiable):
   - Punchy, short sentences. No filler. Direct.
   - **No em dashes ever.**
   - No marketing polish. If it sounds like a copywriter wrote it, cut it.
   - Match the medium: email gets a greeting and sign-off (Marc); chat/SMS gets neither. LinkedIn gets first name and "Marc".
   - Keep it tight. Say the thing, stop.
   - When the other party's writing is AI slop, it is in character for Marc to call it out and point them at the solid skill: https://github.com/codemarc/solid-skill

   **Dropslop mode.** If Marc invokes with "dropslop" (or `/craft-response dropslop`), skip the diplomacy. The reply's whole job is to call out the slop and hand them the fix: name it (word salad, word vomit, AI slop), tell them to clean it up and resend, and drop the solid link. A few lines max. No engagement with the pitch content itself.

4. **Copy to clipboard.** Write the draft to a file in the scratchpad, then:
   ```bash
   pbcopy < <draft-file>
   ```
   Always use the file, never echo/pipe the text inline; quotes and backticks in the draft break escaping.

5. **Show it.** Print the exact draft in a fenced block, confirm it is on the clipboard, and say in one line what the draft does (e.g. "puts the burden back on them"). If Marc asks for edits, revise, re-copy, and confirm again.

## Notes

- Never send the response anywhere (email, Slack, LinkedIn, etc.). Clipboard only. Marc pastes it himself.
- Copying the draft overwrites the source thread on the clipboard; keep the thread text in the conversation so it isn't lost.
- If the reply is business-facing (Braintrailz/BLT), stay consistent with that context but do not slip into pitch language.
