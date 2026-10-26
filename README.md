# AI Job Search

A skill that helps you find jobs through permitted public APIs and feeds, filter by location, work mode and seniority, score resume matches with an explainable rubric, and keep an application tracker you control.

It ships in two versions with the same behavior:

| Folder | For | Manifest |
|---|---|---|
| [`claude/`](claude) | Claude | `.claude-plugin/plugin.json` |
| [`chatgpt/`](chatgpt) | ChatGPT | `plugin.json` |

## What it does

- Searches only documented public sources (Greenhouse published boards, Arbeitnow) and records coverage and exclusions.
- Scores resume fit with a transparent heuristic: required skills 45, responsibilities 30, seniority 15, preferred 10.
- Keeps a CSV/JSON application tracker with status history. Saving a job is never treated as applying.
- Never submits applications, scrapes LinkedIn/Indeed, or sends your resume to job providers.

## Notes

- Greenhouse boards are employer-specific, so you need the board token of the company you want to search.
- Source terms change; recheck them before relying on a feed (see `skills/ai-job-search/references/sources.md`).

## License

MIT
