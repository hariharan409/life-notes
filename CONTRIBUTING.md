# 🤝 Contributing

Thanks for your interest in contributing to Life Notes!

---

## 1. Prerequisites

You need **Git** and **Node.js** — both are standard dev tools likely already on your machine.

The only one you may need to install separately is **Hugo Extended**:

```bash
winget install Hugo.Hugo.Extended  # Windows
brew install hugo                  # macOS
```

> Hugo is a compiled binary — it cannot be installed via `npm`. Install it once, it works forever.

---

## 2. Clone and install

```bash
git clone https://github.com/hariharan409/life-notes.git
cd life-notes
npm install
```

`npm install` handles everything else automatically:

- Fetches the Hugo Book theme (git submodule)
- Wires the markdownlint pre-commit hook via Husky

---

## 3. Run locally

```bash
hugo server
```

Site is live at **http://localhost:1313/life-notes/**. Hot-reloads on every save.

---

## 4. Add a new note

```bash
hugo new content tools/git.md
```

Hugo creates `content/tools/git.md` pre-filled with frontmatter and section headings.

Fill it in, then add a row to `content/tools/_index.md`.

---

## 5. Commit

```bash
git add .
git commit -m "notes: add git tool note"
git push
```

The pre-commit hook runs markdownlint automatically on staged `.md` files:

- `⏭️  No .md files staged, skipping markdownlint.`
- `✅ Markdownlint passed.`
- `❌ Markdownlint failed.` — fix the listed errors, then commit again

---

## Lint Commands

```bash
npm run lint:md        # check all .md files
npm run lint:md:fix    # auto-fix what can be fixed
```

Emergency bypass:

```bash
git commit --no-verify
```
