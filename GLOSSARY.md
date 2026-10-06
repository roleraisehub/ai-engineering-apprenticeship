# GLOSSARY

Every important term we meet, in the order we meet it. Each entry: one-line definition, beginner explanation, example, related terms.

Rule: if you can't explain an entry without reading it, you don't know it yet.

---

## Terminal

**One line:** The app that lets you type commands to your computer instead of clicking.

**Beginner:** A text window. You type a command, press Enter, the computer does it and prints a result. Everything a developer installs, runs, or tests goes through here.

**Example:** `ls` prints the files in the current folder.

**Related:** shell, prompt, command, flag

## Shell (zsh)

**One line:** The program inside the terminal that reads your commands and runs them.

**Beginner:** Terminal is the window; the shell is the interpreter living in it. On a modern Mac the shell is **zsh**; you can tell because the prompt ends in `%`.

**Example:** `~/.zprofile` is a file zsh reads every time a new terminal opens.

**Related:** Terminal, prompt, PATH, dotfile

## Prompt

**One line:** The text the shell shows when it's waiting for you to type.

**Beginner:** `sahilkohli@sahils-MacBook-Pro ~ %` — user, machine, current folder, and `%` meaning "ready."

**Related:** shell

## Flag

**One line:** An option passed to a command to change what it does.

**Beginner:** Short flags are one dash and one letter (`-m`, `-a`); long flags are two dashes and a word (`--version`, `--install`). `--version` works on nearly every tool and is how you verify an install.

**Example:** `ls -a` lists all files including hidden ones; `uname -m` prints the machine type.

**Related:** command

## Path (file path)

**One line:** The address of a file or folder on disk.

**Beginner:** `/Users/sahilkohli/ai-engineering-apprenticeship/README.md` — start at the root `/`, walk down each folder, end at the file. `.` means the current folder, `..` means the parent, `~` means your home directory.

**Related:** home directory, PATH (different thing — see below)

## Home directory (`~`)

**One line:** Your personal folder; where every terminal starts.

**Beginner:** `/Users/sahilkohli`. `~` is shorthand for it. `cd ~` always takes you home.

**Related:** path, dotfile

## PATH

**One line:** The ordered list of folders the shell searches, left to right, to find a command you type.

**Beginner:** The shell's address book. When you type `python3`, the shell checks each folder in PATH in order and runs the **first** `python3` it finds. "Command not found" almost always means "not in PATH," not "not installed." `which <command>` tells you which file actually runs.

**Example:** `echo $PATH` prints it. On this machine `/opt/homebrew/bin` comes before `/usr/bin`, so Homebrew's Python wins over Apple's.

**Related:** environment variable, which, /etc/paths.d

## Environment variable

**One line:** A named value the shell keeps and makes available to every program it runs.

**Beginner:** Like a variable in Python, but for the whole terminal session. `PATH` is one. Later, `ANTHROPIC_API_KEY` will be one. `$NAME` reads the value.

**Example:** `echo $PATH`

**Related:** PATH, secrets (later)

## Dotfile

**One line:** A file or folder whose name starts with `.`; hidden by default.

**Beginner:** `.git`, `.zprofile`, `.gitconfig`, `.venv` are all dotfiles. `ls -a` shows them. Hidden doesn't mean unimportant — `.git` *is* your repository.

**Related:** shell, Git

## Command Line Tools (Xcode CLT)

**One line:** Apple's minimal developer toolkit — compilers, Git, and friends.

**Beginner:** Installed with `xcode-select --install`. Required by Homebrew and by many Python packages. Not the same as the 10 GB Xcode app.

**Related:** Homebrew, Git

## sudo

**One line:** Run a command as the superuser (administrator).

**Beginner:** "Superuser do." Needed when a command writes to system folders. Asks for your Mac password; nothing shows as you type it. Be suspicious of any tutorial that tells you to `sudo` something you don't understand.

**Related:** Terminal

## Package manager

**One line:** A tool that installs, updates, and removes software from the command line.

**Beginner:** An App Store for developer tools. On Mac it's **Homebrew**; Python has its own (`pip`, later `uv`); JavaScript has `npm`.

**Example:** `brew install python`

**Related:** Homebrew, formula, cask

## Homebrew (brew)

**One line:** The package manager for macOS.

**Beginner:** Installs into `/opt/homebrew` on Apple silicon. Vocabulary: a **formula** is a recipe for a command-line tool; a **cask** is a recipe for a GUI app (`brew install --cask visual-studio-code`); a **bottle** is a pre-built binary so your machine doesn't compile; a **tap** is a catalog of recipes. `brew doctor` checks the install.

**Related:** package manager, PATH

## curl

**One line:** A command that downloads from a URL.

**Beginner:** `curl -fsSL <url>` fetches a file quietly. The pattern `bash -c "$(curl ... )"` means "download a script and run it" — acceptable from Homebrew's official GitHub, dangerous from a random blog.

**Related:** Terminal, security

## Interpreter

**One line:** A program that reads source code and executes it line by line.

**Beginner:** `python3` is the Python interpreter. You write `hello.py`; the interpreter runs it. Different from a compiler, which translates the whole program first.

**Related:** Python

## Python

**One line:** The programming language we use for everything in this apprenticeship.

**Beginner:** Readable, general-purpose, the standard language for data and AI engineering. On this machine there are three copies; Homebrew's (`/opt/homebrew/bin/python3`, 3.14) is the one that runs because it's first in PATH.

**Related:** interpreter, PATH, virtual environment (Day 1)

## Variable

**One line:** A name that refers to a value.

**Beginner:** `x = 5` makes `x` refer to `5`. Not "temporary" — it lives as long as the code that owns it (we'll cover *scope* on Day 2).

**Related:** string, dictionary

## String

**One line:** Text, written inside quotes.

**Beginner:** `"age"` is a string. `age` without quotes is a *variable name*. `person[age]` looks up a variable called `age` (which doesn't exist → error); `person["age"]` looks up the key `"age"`. This bug came up in the diagnostic. It will come up again.

**Related:** variable, dictionary

## Dictionary (dict)

**One line:** A collection of key → value pairs.

**Beginner:** `person = {"name": "Ana", "age": 31}`. Look up with `person["age"]` → `31`. JSON looks almost identical, which is why Python and APIs get along.

**Related:** JSON, string

## Function

**One line:** A named, reusable block of code that takes inputs and returns an output.

**Beginner:**
```python
def add(x, y):
    return x + y
```
`def` defines it, `x, y` are parameters, `return` hands the result back. Day 1 topic.

**Related:** variable

## Git

**One line:** A program that saves snapshots of a folder so you can track, compare, and undo changes.

**Beginner:** Lives on your laptop. The `.git` folder inside a project holds every snapshot. Git never touches the internet unless you tell it to (`push`/`pull`).

**Related:** repository, commit, GitHub

## Repository (repo)

**One line:** A folder Git is watching, plus its full history.

**Beginner:** `git init` turns a plain folder into one by creating `.git`. Delete `.git` and the history is gone.

**Related:** Git, commit

## Commit

**One line:** A saved snapshot of the repository at a moment you chose.

**Beginner:** A save point. Has a unique **hash** (long hex ID), an author, a date, and a message. Message rule: imperative, says what the change does — "add README," not "changes."

**Example:** `git commit -m "Initial commit: add README"`

**Related:** staging area, hash, git log

## Staging area

**One line:** The set of changes that will go into the *next* commit.

**Beginner:** `git add <file>` puts a file in the box; `git commit` seals the box. Two steps so you can choose which changes belong together. `git status` shows what's staged (green) vs unstaged/untracked (red).

**Related:** commit

## Remote

**One line:** A named address of another copy of your repository, usually on GitHub.

**Beginner:** `origin` is the conventional name for the main remote. `git push` uploads your commits there; `git pull` downloads theirs. Until you add a remote and push, your repo exists only on your laptop.

**Related:** GitHub, commit

## GitHub

**One line:** A website that hosts copies of Git repositories.

**Beginner:** Git is the tool; GitHub is a place. Commit = save the game locally; push = upload the save to the cloud.

**Related:** Git, remote

## Markdown (.md)

**One line:** Plain-text formatting: `#` for headings, `-` for bullets, backticks for code.

**Beginner:** Every README, every doc in this repo. GitHub renders it. This glossary is Markdown.

**Related:** README

## API

**One line:** A contract that lets two programs talk to each other.

**Beginner:** "Application Programming Interface." Your code sends a request in an agreed format; the other system sends a response. Weather services, payment processors, and Claude all expose APIs. Week 1 topic.

**Related:** HTTP, JSON

## HTTP

**One line:** The protocol browsers and APIs use to send requests and receive responses.

**Beginner:** Your browser sends an HTTP *request* ("GET me this page"); the server sends an HTTP *response* (the page plus a status code like 200 OK or 404 Not Found). API calls are the same mechanism, used by programs.

**Related:** API, JSON

## JSON

**One line:** A text format for structured data, made of key/value pairs, lists, strings, and numbers.

**Beginner:** `{"name": "Ana", "age": 31}`. Looks like a Python dict because it's nearly the same thing. The universal language of APIs.

**Related:** API, dictionary

## Database

**One line:** A program that stores structured data and answers questions about it.

**Beginner:** Tables of rows and columns, queried with SQL. We'll use **PostgreSQL**.

**Related:** SQL, JOIN

## SQL

**One line:** The language for asking databases questions.

**Beginner:** `SELECT name FROM customers WHERE country = 'Canada';` returns the names of Canadian customers. A **JOIN** combines two tables on a shared key (customer id in both `customers` and `orders`).

**Related:** database

## Test

**One line:** Code that checks other code does what it should.

**Beginner:** Not just "does it work today" — the real purpose is so you can *change* code later without fear. We'll use **pytest**.

**Related:** debugging

## Token

**One line:** The chunk of text an LLM reads and writes in; roughly a word or part of a word.

**Beginner:** "I am a human" ≈ 4 tokens. Costs are charged per token. Week 2 topic.

**Related:** context window, LLM

## Context window

**One line:** The maximum number of tokens a model can hold at once.

**Beginner:** The size of the table, not what's on it. System prompt + conversation + tool results + the model's reply all have to fit together. Not "the number of tokens in input and output" — that's what's *on* the table.

**Related:** token

## RAG

**One line:** Retrieval-Augmented Generation — fetch relevant information, then hand it to an LLM as context before it answers.

**Beginner:** The model was trained on general text; RAG gives it *your* documents at question time. Week 2 project.

**Related:** embedding (later), context window

## Agent

**One line:** An LLM-powered system that observes, decides, acts using tools, and checks results in a loop.

**Beginner:** Week 3. Rule we'll repeat: don't use an agent when a plain workflow is enough.

**Related:** tool, RAG
