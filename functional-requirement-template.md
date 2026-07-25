---
id: FR-001
title: Publish a Text Post
domain: Social Platform
capability: Post Publishing

status: draft          # draft | approved | implemented | deprecated
owner: Social Platform Team

version: 0.1.0
last_updated: YYYY-MM-DD

parent:
children: []

business_rules:
  - BR-001

jira:
  - SOC-123

related_requirements: []

repositories:
  - social-api
  - web-app

releases: []

tags:
  - social-platform
  - post-publishing
---

# Functional Requirement

## Purpose

Describe the business capability this requirement provides.

---

# Intent

Explain **why** this capability exists.

- Business objective
- Customer value
- Regulatory requirement
- Operational benefit

Example:

Allow users to publish short text posts that appear on their profile and in follower timelines.

---

# Scope

## In Scope

- Creating short text posts
- Enforcing post length limits
- Publishing posts to the author's profile
- Making posts available to follower timelines

## Out of Scope

- Direct messages
- Long-form articles
- Paid promotion
- Content recommendation ranking

---

# Functional Requirement

The system shall:

FR-001

The system shall allow an authenticated user to create a text post.

FR-002

The system shall reject posts that exceed the configured character limit.

FR-003

The system shall make a successfully published post visible on the author's profile.

---

# Business Rules

### BR-001

A post must contain at least one visible character after leading and trailing whitespace is removed.

Status: implemented

---

### BR-002

A post must not exceed 280 characters.

Status: approved

---

### BR-003

Only authenticated and active users may publish posts.

Status: draft

---

# Constraints

## Business Constraints

- Post publishing rules are maintained by the Social Platform product team.
- A post is considered published only after it has been persisted successfully.

## Technical Constraints

- Server-side validation is authoritative.
- Client-side validation may provide early feedback but must not be the only enforcement layer.

---

# Inputs

| Input | Description |
|--------|-------------|
| Author ID | Identifier of the authenticated user |
| Post Text | Text content submitted by the user |
| Client Timestamp | Optional timestamp supplied by the client |

---

# Outputs

| Output | Description |
|--------|-------------|
| Post | Newly created post record |
| Publish Result | Success or failure |
| Error Code | Machine-readable error |

---

# Dependencies

## Requirements

- FR-010 User Account Status

## External Services

- User Account Service
- Timeline Distribution Service

## Policies

- Community Guidelines
- Post Publishing Policy

---

# Non-functional Considerations

## Performance

Post publishing should complete within acceptable interactive response time.

## Reliability

A successful publish request must not create duplicate posts when the same idempotency key is retried.

## Auditability

Post creation and rejection events should be traceable.

---

# References

- Policy documents
- Architecture Decision Records
- API specifications

---

# Delivery Notes (Informational Only)

These notes help engineers and AI agents understand delivery context.

## Planned Jira Changes

- SOC-123
- SOC-145

## Expected Repositories

- social-api
- web-app

---

# Progress Log

## YYYY-MM-DD

Initial draft created.

---

# Open Questions

- Should URLs count toward the character limit using their raw length or a fixed length?
- Should users be able to publish replies before reply functionality is formally introduced?

---

# Future Considerations

Potential future enhancements.

- Media attachments
- Scheduled posts
- Hashtags and mentions
- Post editing

---

# Authoring Principles

This document intentionally contains only **long-lived knowledge**.

Included:

- Intent
- Functional Requirements
- Business Rules
- Constraints
- References

Not included:

- Sprint planning
- Acceptance Criteria
- Developer tasks
- Temporary implementation notes
- Agent execution plans

Those belong in Jira or an AI task execution layer (for example Beads or a future SQLite-based agent task store).
