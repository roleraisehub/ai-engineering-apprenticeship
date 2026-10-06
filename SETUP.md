# SETUP

What's installed on this machine, how it was verified, and what I learned doing it. If the laptop is replaced, this file is the rebuild guide.

## Machine

- MacBook Pro, Apple silicon (`uname -m` → `arm64`), 48 GB RAM
- Shell: zsh (prompt ends in `%`)
- Home: `/Users/sahilkohli`

## Installed (2026-10-06)

| Tool | How | Verify | Got |
|---|---|---|---|
| Xcode Command Line Tools | `xcode-select --install` | `git --version` | git 2.50.1 (Apple Git-155) |
| Homebrew | official install script (`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`) | `brew --version`, `brew doctor` | Homebrew 7.0.8 |
| Python | `brew install python` | `python3 --version`, `which python3` | 3.14.8 at `/opt/homebrew/bin/python3` |
| VS Code | `brew install --cask visual-studio-code` | `code --version` | 1.140.0 arm64 |

Not yet installed: Claude Code, PostgreSQL, Docker. Each gets added here when it goes in.

## Open items

- `brew doctor` warns a newer Command Line Tools release is available. Fix: System Settings → General → Software Update. Not blocking.
- Three Pythons exist on this machine: Apple's (`/usr/bin/python3`), Homebrew's (`/opt/homebrew/bin/python3`, 3.14), and one at `/Library/Frameworks/Python.framework/Versions/3.14/bin` (the python.org installer location — origin installed from python.org earlier; Homebrew's takes precedence). Homebrew's wins because it's first in PATH. Revisit if a tool ever picks the wrong one.
- Python 3.14 is very new. If a library refuses to install on it, install an older Python alongside (`brew install python@3.12`) and use that for the project. Decide per project, not globally.

## PATH on this machine

```
/opt/homebrew/bin:/opt/homebrew/sbin:/Library/Frameworks/Python.framework/Versions/3.14/bin:/usr/local/bin:...:/usr/bin:/bin:/usr/sbin:/sbin:...
```

Homebrew's entry comes from `/etc/paths.d/homebrew`, written by the installer with `sudo`. macOS builds PATH from `/etc/paths` plus everything in `/etc/paths.d/`.

## Lessons from setup

1. **PATH is an ordered list; first match wins.** `which <cmd>` shows which file actually runs. "Command not found" usually means "not in PATH," not "not installed."
2. **Stable concept vs current implementation detail.** Three version guesses were stale in one session (Homebrew 4 → actually 7; Python 3.12/3.13 → actually 3.14; the Homebrew installer's `.zprofile` step → replaced by `/etc/paths.d/`). The concepts were right every time; the keystrokes were out of date. When a tutorial doesn't match the screen, check the concept, then check current official docs.
3. **Paste the exact output.** A summary of output is a guess about the evidence.
4. **Predict, then run.** Ten seconds, and it's the difference between learning and watching.
5. **`curl | bash` is acceptable only from a source you'd trust with your laptop.** Homebrew's own GitHub, yes. A blog, no.
6. **`sudo` deserves a pause.** Know what the command writes before giving it admin rights.
