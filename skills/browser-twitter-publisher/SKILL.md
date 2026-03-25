---
name: browser-twitter-publisher
description: Publish X/Twitter posts through a browser session controlled by chrome-devtools-mcp. Use when a user wants you to research X in-browser, draft a stronger post, create a simple news card image, and publish a text or image post directly from the browser instead of only returning copy.
---

# Browser Twitter Publisher

Publish X posts from a browser session, not just as draft text. Use this for browser-driven X workflows: search, curate, compress copy to fit X limits, generate a simple card image, upload media, and post.

## Workflow

1. **Attach to a controllable Chrome**
   - Prefer `chrome-devtools-mcp` through `mcporter`.
   - If no debuggable browser exists, start Chrome with `--remote-debugging-port` and a dedicated `--user-data-dir`.
   - Verify with `list_pages` and `take_snapshot` before doing anything else.

2. **Verify X session state**
   - Open `https://x.com/home` or the intended search URL.
   - If X redirects to login, stop and ask the user to log in inside that browser session.
   - Do not promise posting until the snapshot shows the signed-in account UI.

3. **Research before posting**
   - Use X search with focused queries such as:
     - `"AI Agent" -filter:replies filter:links`
     - add `f=live` for latest flow
   - Use snapshots to collect candidates.
   - Manually remove junk: giveaways, “claim my agent”, spam, duplicate reposts, low-information replies.
   - Keep the final list anchored on actual signals: product releases, data points, infra changes, security/governance, enterprise adoption.

4. **Write for X, not for reports**
   - Lead with one hook: number, contrast, surprise, or conflict.
   - Prefer one claim per post.
   - For a main post, use this structure:
     - hook
     - 1–3 proof points
     - one conclusion
     - 1 short hashtag block at most
   - When a post feels flat, tighten toward:
     - data first
     - short paragraphs
     - fewer adjectives
     - no generic “today I learned” filler

5. **Check character count in-browser**
   - Prefilling `https://x.com/compose/post?text=...` is fast, but always inspect the composer snapshot.
   - If snapshot says the post exceeds the limit, rewrite and reload.
   - Do not click `Post` until the composer shows the button enabled.

6. **Create a simple card image when needed**
   - Prefer editing `assets/card-template.svg` instead of rebuilding a card from scratch.
   - Keep the card to one headline, one subtitle, 2–3 short modules, and one footer takeaway.
   - Open the SVG in the browser and use `take_screenshot` to export PNG.
   - Then upload via the composer’s media button using `upload_file`.
   - Keep card copy minimal; the post should still work without reading every line on the card.

7. **Publish and verify**
   - Click the final `Post` button only after text and media are ready.
   - Confirm success by checking for `Your post was sent.` or by spotting the fresh post in the timeline/profile.
   - Return the final post URL to the user.

## Copy patterns

### Main post pattern
- Line 1: strongest data or conflict
- Blank line
- 2–4 short lines of proof
- Blank line
- one takeaway sentence
- optional hashtag line

### Thread pattern
- Post 1: hook + core data point + thesis
- Post 2: explain why the gap exists
- Post 3: where the market is moving next

## Card rules

Use a 4:5 card when possible.

Preferred layout:
- top label
- giant number / headline
- short subtitle
- 2–3 stacked modules
- one-line takeaway footer

Good card title styles:
- `AI AGENT PRODUCTION GAP`
- `85% PILOT / 5% PRODUCTION`
- `FROM DEMO TO DEPLOYMENT`

## Quality bar before posting

Only publish when the draft has all three:
- one visible hook in the first 1–2 lines
- at least one concrete signal, number, or named company
- one clear takeaway

If the draft misses any of these, rewrite before posting.

## Safety / execution notes

- Publishing is an external action: make sure the user asked for it.
- Do not silently post from the wrong account; verify the visible profile handle in snapshot first.
- If X shows graduated-access or anti-spam friction, tell the user exactly what blocked posting.
- Prefer one strong post with media over several weak posts.
- Retry failed publish attempts carefully; do not spam the composer.

## Read as needed

- Read `references/post-templates.md` when you need ready-to-use hooks, thread structures, and card copy patterns.
- Read `references/browser-publish-checklist.md` when you need the exact browser execution sequence.
- Read `references/search-playbook.md` when you need tighter X query strategy and filtering heuristics.
- Read `references/publish-recovery.md` when publishing fails, text overflows, or X shows account friction.