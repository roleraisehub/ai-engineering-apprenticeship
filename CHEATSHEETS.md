# CHEATSHEETS

For revision, not a replacement for understanding. If a line here is unfamiliar, go to GLOSSARY.md or the relevant notes.

## Terminal (zsh on macOS)

| Command | What it does |
|---|---|
| `pwd` | Print current directory |
| `ls` / `ls -a` / `ls -la` | List files / include hidden / long form with permissions and sizes |
| `cd <dir>` / `cd ~` / `cd ..` | Change directory / go home / go up one |
| `mkdir <name>` | Make a directory |
| `code .` | Open current directory in VS Code |
| `which <cmd>` | Which file runs when you type `<cmd>` |
| `echo $PATH` | Print the PATH list |
| `<tool> --version` | Verify an install |
| `uname -m` | Machine type (`arm64` = Apple silicon) |
| `cat <file>` | Print a file's contents |
| `man <cmd>` | Manual for a command (`q` to quit) |

Symbols: `~` home · `.` current dir · `..` parent dir · `/` root · `$NAME` read a variable · `-x` short flag · `--word` long flag

## Homebrew

| Command | What it does |
|---|---|
| `brew install <formula>` | Install a command-line tool |
| `brew install --cask <app>` | Install a GUI app |
| `brew list` | What's installed |
| `brew update && brew upgrade` | Refresh recipes, then upgrade everything |
| `brew doctor` | Health check |
| `brew uninstall <thing>` | Remove |

## Git (local)

| Command | What it does |
|---|---|
| `git init` | Turn this folder into a repository |
| `git status` | What's changed, staged, untracked — run constantly |
| `git add <file>` / `git add .` | Stage one file / stage everything |
| `git commit -m "message"` | Snapshot staged changes |
| `git log` / `git log --oneline` | History / compact history |
| `git diff` | Unstaged changes, line by line |
| `git config --global user.name "..."` | One-time identity setup (also `user.email`) |

Commit message rule: imperative, says what the change does. "add README", "fix PATH note" — not "changes", not "updated stuff".

## Git (remote) — filled in when we push

| Command | What it does |
|---|---|
| `git remote add origin <url>` | Register GitHub copy as `origin` |
| `git push -u origin main` | First push; `-u` remembers the pairing |
| `git push` | Every push after that |
| `git pull` | Download and merge changes from origin |

## Workflow (daily)

```
edit → git status → git add → git commit -m "..." → git push
```

Commit often, locally. Push when you want GitHub to catch up.
