---
tags: [tool, linter, markdown, code-quality, pre-commit, ci]
tool_name: markdownlint-cli2
category: Linter / Code Quality
version_noted: v0.17.2 (markdownlint v0.37.4)
last_used: 2026-03-24
os: [windows, mac, linux]
---

# 🔧 markdownlint-cli2

> A fast CLI tool to lint Markdown files against a set of rules. Catches bad formatting, missing code block languages, trailing spaces, and inconsistent structure — before they reach GitHub.

---

## 📦 Install

```bash
npm install --save-dev markdownlint-cli2
```

Requires Node.js. No global install needed — use via `npx` or `npm run` scripts.

---

## ✅ Core Use Cases

- Enforce consistent Markdown formatting across all `.md` files
- Block bad commits via a git pre-commit hook (via Husky)
- Fail CI/CD pipelines on unformatted Markdown
- Auto-fix many common issues with `--fix`

---

## 🔑 Key Commands / Usage

### Check all Markdown files

```bash
npm run lint:md
# or directly:
npx markdownlint-cli2 "**/*.md" "#node_modules" "#themes" "#public"
```

**What it does:** Scans all `.md` files, prints violations with file + line number.

---

### Auto-fix fixable issues

```bash
npm run lint:md:fix
# or directly:
npx markdownlint-cli2 --fix "**/*.md" "#node_modules" "#themes" "#public"
```

**What it does:** Automatically fixes trailing spaces, blank lines around fences, multiple blank lines. Does NOT fix missing code block languages — those need manual attention.

---

### What `--fix` can and cannot fix

| Rule | Auto-fixed? |
|---|---|
| `MD009` trailing spaces | ✅ |
| `MD012` multiple blank lines | ✅ |
| `MD031` blank lines around fences | ✅ |
| `MD040` missing code block language | ❌ Must be added manually |

---

## ⚙️ Config / Setup

### `package.json` scripts

```json
{
  "scripts": {
    "lint:md": "markdownlint-cli2 \"**/*.md\" \"#node_modules\" \"#themes\" \"#public\"",
    "lint:md:fix": "markdownlint-cli2 --fix \"**/*.md\" \"#node_modules\" \"#themes\" \"#public\""
  },
  "devDependencies": {
    "markdownlint-cli2": "^0.17.0"
  }
}
```

> `#themes` and `#public` exclude the Hugo theme submodule and build output from linting.

---

### `.markdownlint.json` — rules config (relaxed for notes)

```json
{
  "MD013": false,
  "MD033": false,
  "MD034": false,
  "MD041": false,
  "MD007": { "indent": 2 },
  "MD009": true,
  "MD012": { "maximum": 2 },
  "MD022": true,
  "MD025": true,
  "MD031": true,
  "MD032": true
}
```

| Rule | What it does | Enabled? |
|---|---|---|
| `MD013` | Max line length (80 chars) | ❌ Off — too strict for notes |
| `MD033` | No inline HTML | ❌ Off — useful in notes |
| `MD034` | No bare URLs | ❌ Off — notes have plain links |
| `MD041` | First line must be H1 | ❌ Off — frontmatter comes first |
| `MD009` | No trailing spaces | ✅ |
| `MD012` | Max 2 consecutive blank lines | ✅ |
| `MD022` | Blank lines around headings | ✅ |
| `MD025` | Only one H1 per file | ✅ |
| `MD031` | Blank lines around fences | ✅ |
| `MD032` | Blank lines around lists | ✅ |

---

### Pre-commit hook (via Husky) — `.husky/pre-commit`

The hook is managed by Husky and auto-installs via `npm install`. See [husky.md](husky.md).

```sh
#!/bin/sh

STAGED_MD=$(git diff --cached --name-only --diff-filter=ACM | grep '\.md$' || true)

if [ -z "$STAGED_MD" ]; then
  echo "⏭️  No .md files staged, skipping markdownlint."
  exit 0
fi

echo "🔍 Running markdownlint on staged files..."
echo "$STAGED_MD" | xargs npx markdownlint-cli2

if [ $? -ne 0 ]; then
  echo ""
  echo "❌ Markdownlint failed. Fix the issues above before committing."
  echo "   To skip (not recommended): git commit --no-verify"
  exit 1
fi

echo "✅ Markdownlint passed."
exit 0
```

> `|| true` after `grep` prevents exit code 1 from propagating when no `.md` files are staged.

---

### GitHub Actions CI — `.github/workflows/lint.yml`

```yaml
name: Lint Markdown

on: [push, pull_request]

jobs:
  markdownlint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install
      - run: npm run lint:md
```

Blocks any PR that has Markdown violations — cannot be bypassed unlike the local hook.

---

## ⚠️ Gotchas & Notes

- `package-lock.json` must be committed — required for CI `npm install` to work.
- `--fix` is safe to run anytime — it only touches fixable issues and doesn't change content/meaning.
- To bypass the hook in an emergency: `git commit --no-verify` (use sparingly).
- `#themes` and `#public` must be excluded or the Hugo theme's own markdown files get linted.

---

## 🔗 Related Tools

- [husky.md](husky.md) — manages the pre-commit hook
- [eslint.md](eslint.md) — same concept but for JavaScript/TypeScript

## 📎 Official Links

- GitHub: https://github.com/DavidAnson/markdownlint-cli2
- Rules reference: https://github.com/DavidAnson/markdownlint/blob/main/doc/Rules.md
- VS Code extension: https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint
