---
tags: [tool, linter, javascript, typescript, code-quality]
tool_name: ESLint
category: Linter / Code Quality
version_noted: v9.x (flat config era)
last_used: 2026-03-23
os: [windows, mac, linux]
---

# 🔧 ESLint

> A static code analysis tool for JavaScript and TypeScript. Catches bugs, enforces code style, and flags bad patterns — before you run the code.

---

## 📦 Install

```bash
# Install locally in a project (recommended)
npm install --save-dev eslint

# Initialize config (interactive setup)
npx eslint --init
```

> ⚠️ As of ESLint v9, the config format changed from `.eslintrc.*` to `eslint.config.js` (flat config). Most tutorials online still show the old format — check the version.

---

## ✅ Core Use Cases

- Catch bugs early (undefined variables, unused imports, unreachable code)
- Enforce consistent code style across a team
- Integrate with VS Code for real-time red underlines
- Run in CI/CD to block bad code from merging
- Works with JavaScript, TypeScript, JSX, TSX, Vue, etc.

---

## 🔑 Key Commands / Usage

### Lint a file or folder

```bash
npx eslint src/
npx eslint src/index.js
```

**What it does:** Scans files and prints all rule violations with line numbers.

---

### Auto-fix fixable issues

```bash
npx eslint src/ --fix
```

**What it does:** Automatically fixes issues it can (formatting, unused vars in some cases). Does NOT fix everything — complex issues still need manual fixes.

---

### Lint only specific file types

```bash
npx eslint src/ --ext .js,.ts,.tsx
```

---

### Ignore files

Create a `.eslintignore` file:

```text
node_modules/
dist/
build/
*.min.js
```

> In v9 flat config, ignores go inside `eslint.config.js` instead.

---

### Check your config is working

```bash
npx eslint --print-config src/index.js
```

**What it does:** Dumps the resolved config for a specific file — useful for debugging why a rule isn't applying.

---

## ⚙️ Config / Setup

### Old format (v8 and below) — `.eslintrc.json`

```json
{
  "env": { "browser": true, "es2021": true },
  "extends": ["eslint:recommended"],
  "rules": {
    "no-unused-vars": "warn",
    "no-console": "off"
  }
}
```

### New format (v9+) — `eslint.config.js`

```js
import js from "@eslint/js";

export default [
  js.configs.recommended,
  {
    rules: {
      "no-unused-vars": "warn",
      "no-console": "off"
    }
  }
];
```

### VS Code integration

Install the **ESLint extension** (`dbaeumer.vscode-eslint`) and add to `.vscode/settings.json`:

```json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  }
}
```

This auto-fixes on every save.

---

## ⚠️ Gotchas & Notes

- **v8 vs v9 config format** — breaking change. If you see `.eslintrc.js` in a project, it's using old format. `eslint.config.js` = new flat config.
- `--fix` only fixes "fixable" rules — not all violations can be auto-fixed
- ESLint is for **logic/style rules**. Use **Prettier** separately for pure formatting (spaces, line width). They can conflict — use `eslint-config-prettier` to disable formatting rules in ESLint when using both together.
- TypeScript needs extra setup: `@typescript-eslint/parser` + `@typescript-eslint/eslint-plugin`

---

## 🔗 Related Tools

- [prettier.md](prettier.md) — code formatter, often used alongside ESLint
- [typescript.md](typescript.md) — needs `@typescript-eslint` plugin to lint `.ts` files

## 📎 Official Links

- Docs: https://eslint.org/docs/latest/
- Config migration (v8 → v9): https://eslint.org/docs/latest/use/configure/migration-guide
- VS Code Extension: https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint

```
