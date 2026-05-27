---
name: skill-search
description: "Search engine for discovering Codex skills on GitHub. Use when the user asks to find, search, discover, or look up a Codex skill based on needs, requirements, or functionality. Triggers on phrases like: find a skill for, search skill, is there a skill that, what skill can, skill for PDF/Excel/video, or any request to discover skills."
---

# Skill Search

Search GitHub for Codex skill repositories matching the user's needs and return repo URLs with descriptions.

## Workflow

### 1. Understand the user's need

Extract the core functionality the user wants. Translate it into 2-3 English keyword groups.

### 2. Search GitHub via AnySearch

Use the AnySearch skill to run parallel searches. Construct search queries as:

```
site:github.com "SKILL.md" codex <keywords>
site:github.com "codex skill" <keywords>
site:github.com "codex-skill" <keywords>
```

Run all three as a batch_search for efficiency. Set max_results to 5-10 per query.

### 3. Extract and deduplicate repos

From search results, extract GitHub repo URLs matching the pattern `https://github.com/<owner>/<repo>`.

- Skip repos that are not skill-related (e.g., general Codex CLI repos, unrelated projects).
- Deduplicate by repo URL.
- Prefer repos whose name or description contains keywords matching the user's need.

### 4. Present results

For each repo found, present:

- **Repo name**: `owner/repo`
- **URL**: `https://github.com/owner/repo`
- **Description**: From the search snippet or repo description
- **Relevance note**: Brief 1-sentence why it matches

If no results found, broaden the search by dropping filters and trying alternative keywords. If still nothing, honestly tell the user no matching skills were found.

### 5. Offer next steps

After presenting results, offer to install any found skill using the skill-installer:
```
skill-installer --repo owner/repo
```
