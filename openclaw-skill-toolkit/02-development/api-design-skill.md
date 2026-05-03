# API Design Skill

Design REST APIs that make sense to use and maintain.

## When to Use

Starting a new API from scratch, adding endpoints to an existing API, or reviewing API designs.

## The Skill

```
Design a REST API for:

PURPOSE: [what this API does]
USERS: [who will use it — internal team, external developers, etc.]
PLATFORM: [web, mobile, both, CLI, etc.]

Requirements:
- [ ] What are the core resources?
- [ ] What operations do users need?
- [ ] What data is sensitive?
- [ ] Any third-party integrations?
- [ ] Rate limiting needs?
- [ ] Versioning strategy?

Generate:

1. RESOURCE MODEL
   For each resource:
   - Name (noun, plural)
   - Fields with types
   - Relationships to other resources
   - Ownership (who can access)

2. ENDPOINTS
   For each endpoint:
   METHOD /resource
   - What it does
   - Request: path params, query params, body
   - Response: status codes, body shape
   - Auth required?
   - Errors possible

3. DESIGN DECISIONS
   - Pagination strategy
   - Filtering/sorting approach
   - Error response format
   - Versioning method
   - Authentication method

4. EXAMPLE REQUESTS
   Show 3-5 common API calls with realistic data
```

## Example

**API Purpose:** User task management
**Users:** Solo devs, small teams

**Output:**

```
RESOURCE MODEL:

users
- id: uuid (read-only)
- email: string (unique)
- name: string
- created_at: timestamp

projects
- id: uuid
- name: string
- owner_id: uuid (FK → users)
- created_at: timestamp

tasks
- id: uuid
- title: string
- description: string?
- status: enum (todo | in_progress | done)
- project_id: uuid (FK → projects)
- assignee_id: uuid? (FK → users)
- due_date: date?
- created_at: timestamp
- updated_at: timestamp

ENDPOINTS:

GET /projects/:id/tasks
- List tasks in a project
- Query: status, assignee_id, sort, page
- Response: 200, { data: Task[], meta: pagination }
- Auth: project member

POST /projects/:id/tasks
- Create task in project
- Body: { title, description?, assignee_id?, due_date? }
- Response: 201, { data: Task }
- Auth: project member

PATCH /tasks/:id
- Update task
- Body: { title?, description?, status?, assignee_id?, due_date? }
- Response: 200, { data: Task }
- Auth: task assignee or project owner

ERROR FORMAT:
{
  "error": {
    "code": "TASK_NOT_FOUND",
    "message": "Task does not exist or you don't have access",
    "details": {}
  }
}
```

## Tips

- Resources are nouns, operations are HTTP methods
- Keep URLs flat — avoid /projects/1/tasks/1/assignees/2/owner
- Be consistent — same pattern everywhere
- Design errors as carefully as successes
- Think about the client developer experience

## Variations

**GraphQL:** Replace endpoints section with types and queries/mutations
**Webhook API:** Add outbound notification design
**Internal API:** Can skip some documentation, focus on clarity
