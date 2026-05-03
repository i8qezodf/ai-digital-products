# Knowledge Base Skill

Build and maintain a personal knowledge base that actually works.

## When to Use

You want to save information for later. You need to find something you learned before. You want to connect ideas across different areas.

## The Skill

```
Manage this knowledge base entry:

OPERATION: [save / search / update / link]

CONTENT:
[what you want to save or question you're asking]

METADATA:
- Source: [where this came from]
- Tags: [relevant tags, comma separated]
- Related to: [other topics/entries this connects to]
- Confidence: [high / medium / low - how sure you are]

For SAVING: Store in appropriate category, create cross-links
For SEARCHING: Find relevant entries, show connections to current topic
For UPDATING: Revise entry, note what changed and why
For LINKING: Show how this connects to existing knowledge
```

## Categories

Use these top-level categories:
- **tech** — Technical findings, commands, architecture
- **tools** — Tool setups, CLI tips, workarounds
- **people** — People mentioned and what you know about them
- **projects** — Project context, decisions, blockers
- **learnings** — Lessons, mistakes, insights
- **inbox** — Unsorted, review later

## Example Save

**Input:**
```
OPERATION: save
CONTENT: The command 'openclaw gateway restart' requires admin privileges. Running without elevated permissions gives error code 403. Workaround: use 'openclaw gateway stop' then 'openclaw gateway start' as separate commands.
METADATA:
- Source: personal testing, 2024
- Tags: openclaw, gateway, troubleshooting
- Related to: openclaw-cli, windows-admin
- Confidence: high
```

## Example Search

**Input:**
```
OPERATION: search
CONTENT: How do I restart the OpenClaw gateway on Windows?
```

**Output:**
```
Found 2 relevant entries:

1. [tech/openclaw-gateway] - HIGH relevance
   The command 'openclaw gateway restart' requires admin privileges...
   
2. [tools/openclaw-cli] - MEDIUM relevance
   Gateway commands and common issues...

These connect to: openclaw-troubleshooting, windows-admin-tips
```

## Tips

- Save decisions, not just information
- Tag consistently — makes search much better
- Link related entries — knowledge compounds
- Review inbox weekly, sort into categories
- Write for your future self — include context

## Variations

**Project journal:** Add "project:" prefix, include status updates
**People directory:** Add contact context, conversation summaries
**Error log:** Track errors with solutions found
