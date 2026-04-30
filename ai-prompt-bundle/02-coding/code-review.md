# Code Review Prompt

Drop this into your AI tool when you need to take a look at some code.

## The Template

```
Can you take a look at this code? Working with [language/framework here] and here's what it's supposed to do: [what the code does]

Here's the code:
```
[paste your code here]
```

## What I Want You to Check

1. **Does it actually work?** Any obvious bugs or edge cases that'll bite us later?

2. **Security stuff** - SQL injection, XSS, that kind of thing. Also whether we're accidentally leaking anything sensitive.

3. **Performance** - Any obvious slowdowns? N+1 queries, unnecessary loops, memory issues?

4. **Readability** - Would someone else be able to figure out what's going on here? Are things named sensibly? Comments where they need to be?

5. **General structure** - Is this going to be a nightmare to maintain six months from now?

## Output

Give me a list of issues sorted by how bad they are. For each one, tell me where it is and how to fix it. If there's nothing obviously wrong, just tell me and I'll move on.

```

## How to Use It

Paste your code in place of the placeholder. Be specific about what language and framework you're using. If you have a particular concern (like "I'm worried about performance here"), mention that upfront.

The AI will flag issues it finds. Use your judgment on which ones actually matter for your situation.
