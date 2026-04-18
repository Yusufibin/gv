![screenshot](https://raw.githubusercontent.com/Yusufibin/gv/refs/heads/main/screen.png)

# gv — git, short version

A bash wrapper around git that replaces the most frequent commands with readable, interactive interfaces.

```
$ gv status

  Status  branch: main  → 2 to push

  ~  src/app.js                           modified
  +  src/utils/format.js                  new (untracked)
  ✗  tests/old.test.js                    deleted

  ············································
  ~1   modified     +1   new     ✗1   deleted

  → gv full to commit · gv diff to inspect
```

---

## Installation

**Quick install**

```bash
curl -fsSL https://raw.githubusercontent.com/Yusufibin/gv/main/gv \
  -o /usr/local/bin/gv && chmod +x /usr/local/bin/gv
```

**Manual install**

```bash
git clone https://github.com/Yusufibin/gv.git
cp gv/gv /usr/local/bin/gv
chmod +x /usr/local/bin/gv
```

**Requirements**: bash 4+,zsh, git 2.x — nothing else.

---

## Commands

| Command | Description |
|---|---|
| `gv switch` | interactive branch navigation |
| `gv full [message]` | `git add -A` + commit in one step |
| `gv list [-n N]` | list the last N commits (default: 5) |
| `gv status` | colored, readable repository state |
| `gv diff` | inspect changes file by file |
| `gv return <hash>` | go back to a specific commit |

---

## Examples

```bash
# Pick a branch from a numbered menu
gv switch

# Stage everything and commit
gv full "feat: add dark mode"

# Show the last 20 commits
gv list -n 20

# Inspect changes before committing
gv diff

# Go back to a specific commit (files are kept)
gv return a3f9c12
```

### gv diff — output

```
┌── src/app.js ──────────────────────────────────────────────┐

  ├─ hunk 1  function render() ──────────────────────────────
      42    const el = document.querySelector('#app')
  -         el.innerHTML = data
  +   43    el.textContent = data
      44    return el

└────────────────────────────────────────────────────────────┘
```

### gv switch — output

```
Available branches

   1)  main  ← current
   2)  feat/dark-mode
   3)  fix/typo-readme

Number (q to cancel):
```

---

## Why gv?

Git is powerful but verbose. Day-to-day operations — committing, switching branches, reviewing history — require too much typing for tasks repeated dozens of times a day.

`gv` does not replace git. It just covers the most common workflow with less noise.

---

## Contributing

PRs are welcome, especially for:

- new commands consistent with the spirit of the script
- bug fixes on git edge cases
- bash compatibility improvements (macOS, alternative distros)

For new commands, open an issue first to discuss whether it fits the philosophy before writing any code.

---

