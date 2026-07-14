# CLAUDE.md

This file provides guidance to Claude Code (`claude.ai/code`) when working in this repository.

## What this directory actually is

This is **not a software project repository**.
`C:\Users\shint\.codex` is the home directory of the **OpenAI Codex CLI** (`CODEX_HOME`), and it is also used as the owner's personal **work-and-publish workspace**. Two very different things live side by side here:

1. **Codex machine state**
   `config.toml`, `sessions/`, `plugins/`, `skills/`, `memories/`, `rules/default.rules`, `*.sqlite*`, `auth.json`, `.sandbox*`, `.tmp/`, `node_repl/`, `computer-use/`, `installation_id`

   These are managed by the Codex runtime.
   **Do not hand-edit, refactor, reorganize, or "clean up" these files or folders.**
   They are not source code.

   `rules/default.rules` is especially important: it is an auto-generated command allow-list, not a document to manually rewrite.

2. **The owner's actual work and published website**
   Markdown/HTML deliverables, project folders, templates, assets, and related working documents.

   This is where normal task work happens.

Almost the entire directory is ignored by git (see `.gitignore`).
Only a small set of outward-facing published files is tracked in git.

## Read this before writing anything

The owner is **Jay Jung** (`kevin@shints.com`), Planning Team Head at **SHINTS Co., Ltd.**
SHINTS is a global garment OEM/ODM manufacturer with Korea HQ, **BVT** in Vietnam, and **ETP** in Ethiopia.

Typical deliverables include:

- ESG reports
- buyer-facing documents
- board and executive reports
- infographics
- market and business analysis
- company introduction and investor materials

## Highest-priority context

**`AGENTS.md` is the authoritative context file and must be read before drafting content.**

Use `AGENTS.md` as the primary source for:

- user profile and working preferences
- company and entity facts (`SHINTS`, `BVT`, `ETP`)
- ESG context and messaging direction
- tone, style, and writing preferences
- preferred Korean and English expression style

If this file and `AGENTS.md` appear to differ, **follow `AGENTS.md`** for user context, tone, and writing behavior.

## Default language

Default to **Korean** for responses, summaries, progress updates, and working notes unless the user asks otherwise. For everything else about tone, style, and English/Korean wording preferences, follow `AGENTS.md` (see above) rather than duplicating it here.

## Workspace conventions

Working files follow the numbered-folder flow described in `README_WORKSPACE.md`:

- `00_inbox/` -> newly received files land here first
- `10_projects/` -> active projects, each usually in a `YYYYMMDD_name` folder
- `20_templates/` -> reusable HTML/Markdown templates
- `30_assets/` -> images and static resources
- `40_logs/` -> logs
- `90_archive/` -> finished work

Most deliverables are:

- self-contained single-file HTML documents
- Markdown documents
- report-style visual documents
- infographic-style pages

Many HTML outputs are `lang="ko"`.
Some use Tailwind from `https://cdn.tailwindcss.com`; others are fully inline.
The main output format here is usually **reports and presentation-style content**, not application code.

## Safe editing vs. do-not-touch areas

Safe to edit when the task requires it:

- tracked HTML files
- report or deliverable Markdown files
- project folders under the workspace flow
- templates and content assets related to deliverables

Do not edit unless the user explicitly asks and the reason is clear:

- Codex runtime state
- authentication files
- session history
- generated rule files
- sqlite databases
- sandbox or temporary machine files

Do not perform cleanup or restructuring just because something looks unused.

## Deployment: this git repo is also a live site

Tracked published files are deployed through **GitHub Pages** to **`shints-lab.pro`** via `CNAME`.
The remote repository is `JayJUNG15/shints` and the main branch is `main`.

Tracked files include:

- `index.html` as the hub page
- a small set of published report HTML files
- `CNAME`

Editing one of those tracked HTML files and pushing to `main` updates the public website.
Treat all tracked published-file edits as **external-facing changes**.

Commit only when asked.
When a commit is needed in this repository, write the commit message in **Korean**.

There is no build, test, or lint pipeline here.
Files are static.
To preview a report, open the HTML directly in a browser.

## Environment

- OS: **Windows 11**
- Default shell: **PowerShell**
- Bash may also be available for POSIX-style scripts

When writing Korean text to files, be careful with encoding.
Use **UTF-8 explicitly** when needed, for example with PowerShell `-Encoding utf8`.

Ad-hoc data pulls in this workspace often use:

- UN Comtrade (`data.un.org`)
- World Bank APIs
- PowerShell `Invoke-WebRequest`
- PowerShell `Invoke-RestMethod`

Downloaded or temporary data should go under `data/` and is typically gitignored.
