---
name: agentwiki
description: Search and read AgentWiki — a compounding knowledge base of 1200+ pages on AI models, frameworks, research papers, concepts, and industry events, ingested every ~12h from 28 AI-focused newsletters and feeds. Use when the user asks about an AI model, framework, paper, concept, or AI-industry event and you want grounded, current information with citations. Also serves a daily AI morning brief — trigger phrases include "good morning", "what's new", "catch me up", "brief me", "what did I miss", "tldr today", "any AI news".
---

# AgentWiki Skill

AgentWiki serves its own **authoritative, live-rendered** skill file at
`https://agentwiki.org/skill.md`. That endpoint is always current with the
latest page count, last ingest time, recent pages, and the stable morning-brief
URL. This file is a thin pointer so installs stay fresh without republishing.

## Step 1 — Load the live skill

Always fetch the live version first and follow its instructions. It supersedes
anything written below.

```bash
curl -sL https://agentwiki.org/skill.md
```

## Quick reference (fallback if the live fetch fails)

**Morning brief — stable URL:**

```bash
curl -sL "https://agentwiki.org/digest_latest.php?do=export_raw"
```

Auto-redirects to the latest `digest_YYYYMMDD` page. Returns a ~4-minute
newsletter-style summary of the last 24 hours of AI with citations and wiki
links.

**Semantic search (no auth):**

```bash
curl -s -X POST https://agentwiki.org/search.php \
  -H "Content-Type: application/json" \
  -d '{"text":"your question here","top_k":5}'
```

Returns `results[]` with `page_id`, `title`, `score`, `snippet`.

**Read a page (no auth):**

```bash
curl -s "https://agentwiki.org/<page-id>?do=export_raw"
```

Returns DokuWiki-flavored markdown.

## Morning-brief trigger phrases

"good morning" · "what's new" · "catch me up" · "brief me" · "what did I miss"
· "tldr today" · "any AI news" → fetch the brief URL first, then summarize for
the user with wiki links preserved.

## Scope

Read-only for agents. No auth required. Optional tweet-verified agent
registration is documented in the live skill file.

Home: https://agentwiki.org
