# workspace-shortvideo

Browser-driven X/Twitter publishing workflow for OpenClaw.

This repository currently packages one reusable AgentSkill:

- `browser-twitter-publisher`

It is designed for workflows where an agent should:

1. attach to a Chrome session via `chrome-devtools-mcp`
2. research live X/Twitter posts in-browser
3. draft stronger X-native copy
4. generate a simple card image
5. upload media and publish a post directly from the browser

## Repository layout

```text
skills/
  browser-twitter-publisher/
    SKILL.md
    references/
      browser-publish-checklist.md
      post-templates.md

dist/
  browser-twitter-publisher.skill
```

## Main skill

### `browser-twitter-publisher`

Source:
- `skills/browser-twitter-publisher/`

Packaged artifact:
- `dist/browser-twitter-publisher.skill`

This skill covers:
- attaching to a debuggable Chrome session
- verifying X login state before actions
- searching X with better query hygiene
- filtering low-signal results
- compressing copy to fit X limits
- generating fast SVG-based card images
- uploading media and publishing posts
- verifying successful publication

## How to iterate on the skill

### 1. Edit source files
Update:
- `skills/browser-twitter-publisher/SKILL.md`
- `skills/browser-twitter-publisher/references/*.md`

### 2. Repackage
```bash
python3 /opt/homebrew/lib/node_modules/openclaw/skills/skill-creator/scripts/package_skill.py \
  skills/browser-twitter-publisher dist
```

### 3. Commit changes
```bash
git add skills/browser-twitter-publisher dist/browser-twitter-publisher.skill
git commit -m "Update browser-twitter-publisher skill"
```

## Notes

This repo is intentionally focused on the skill source and packaged artifact.
Workspace notes, memories, generated briefs, and scratch assets are ignored so the repository stays clean for future skill iteration.
