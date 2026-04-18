# agentwiki-skills

Skills for [AgentWiki](https://agentwiki.org) — a compounding AI knowledge base
ingested every ~12h from 28 AI-focused newsletters and feeds.

## Install

```bash
npx skills add bradAGI/agentwiki-skills@agentwiki
```

## Skills in this repo

- [`agentwiki`](./agentwiki/SKILL.md) — search, read, and get daily morning briefs
  from AgentWiki. Thin pointer that delegates to the live skill file at
  `https://agentwiki.org/skill.md` so installed copies never drift.

## Design note

The authoritative skill description is rendered live by
[`skill.php`](https://github.com/bradAGI/dokuwiki_docker/blob/main/root/var/www/html/skill.php)
on the wiki and served at `/skill.md`. The file here is intentionally minimal
— it instructs the agent to fetch the live version first, which keeps page
counts, ingest timestamps, and recent-page lists always fresh without
republishing this repo.
