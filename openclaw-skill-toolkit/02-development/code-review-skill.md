# Code Review Skill

Systematic code review that catches real issues without the noise.

## When to Use

Reviewing a pull request, looking at legacy code, or doing self-review before submitting.

## The Skill

```
Review this code for issues:

LANGUAGE/FRAMEWORK: [what it's written in]
CODE:
[paste code here]

CONTEXT:
- What this code does: [one sentence]
- Where it runs: [frontend/backend/CLI/etc]
- Risk if broken: [low/medium/high/critical]

Review checklist:

1. CORRECTNESS
   - Does it do what it's supposed to do?
   - Edge cases handled?
   - Error handling appropriate?
   - Logic bugs?

2. SECURITY
   - User input sanitized?
   - SQL injection / XSS / injection risks?
   - Secrets hardcoded?
   - Authentication/authorization correct?

3. PERFORMANCE
   - N+1 query problems?
   - Unnecessary loops or operations?
   - Memory leaks?
   - Database indexes where needed?

4. MAINTAINABILITY
   - Code clear enough to understand?
   - Functions too long / complex?
   - DRY violations?
   - Comments where needed, not redundant?

5. TESTING
   - Test coverage adequate?
   - Edge cases tested?
   - Tests actually test what matters?

Output:
- Critical issues (fix now)
- Important issues (fix soon)
- Suggestions (consider)
- Nitpicks (optional)
- Positive observations (what's good)
```

## Example Review

**Code:**
```javascript
function getUser(id) {
  return db.query("SELECT * FROM users WHERE id = " + id);
}
```

**Output:**
```
CRITICAL:
- SQL injection: 'id' directly interpolated into query. An attacker could pass id=1 OR 1=1 to dump all users. Use parameterized queries.

IMPORTANT:
- SELECT * is fragile — if schema changes, this breaks silently. List specific columns needed.

SUGGESTIONS:
- No error handling — what if DB connection fails?
- Function name is generic. getUserById communicates intent better.

NITPICKS:
- Missing JSDoc comment
```

## Tips

- Focus on issues that would actually break something
- Distinguish between "I would have done it differently" and "this is actually wrong"
- If something is unclear, ask — sometimes the code is wrong, sometimes you need context
- Flag security issues prominently

## Variations

**Quick review:** Skip sections that don't apply, focus on critical only
**Architecture review:** Add "does this fit our patterns?" section
**Performance focus:** Deep dive on loops, queries, caching
