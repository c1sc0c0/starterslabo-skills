# Starters Labo skills

Unofficial [Cursor](https://cursor.com) / [Claude Code](https://code.claude.com) skills for the [mijn.starterslabo.be](https://mijn.starterslabo.be) portal.

Not affiliated with Starterslabo. You need your own login. Credentials never live in these repos.

This page is only an index. Each skill is a separate repo: clone it **as the skill folder** so `SKILL.md` sits at the root.

| Skill | What it does | Login? |
| --- | --- | --- |
| [starterslabo-faq](https://github.com/c1sc0c0/starterslabo-faq) | Crawl the portal FAQ + bijlagen and answer from a local corpus | yes |
| [starterslabo-eval](https://github.com/c1sc0c0/starterslabo-eval) | Fill the monthly evaluatiefiche Excel (`openpyxl`) | no |
| [starterslabo-expenses](https://github.com/c1sc0c0/starterslabo-expenses) | Draft **Nieuwe aankoopfactuur SL** (Playwright) | yes |
| [starterlabo-invoices](https://github.com/c1sc0c0/starterlabo-invoices) | Draft **Nieuwe verkoopfactuur** as concept (Playwright) | yes |
| [starterslabo-export](https://github.com/c1sc0c0/starterslabo-export) | Sync **Rapport** accounting tables → UTF-8 CSV | yes |
| [starterslabo-beancount](https://github.com/c1sc0c0/starterslabo-beancount) | Ingest Rapport CSVs → Beancount ledger (JSONL IR) | no* |
| [starterslabo-shopify](https://github.com/c1sc0c0/starterslabo-shopify) | Shopify paid B2C → dagontvangsten + fee onkostennota | Shopify; portal for `--apply` |
| [starterslabo-onkostennota](https://github.com/c1sc0c0/starterslabo-onkostennota) | Draft **Nieuwe onkostennota** (Playwright) | yes |
| [starterslabo-messages](https://github.com/c1sc0c0/starterslabo-messages) | Prefill / send portal **Berichten** | yes |

\*Beancount ingest reads local CSVs from the export skill (or fixtures); portal login is only needed when refreshing exports.

## Accounting pair (export + books)

`starterslabo-export` and `starterslabo-beancount` share path config (`scripts/paths.py`, `starterslabo.yaml.example`):

| Doc | Purpose |
|-----|---------|
| [export OVERVIEW](https://github.com/c1sc0c0/starterslabo-export/blob/main/docs/OVERVIEW.md) | Human pipeline for Rapport → CSV |
| [export PATHS](https://github.com/c1sc0c0/starterslabo-export/blob/main/docs/PATHS.md) | Where flat files land (CLI / env / yaml) |
| [beancount OVERVIEW](https://github.com/c1sc0c0/starterslabo-beancount/blob/main/docs/OVERVIEW.md) | Human pipeline for CSV → ledger |
| [beancount PATHS](https://github.com/c1sc0c0/starterslabo-beancount/blob/main/docs/PATHS.md) | Same resolver; `books_dir` + `export_dir` |

Defaults work out of the box (`rapport-export/` + local `books/`). Point `STARTERSLABO_DATA` or `STARTERSLABO_CONFIG` at any private folder for cron / vault layouts.

## Install (Cursor, all projects)

```bash
git clone https://github.com/c1sc0c0/starterslabo-faq.git ~/.cursor/skills/starterslabo-faq
git clone https://github.com/c1sc0c0/starterslabo-eval.git ~/.cursor/skills/starterslabo-eval
git clone https://github.com/c1sc0c0/starterslabo-expenses.git ~/.cursor/skills/starterslabo-expenses
git clone https://github.com/c1sc0c0/starterlabo-invoices.git ~/.cursor/skills/starterlabo-invoices
git clone https://github.com/c1sc0c0/starterslabo-export.git ~/.cursor/skills/starterslabo-export
git clone https://github.com/c1sc0c0/starterslabo-beancount.git ~/.cursor/skills/starterslabo-beancount
git clone https://github.com/c1sc0c0/starterslabo-shopify.git ~/.cursor/skills/starterslabo-shopify
git clone https://github.com/c1sc0c0/starterslabo-onkostennota.git ~/.cursor/skills/starterslabo-onkostennota
git clone https://github.com/c1sc0c0/starterslabo-messages.git ~/.cursor/skills/starterslabo-messages
```

Claude Code: same URLs into `~/.claude/skills/<name>`. Per-project: `.cursor/skills/` or `.claude/skills/` inside the repo.

Start a new agent chat after cloning. Setup, env vars, and usage are in each repo’s README.

## Typical chain (export → books)

```bash
# 1) Portal Rapport → CSV
~/.cursor/skills/starterslabo-export/.venv/bin/python \
  ~/.cursor/skills/starterslabo-export/scripts/sync_rapport.py --force

# 2) CSV → Beancount (needs a private books/ tree; see docs/PATHS.md)
.venv/bin/python ~/.cursor/skills/starterslabo-beancount/scripts/sync_books.py
```

## Shared rules

- Prefer `STARTERSLABO_EMAIL` / `STARTERSLABO_PASSWORD` for portal runs. Never commit `.env`.
- FAQ PDFs, filled evaluatiefiches, invoice screenshots, `shopify-sync/` dumps, Rapport CSVs, and Beancount inbox/generated stay on your machine (or a **private** data repo).
- Portal content belongs to Starterslabo; keep crawls and drafts for personal use.

## License

MIT for these skill repos. Starterslabo’s website, portal, and documents remain theirs.
