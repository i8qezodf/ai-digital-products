# Meeting Notes Skill

Structured meeting summaries that capture what happened and what needs to happen next.

## When to Use

After any meeting, call, or discussion you want to remember. Use this to organize your notes into something actually useful.

## The Skill

```
Process these meeting notes into a structured summary:

RAW NOTES:
[paste your meeting notes or transcript]

Generate a document with these sections:

## Meeting Overview
- Date:
- Attendees:
- Duration:
- Purpose:

## Key Discussion Points
[bullet list of what was discussed, decisions made]

## Decisions Made
[explicit decisions with the reasoning if available]

## Action Items
For each action item:
- WHAT: [specific task]
- WHO: [person responsible]
- WHEN: [deadline if mentioned]
- STATUS: [pending / in progress / blocked]

## Follow-up Questions
[things that came up that need more research or answers]

## Next Steps
[what happens next, next meeting if any]
```

## Example

**Input:**
```
Meeting with Sarah about Q2 launch. She said marketing needs 3 weeks before launch, not 2. Dev team can have beta ready by June 1. Budget is tight — maybe $5k for ads. We should sync again next Thursday.
```

**Output:**
```
## Meeting Overview
- Date: [date]
- Attendees: You, Sarah
- Purpose: Q2 Launch Planning

## Key Discussion Points
- Marketing needs 3 weeks pre-launch buffer (vs. original 2 weeks)
- Dev team target: beta ready June 1
- Ad budget constraint: ~$5k
- Follow-up meeting scheduled

## Decisions Made
- Ad budget set at $5k maximum
- Next sync: next Thursday

## Action Items
- WHAT: Confirm beta release date with dev team
  - WHO: [you]
  - WHEN: Before next meeting
  - STATUS: pending
- WHAT: Create marketing timeline (3 weeks out from launch)
  - WHO: Sarah
  - WHEN: Next Thursday
  - STATUS: pending

## Follow-up Questions
- What's the launch date if beta is June 1?
- Which ad platforms for $5k budget?

## Next Steps
Schedule next Thursday sync, prepare beta confirmation
```

## Tips

- Don't try to capture everything — focus on decisions and actions
- Note any blockers mentioned
- If no deadline was given, suggest one
- Review within 24 hours while context is fresh

## Variations

**Daily standup format:** Focus on Yesterday / Today / Blockers
**Brainstorm format:** Collect all ideas first, then categorize
**1:1 format:** Add section for career/personal development topics
