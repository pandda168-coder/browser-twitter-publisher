# browser-twitter-publisher

A focused OpenClaw skill project for browser-driven X/Twitter publishing.

This repository packages one reusable AgentSkill:

- `browser-twitter-publisher`

The skill is designed for workflows where an agent should:

1. attach to a Chrome session through `chrome-devtools-mcp`
2. research live X posts in-browser
3. filter low-signal results
4. rewrite copy so it fits X and reads like X-native content
5. generate a simple card image fast
6. upload media and publish directly from the browser

## Repository layout

```text
skills/
  browser-twitter-publisher/
    SKILL.md
    references/
      browser-publish-checklist.md
      post-templates.md
      publish-recovery.md
      search-playbook.md
    assets/
      card-template.svg

dist/
  browser-twitter-publisher.skill
```

## Skill scope

`browser-twitter-publisher` covers:
- attaching to a debuggable Chrome session
- verifying X login state before external actions
- using better X search query hygiene
- removing spam, duplicate reposts, and low-information posts
- compressing text to fit X limits
- generating SVG-based card images and exporting them to PNG
- uploading media and publishing posts
- verifying publish success and returning the final post URL

## Iteration workflow

### Edit
Update source files in:
- `skills/browser-twitter-publisher/SKILL.md`
- `skills/browser-twitter-publisher/references/*.md`

### Repackage
```bash
python3 /opt/homebrew/lib/node_modules/openclaw/skills/skill-creator/scripts/package_skill.py \
  skills/browser-twitter-publisher dist
```

### Commit
```bash
git add skills/browser-twitter-publisher dist/browser-twitter-publisher.skill README.md .gitignore
git commit -m "Update browser-twitter-publisher skill"
```

## Notes

This repository is intentionally kept narrow: skill source, packaged artifact, and minimal repo metadata.
Workspace memories, generated briefs, scratch assets, and other transient files are ignored so the project stays clean for future skill iteration.
