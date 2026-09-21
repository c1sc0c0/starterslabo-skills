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

## Install all four (Cursor, all projects)

```bash
git clone https://github.com/c1sc0c0/starterslabo-faq.git ~/.cursor/skills/starterslabo-faq
git clone https://github.com/c1sc0c0/starterslabo-eval.git ~/.cursor/skills/starterslabo-eval
git clone https://github.com/c1sc0c0/starterslabo-expenses.git ~/.cursor/skills/starterslabo-expenses
git clone https://github.com/c1sc0c0/starterlabo-invoices.git ~/.cursor/skills/starterlabo-invoices
```

Claude Code: same URLs into `~/.claude/skills/<name>`. Per-project: `.cursor/skills/` or `.claude/skills/` inside the repo.

Start a new agent chat after cloning. Setup, env vars, and usage are in each repo’s README.

## Shared rules

- Prefer `STARTERSLABO_EMAIL` / `STARTERSLABO_PASSWORD` for one crawl or Playwright run. Never commit `.env`.
- FAQ PDFs, filled evaluatiefiches, and invoice screenshots stay on your machine.
- Portal content belongs to Starterslabo; keep crawls and drafts for personal use.

## License

MIT for these skill repos. Starterslabo’s website, portal, and documents remain theirs.
