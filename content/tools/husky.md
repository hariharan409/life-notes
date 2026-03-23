---
tags: [tool, git-hooks, pre-commit, code-quality, javascript]
tool_name: Husky
category: Git Hooks / Code Quality
version_noted: v9.1.7
last_used: 2026-03-23
os: [windows, mac, linux]
---

# 🔧 Husky

> A tool that makes git hooks easy to share across a team. Hooks are stored in the repo (`.husky/`) and automatically activated when anyone runs `npm install` — no manual `git config` needed.

---

## 📦 Install

```bash
npm install --save-dev husky
npx husky init
```

`husky init` does two things:

1. Adds a `prepare` script to `package.json`
2. Creates a default `.husky/pre-commit` file

---

## ✅ Core Use Cases

- Run linters before every commit (e.g. markdownlint, ESLint)
- Run tests before pushing
- Enforce commit message format (with `commitlint`)
- Ensure no contributor can accidentally skip hooks — hook setup is automatic via `npm install`

---

## 🔑 Key Usage

### How it works

```text
git clone <repo>
cd <repo>
npm install
  └── triggers "prepare" script in package.json
        └── runs "husky"
              └── sets git core.hooksPath = .husky/_ automatically
```

No manual `git config` needed — ever.

---

### The `prepare` script in `package.json`

```json
{
  "scripts": {
    "prepare": "husky"
  }
}
```

This is what makes hooks auto-install. `prepare` runs automatically after `npm install`.

---

### Adding a hook

Hooks live in `.husky/` as plain shell scripts:

```text
.husky/
  pre-commit      ← runs before every git commit
  pre-push        ← runs before every git push
  commit-msg      ← runs to validate commit messages
```

Example `.husky/pre-commit` that runs markdownlint on staged `.md` files:

```sh
#!/bin/sh

STAGED_MD=$(git diff --cached --name-only --diff-filter=ACM | grep '\.md$')

if [ -z "$STAGED_MD" ]; then
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

---

### Bypass a hook (emergency only)

```bash
git commit --no-verify
git push --no-verify
```

---

## ⚙️ Config / Setup

No config file — Husky is configured entirely through:

1. The `prepare` script in `package.json`
2. Shell scripts in `.husky/`

---

## ⚠️ Gotchas & Notes

- **Husky v8 vs v9** — breaking change in setup. v9 uses `.husky/_/` internally and simplified `npx husky init`. Old tutorials may show `npx husky install` (v8 syntax — doesn't work in v9).
- `prepare` does NOT run in CI environments (when `NODE_ENV=production`). This is intentional — hooks are for local dev only. CI should have its own lint step.
- On Windows, hooks run via Git's bundled shell (sh/bash). Scripts must use Unix line endings (LF not CRLF). Add `.husky/pre-commit` to `.gitattributes` if needed:

  ```text
  .husky/pre-commit eol=lf
  ```

- If `npm run prepare` was run before hooks were fully set up, run `npm run prepare` manually once to re-wire.

---

## 🔗 Related Tools

- [markdownlint-cli2.md](markdownlint-cli2.md) — the linter used in the pre-commit hook
- [eslint.md](eslint.md) — another common tool to run in pre-commit

## 📎 Official Links

- Docs: https://typicode.github.io/husky/
- GitHub: https://github.com/typicode/husky
- Migration v8 → v9: https://typicode.github.io/husky/migrating-from-v4.html
