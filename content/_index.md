# 🏠 Life Notes — Home

> A personal, long-term knowledge base. Started: 2026-03-23.
> Still readable in 2036 — plain Markdown, GitHub-backed.

---

## 📂 Sections

| Section | Purpose |
|---|---|
| [🔧 Tools](tools/_index.md) | CLI tools, apps, and software — with exact usage |
| [⚙️ Workflows](workflows/_index.md) | Repeatable processes and how-tos |
| [💡 Concepts](concepts/_index.md) | Ideas, mental models, tech concepts |
| [📅 Journal](journal/_index.md) | Time-based personal logs |

---

## ⚡ Quick Start: Adding a New Tool Note

```bash
hugo new content tools/git.md
```

1. Fill in the generated file at `content/tools/git.md`
2. Add a row to [tools/_index.md](tools/_index.md)

---

## 🔗 How to Sync

```bash
# After writing notes, run:
git add .
git commit -m "notes: <what you added>"
git push
```

---

## 🛠️ Setup (fresh clone)

```bash
npm install   # installs dependencies + automatically enables the pre-commit hook
```

> The pre-commit hook runs markdownlint automatically before every commit. No extra steps needed.

---

## ✅ Markdown Lint Commands

```bash
npm run lint:md        # check all .md files for issues
npm run lint:md:fix    # auto-fix what can be fixed
```

The hook only checks **staged files**. To check everything manually, run `npm run lint:md`.

To bypass the hook in an emergency:

```bash
git commit --no-verify
```
