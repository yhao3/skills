---
name: commit-message-helper
description: Helps write Git commit messages following the Conventional Commits specification. Use this skill when the user asks to commit changes, write commit messages, or mentions git commits.
---

# Commit Message Helper

When writing commit messages, follow these rules:

## Format

<subject>

<body>

<footer> // optional

## Guidelines

1. Subject line should be no longer than 50 characters
2. Use imperative mood ("Add feature" not "Added feature")
3. Do not end the subject line with a period
4. Separate subject from body with a blank line
5. Use the body to explain what and why, not how
6. Do NOT overly verbose descriptions or unnecessary details
7. Do NOT use markdown syntax e.g. `inline-block`
8. Do NOT add . in the end of subject

## Examples

Good:
Add OAuth2 login support

Implement OAuth2 authentication flow to allow users to log in
with their Google or GitHub accounts.

Bad:
Updated stuff