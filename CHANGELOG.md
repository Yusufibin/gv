# Changelog

All notable changes to gv are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
Versioning follows [Semantic Versioning](https://semver.org/).

---

## [1.2.0] — 2025-04-13

### Changed
- `gv diff` — complete rewrite of the diff renderer
  - replaced double `git diff` + `git diff --cached` pipe with a single `git diff HEAD` call, eliminating line number desync
  - hunk number tracking now uses a reliable `sed` expression instead of `grep -oP`
  - each hunk is visually separated with `├─ hunk N  context ──` and the function/class name extracted by git
  - file blocks wrapped in `┌─ filename ─┐` / `└──────┘` box-drawing borders
  - untracked files displayed as full green additions with correct line numbers

---

## [1.1.0] — 2025-03-20

### Added
- `gv diff` — new command to inspect changes file by file
  - lists modified files with `+added` / `-removed` line counts
  - interactive prompt: view one file by number, all with `a`, exit with `q`
  - untracked files shown as full additions
  - staged and unstaged changes displayed together

### Changed
- `gv switch` — remote branches no longer duplicated when a local tracking branch already exists
- `gv list` — `-n` flag now accepts the value attached (`-n20`) or as a separate argument (`-n 20`)

---

## [1.0.0] — 2025-02-10

### Added
- `gv switch` — numbered interactive menu to switch branches (local + remote)
- `gv full [message]` — `git add -A` + commit with optional inline message or interactive prompt
- `gv list [-n N]` — last N commits with hash, relative date, subject, and author
- `gv status` — colored file-by-file status with ahead/behind remote counters
- `gv return <hash>` — checkout to a specific commit with detached HEAD warning
- `gv help` — usage reference with examples, auto-detects current branch and commit count
