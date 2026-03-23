# 🏠 Life Notes

> A personal, long-term knowledge base. Started: 2026-03-23.
> Plain Markdown + GitHub — still readable in 2036.

🌐 **Live site:** [hariharan409.github.io/life-notes](https://hariharan409.github.io/life-notes/)

---

## 📂 Sections

| Section | Purpose |
|---|---|
| [🔧 Tools](tools/_index.md) | CLI tools, apps, and software — with exact usage |
| [⚙️ Workflows](workflows/_index.md) | Repeatable processes and how-tos |
| [💡 Concepts](concepts/_index.md) | Ideas, mental models, tech concepts |
| [📅 Journal](journal/_index.md) | Time-based personal logs |

---

## 🚀 Contributing

### 1. Prerequisites

Install these once on your machine:

| Tool | Install |
|---|---|
| [Node.js](https://nodejs.org/) | `winget install OpenJS.NodeJS` / `brew install node` |
| [Hugo Extended](https://gohugo.io/) | `winget install Hugo.Hugo.Extended` / `brew install hugo` |
| [Git](https://git-scm.com/) | `winget install Git.Git` / `brew install git` |

> Hugo is a binary — it cannot be installed via `npm`. Install it once, it works forever.

### 2. Clone and install

```bash
git clone https://github.com/hariharan409/life-notes.git
cd life-notes
npm install
```

> `npm install` handles everything else in one step:
>
> - Fetches the Hugo Book theme (git submodule)
> - Wires the markdownlint pre-commit hook automatically

### 3. Run locally

```bash
hugo server
```

Site is live at **http://localhost:1313/life-notes/**. Hot-reloads on every save.

### 4. Add a new note

```bash
hugo new content tools/git.md
```

Hugo creates `content/tools/git.md` pre-filled with frontmatter and section headings.

Fill it in, then add a row to `content/tools/_index.md`.

### 5. Commit

```bash
git add .
git commit -m "notes: add git tool note"
git push
```

The pre-commit hook runs markdownlint automatically. You will see one of:

- `⏭️  No .md files staged, skipping markdownlint.`
- `✅ Markdownlint passed.`
- `❌ Markdownlint failed.` — fix the listed errors, then commit again

---

## ✅ Lint Commands

```bash
npm run lint:md        # check all .md files for issues
npm run lint:md:fix    # auto-fix what can be fixed
```

To bypass the hook in an emergency:

```bash
git commit --no-verify
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| [Hugo](https://gohugo.io/) | Static site generator |
| [Hugo Book theme](https://github.com/alex-shpak/hugo-book) | Site theme (sidebar, search, dark mode) |
| [markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2) | Markdown linting |
| [Husky](https://typicode.github.io/husky/) | Git pre-commit hook |
| [GitHub Actions](https://github.com/features/actions) | CI lint check + auto deploy to GitHub Pages |
