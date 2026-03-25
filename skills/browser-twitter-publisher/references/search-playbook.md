# Search Playbook

## Goal

Find X posts that are recent enough to matter and information-dense enough to publish from.

## Default query pattern

Start with:

```text
"AI Agent" -filter:replies filter:links
```

Add `f=live` to stay on latest results.

## Better query variants

### Product / launch signals
```text
"AI Agent" (launch OR released OR announce OR introduced) -filter:replies filter:links
```

### Infrastructure signals
```text
"AI Agent" (runtime OR infrastructure OR deployment OR production) -filter:replies filter:links
```

### Enterprise signals
```text
"AI Agent" (enterprise OR workflow OR studio OR platform) -filter:replies filter:links
```

### Security / governance signals
```text
"AI Agent" (security OR governance OR identity OR audit) -filter:replies filter:links
```

## Keep

Prefer posts with at least one of these:
- concrete product release
- specific data point
- recognizable company or source
- operational insight about deployment
- strong market signal

## Drop

Discard posts that are mainly:
- giveaways
- bot verification / claim messages
- meme replies
- low-context reposts
- obvious affiliate spam
- duplicate cross-posts with no added value

## Ranking heuristic

When several candidate posts are available, rank by:
1. signal density
2. business relevance
3. novelty
4. timeliness
5. source credibility
