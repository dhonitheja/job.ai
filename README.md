# AI Job Search

A skill that helps you find jobs through permitted public APIs and feeds, filter by location, work mode and seniority, score resume matches with an explainable rubric, and keep an application tracker you control.

It ships in two versions with the same behavior:

| Folder | For | Manifest |
|---|---|---|
| [`claude/`](claude) | Claude | `.claude-plugin/plugin.json` |
| [`chatgpt/`](chatgpt) | ChatGPT | `plugin.json` |

## Install

### Claude.ai (web or desktop app)

1. Download [`ai-job-search.zip`](ai-job-search.zip) from this repo. It contains the skill folder `ai-job-search/` with `SKILL.md` inside. (To build it yourself, zip `claude/skills/ai-job-search/` and keep the folder name.)
2. Go to **Settings > Capabilities** and turn on **Code execution and file creation**.
3. In the **Skills** section, click **Upload skill**, choose the zip, and toggle the skill on.

Available on Pro, Max and Team plans. On Enterprise, an Owner must enable skills first. Uploaded skills are private to your account. See [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude).

### Claude Code (terminal)

Install from this repo as a marketplace:

```bash
claude plugin marketplace add dhonitheja/job.ai
claude plugin install ai-job-search@job-ai
```

Or try it for one session from a clone:

```bash
git clone https://github.com/dhonitheja/job.ai
claude --plugin-dir ./job.ai/claude
```

To keep just the skill without the plugin, copy the folder instead:

```bash
mkdir -p ~/.claude/skills
cp -r job.ai/claude/skills/ai-job-search ~/.claude/skills/
```

See the [Claude Code plugin docs](https://code.claude.com/docs/en/plugin-marketplaces.md).

### ChatGPT

The [`chatgpt/`](chatgpt) folder is the original ChatGPT package (`plugin.json` plus `skills/`). It has not been tested here; follow OpenAI's current documentation for installing plugin or skill packages.

### Meta Muse and other assistants

Muse's support for installable skills is not confirmed by Meta. Instead, paste the contents of [`muse/ai-job-search-muse.md`](muse/ai-job-search-muse.md) into a chat and ask the assistant to follow it. It is the same skill merged into one file, and it has not been tested in Muse.

## Use it

Try prompts like:

- "Find backend engineer jobs on the Greenhouse board `<company-token>` that are remote in the US."
- "Compare my resume (attached) against these three roles and explain the scores."
- "Add this job to my tracker as saved."

## What it does

- Searches only documented public sources (Greenhouse, Lever and Ashby employer boards, Arbeitnow) plus Indeed or Dice if you have those connectors connected, and records coverage and exclusions.
- Tailors resume bullets and cover letters on request, using only facts your resume supports.
- Scores resume fit with a transparent heuristic: required skills 45, responsibilities 30, seniority 15, preferred 10.
- Keeps a CSV/JSON application tracker with status history. Saving a job is never treated as applying.
- Never submits applications, scrapes LinkedIn/Indeed, or sends your resume to job providers.

## Notes

- Greenhouse, Lever and Ashby boards are employer-specific, so you need the board name of each company you want to search. The skill explains how to find it from a careers-page link; it never guesses.
- The Indeed and Dice connector support is untested here and depends on those connectors being connected in your account.
- Source terms change; recheck them before relying on a feed (see `skills/ai-job-search/references/sources.md`).

## License

MIT
