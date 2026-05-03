# Bug Fix Skill

Diagnose and fix bugs systematically without guessing.

## When to Use

Something is broken and you need to figure out why. Use this instead of random changes until something works.

## The Skill

```
Debug this issue:

PROBLEM STATEMENT:
[What should happen vs. what actually happens]
ENVIRONMENT:
[Browser, OS, language version, etc.]
REPRODUCIBLE: [Yes/No/Usually]

WHAT I'VE TRIED:
[Already attempted fixes, what happened]

DIAGNOSTIC APPROACH:

Step 1: Isolate
- Can I create a minimal test case that reproduces this?
- Can I confirm which component/module is responsible?

Step 2: Hypothesis
Based on symptoms, what could cause this?
1. [Possibility A]
2. [Possibility B]
3. [Possibility C]

Step 3: Test
For each hypothesis:
- How to confirm or rule out?
- What evidence would I see?

Step 4: Fix
- Root cause: [what actually was wrong]
- Fix applied: [what changed]
- Why this fixes it: [connection between cause and solution]

VERIFICATION:
- How to confirm the fix works?
- What could still break?
- Edge cases to test?

```

## Example

```
PROBLEM: User avatars not loading in production
ENVIRONMENT: React app, AWS S3, Chrome latest
REPRODUCIBLE: Yes, for users who signed up after migration

WHAT I'VE TRIED:
- Cleared cache (didn't help)
- Checked S3 bucket (images exist)
- Looked at network tab (404 errors)

DIAGNOSTIC APPROACH:

Step 1: Isolate
- Minimal case: User ID 12345 avatar → 404
- New users only = migration-related

Step 2: Hypothesis
1. Migration didn't copy old avatars to new bucket
2. Path format changed but old references still using old format
3. CORS blocking new bucket

Step 3: Test
1. Check old bucket for user 12345 → NOT FOUND (confirmed migration issue)
2. Check old path vs new path → old used /avatars/12345.jpg, new uses /avatars/12/34/12345.jpg
3. Test direct URL → works (ruling out CORS)

Step 4: Fix
- Root cause: Migration script didn't copy avatars for users who signed up before migration but used the app after
- Fix: Run targeted migration for recently-active users
- Why: These users had records created before migration but their avatar files were in the old bucket

VERIFICATION:
- Test with affected users (internal test account)
- Monitor error rate for avatar 404s
- Add monitoring alert if spike
```

## Tips

- If you can't reproduce it, you can't fix it — spend time on reproduction first
- Change one thing at a time
- Keep notes of what you tried — you'll forget
- "Works on my machine" isn't a fix

## Variations

**Performance bugs:** Add profiling step, measure before/after
**Heisenbugs:** Add logging, disable caching, check timing
**Intermittent issues:** Check race conditions, async timing
