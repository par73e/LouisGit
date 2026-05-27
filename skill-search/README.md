# Skill Search

Search engine for discovering Codex skills on GitHub. Describe your needs and it finds matching skill repositories for you.

## How It Works

Uses AnySearch to run parallel GitHub searches with skill-specific queries, then deduplicates and ranks results by relevance.

## Triggers

- "find a skill for..."
- "search skill that..."
- "is there a skill that..."
- "what skill can..."

## Dependencies

- [AnySearch](https://github.com/anthropics/skills/tree/main/anysearch) — used for web / GitHub search

## Install

```
skill-installer --repo par73e/LouisGit --path skill-search --name skill-search
```
