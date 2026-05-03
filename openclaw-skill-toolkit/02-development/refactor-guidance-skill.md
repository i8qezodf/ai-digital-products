# Refactor Guidance Skill

Improve code without breaking it — systematically.

## When to Use

Code works but is hard to maintain, modify, or understand. Time to refactor but you need to do it safely.

## The Skill

```
Refactor this code:

CODE TO REFACTOR:
[code here]

LANGUAGE: [what it's written in]
CURRENT PROBLEMS:
[ ] Too long
[ ] Too complex
[ ] Duplicated logic
[ ] Poor naming
[ ] Hard to test
[ ] Other: [describe]

GOALS FOR REFACTOR:
[What should be better after]

SAFETY REQUIREMENTS:
- Existing tests: [yes/no, coverage?]
- Can run tests during: [yes/no]
- Production deployment: [frequency/risk]

REFACTOR PLAN:

1. PREPARATION
   - Add/modify tests first
   - Ensure you can roll back
   - Document current behavior

2. SMALLEST CHANGE FIRST
   [Step-by-step plan, one change at a time]

3. VERIFY EACH STEP
   - [ ] Ran tests after this change?
   - [ ] Still works as before?

4. FINAL REVIEW
   - Does it still do the same thing?
   - Is it actually better?
   - Did I introduce any new problems?

OUTPUT:
Provide refactored code with:
- Changes highlighted
- Each change explained
- Test command to verify
```

## Example

```
CODE TO REFACTOR:
```javascript
function processUser(u) {
  let name = u.firstName + " " + u.lastName;
  let greeting = "Hello " + name + "!";
  let email = u.email;
  if (u.age && u.age < 18) {
    greeting = "Hey " + name + "!";
  }
  let fullGreeting = greeting + " Your email is " + email;
  console.log(fullGreeting);
  return fullGreeting;
}
```

PROBLEMS:
- Function does multiple things (builds string, logs, returns)
- Name is vague
- String concatenation is messy
- No tests

REFACTORED:
```javascript
function buildGreeting(user) {
  const fullName = `${user.firstName} ${user.lastName}`;
  const prefix = user.age && user.age < 18 ? "Hey" : "Hello";
  return `${prefix} ${fullName}!`;
}

function formatUserInfo(user) {
  return `${buildGreeting(user)} Your email is ${user.email}`;
}

function processUser(user) {
  const output = formatUserInfo(user);
  console.log(output);
  return output;
}
```

CHANGES:
1. Extracted buildGreeting() - single responsibility
2. Used template literals - more readable
3. formatUserInfo() separates concerns
4. processUser() now orchestrates, doesn't compute

TESTS:
- buildGreeting() can be tested independently
- Test various age values, name formats
```

## Tips

- Never refactor and add features at the same time
- If it doesn't have tests, add them first
- Small steps, commit often
- If a refactor takes more than a few hours, you're doing it wrong — break it up
- "It works" is not the same as "it's good"

## Variations

**Big cleanup:** Focus on module/folder structure first
**Performance refactor:** Profile before, only optimize what matters
**Testability:** Extract dependencies, use dependency injection
