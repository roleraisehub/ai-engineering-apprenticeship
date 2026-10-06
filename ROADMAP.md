# ROADMAP — 30 days

Built from the Day 0 diagnostic. This is a plan, not a contract: days stretch when a fundamental isn't landing and compress when it is. What does not move is the order and the four project gates.

## Who this is built for

- Recognizes most concepts (databases, JOINs, APIs, RAG, tokens); has executed almost none of them. The gap is hands, not vocabulary.
- Absorbs new concepts slowly. So: **fewer concepts per day, each used three ways** (explain → use → break). Never more than two genuinely new ideas before lunch.
- Debugs by asking Claude. So: every error gets the ten debugging questions before any fix is offered.
- Claude Pro, no API key yet, $10 API budget. So: Weeks 1 and most of Week 2 cost $0 in API. Every API-touching exercise is designed to run on mocks first and real calls last.
- Python 3.14 is installed. If a library lags, drop to 3.12 for that project only.

## The shape

```
Week 1   Software + data foundations      → Project 1: Task Management API
Week 2   Data engineering + LLM + RAG      → Project 2: RAG system
Week 3   Agents + MCP + Claude Code        → Project 3: AI data analyst agent
Week 4   Production + LLMOps + security    → Final: a real product, deployed
Day 30   Assessment
```

Every day: ~1h concept, ~3h hands-on, ~1h project, ~1h test/debug/productionize, ~1h interview prep, ~1h review + docs. Hard Interview Mode on days marked ⚔.

## Gates (these do not move)

| Gate | Day | You pass only if you can |
|---|---|---|
| G1 | 7 | Build, test, and run a FastAPI + PostgreSQL service in Docker, and explain every file in it without notes |
| G2 | 14 | Ingest documents, retrieve with citations, and show an eval score, with token/cost tracking, and explain where the tokens go |
| G3 | 21 | Write the agent loop from scratch (no framework), add a tool, make it fail safely, and argue when NOT to use an agent |
| G4 | 29 | Deploy the final product with CI, logs, and an eval, and explain its architecture, security model, and cost in a 45-min design interview |

Failing a gate means the next week starts with the gap, not the next topic.

---

## WEEK 1 — Software and data foundations

**Goal:** stop recognizing, start executing. By Day 7 you have written a real backend service with tests.

### Day 1 — Python I: run code, variables, strings, functions
- Virtual environments (the full baby-step treatment); run a `.py` file; the REPL
- Variables, numbers, strings, f-strings, type(), basic errors
- Functions: `def`, parameters, `return`, calling; the Q5 function, for real
- Exercise: 5 small functions with `assert` checks; deliberately break one, read the traceback
- Docs: `00-foundations/python/day01.md`, glossary additions, first flashcards
- Interview: "What's the difference between a parameter and an argument?" and 4 more

### Day 2 — Python II: collections, control flow, scope ⚔
- Lists, dicts, tuples, sets; indexing, slicing, `in`
- `if`/`elif`/`else`, `for`, `while`, `range`, `enumerate`
- Scope: why "temporary" was wrong on the diagnostic
- Exercise: a contact book in memory — add, find, delete, list; then a word-frequency counter over a string
- Failure drill: `KeyError`, `IndexError`, off-by-one; diagnose before fixing

### Day 3 — Python III: files, exceptions, modules, classes, tests
- Reading/writing files, `with`, paths; `try`/`except`; `import`, your own modules
- Classes: just enough — `class`, `__init__`, methods, when a dict is better
- Type hints; `pytest` from zero: first real test file, run it, make it fail, make it pass
- Exercise: move the contact book to a CSV file with a `Contact` class and 6 tests

### Day 4 — Terminal, Git for real, HTTP, JSON, first API call
- Terminal: pipes, `grep`, `find`, permissions, processes, env vars, `.env` files
- Git: branches, merging, pull requests on GitHub, resolving a conflict on purpose
- HTTP: request/response, methods, status codes, headers; JSON ↔ dict
- Call a public API from Python (`httpx`); handle a 404 and a timeout
- Claude Code: install (verify against current docs), explore your repo, ask it questions. **Read-only use until Day 7.**

### Day 5 — SQL and PostgreSQL ⚔
- Install PostgreSQL; create a database; tables, types, primary/foreign keys, constraints
- SELECT/WHERE/ORDER/GROUP BY/HAVING; JOINs; subqueries; CTEs; window functions (intro)
- Indexes: EXPLAIN before and after; transactions; a migration by hand
- Exercise: model tasks + users + projects; 15 queries, increasing difficulty

### Day 6 — FastAPI
- "What problem would exist without this framework?" first
- First endpoint; path/query/body params; Pydantic models for validation; auto docs
- Connect to PostgreSQL; CRUD for tasks; error responses; logging
- Tests with `TestClient`
- Spec-driven development begins: write `SPEC.md` for Project 1 before the next line of code

### Day 7 — Project 1: Task Management API → Gate G1
- Finish: auth (token-based), CRUD, validation, tests, logging, Docker, README/API.md/TESTING.md
- Code review as a staff engineer would
- 15-minute mock interview; Week 1 review; skill matrix update with evidence
- Pick the primary Day-31 outcome. This decides the final project.

---

## WEEK 2 — Data engineering + LLM foundations + RAG

**Goal:** move data with confidence, understand what an LLM actually does, build RAG with evaluation. **API spend target: ≤ $3.**

### Day 8 — Data engineering I: pandas, DuckDB, ETL
- ETL vs ELT; batch vs streaming (concepts); pipelines as functions
- pandas: load, clean, transform, write; DuckDB: SQL over files
- Exercise: a messy CSV → clean Parquet → summary table, with data-quality checks

### Day 9 — Data engineering II: modeling, quality, orchestration ⚔
- Data modeling: normalization, star schema, when to denormalize; schema evolution; data contracts; lineage
- Orchestration concepts (DAGs, idempotency, retries) without a heavy framework
- Polars and Spark: what they are, when they matter, 30 minutes each, no deep dive
- Exercise: design the data model for Project 2's document store

### Day 10 — LLM fundamentals (Claude Pro only, $0)
- What an LLM is; transformers and attention at the intuition level; tokens, tokenization (count them by hand, then with a tokenizer); context windows; inference; temperature
- Prompting: system/user/assistant roles; structure; the cost of vague prompts
- Exercise: estimate token counts and costs for 5 scenarios, verify with a tokenizer

### Day 11 — Claude API: first key, secrets, first calls
- Create the API key; `.env`, never in code, never in Git; rotate if ever exposed
- Messages API: request, response, usage field; errors, retries, rate limits, timeouts
- **Mock first**: write the client against a fake, then flip to real
- Token tracker: every call logs input/output tokens and estimated cost to a file
- Budget check against the provider's billing page

### Day 12 — Structured output and tool calling ⚔
- JSON-mode outputs validated with Pydantic; handling malformed output
- Tool use: define a tool, let the model call it, execute, return result
- Exercise: an extraction pipeline (text → structured records) with tests on mocked responses

### Day 13 — Embeddings and retrieval
- Vectors, similarity, semantic search; run a local embedding model ($0)
- Chunking strategies; metadata; a vector index (pgvector or a simple in-memory index first)
- Exercise: embed 50 chunks, retrieve for 10 questions, inspect what retrieval gets wrong

### Day 14 — Project 2: RAG system → Gate G2
- Ingestion → chunking → embeddings → retrieval → reranking (simple) → generation with citations
- Evaluation: a 20-question set with expected sources; retrieval hit rate; answer quality
- Token and cost tracking on every request; API; tests; logging; docs
- 30-minute mock interview; Week 2 review

---

## WEEK 3 — Agentic AI + MCP + Claude Code

**Goal:** build the agent loop yourself, know when not to use one, become dangerous with Claude Code. **API spend target: ≤ $3.**

### Day 15 — The agent loop from scratch
- Observe → reason → act → verify; state; stopping conditions
- Build it in ~100 lines with no framework, against a mocked model first
- Failure drills: infinite loop, malformed tool call, tool error

### Day 16 — Tools, state, memory ⚔
- Tools for: calculator, filesystem (sandboxed), database (read-only), an HTTP API
- Tool permissions and least privilege; tool results that are too large
- Memory: what to keep, what to summarize, what to drop; cost of history

### Day 17 — Agent architectures and when not to use them
- Workflow → tool-calling workflow → single agent → multi-tool → planner/executor → human-in-the-loop → multi-agent → event-driven
- For each: cost, failure modes, evaluation. The seven questions before any agent
- Exercise: three problems — decide agent vs workflow for each and defend it

### Day 18 — MCP
- What problem MCP solves; architecture; servers, clients, tools, resources
- Build a tiny MCP server exposing one tool; connect it to Claude Code
- Security: what an MCP server can reach, and why that matters

### Day 19 — Claude Code, intermediate → advanced ⚔
- CLAUDE.md; planning before coding; context management; permissions; code review of its output
- Guardrails: prevent destructive changes, invented APIs, skipped tests, unrelated edits
- Exercise: implement a Project 1 feature with Claude Code, then explain every change it made

### Day 20 — Spec-driven development, Project 3 spec
- Problem → requirements → constraints → assumptions → spec → architecture → acceptance criteria → plan → tasks → tests
- Write SPEC.md, ARCHITECTURE.md, IMPLEMENTATION_PLAN.md, TASKS.md, SECURITY.md for Project 3
- Threat model: SQL from an LLM — injection, data exfiltration, destructive queries

### Day 21 — Project 3: AI data analyst agent → Gate G3
- Question → inspect schema → write SQL → execute (read-only, sandboxed) → analyze → explain → ask for clarification when ambiguous
- Evaluation set; observability (trace every step); cost per question
- 45-minute system design mock; Week 3 review

---

## WEEK 4 — Production, LLMOps, security, final product

**Goal:** ship something real and defend it. **API spend target: ≤ $3, $1 reserve.**

### Day 22 — Docker and CI/CD
- Docker beyond the basics: images, layers, compose with Postgres + Redis; environment variables and secrets
- GitHub Actions: lint, test, build on every push; a failing CI run on purpose

### Day 23 — Observability ⚔
- Structured logs; metrics; traces across API → agent → tool → model
- Health checks; what "it's slow" looks like in data; rollback

### Day 24 — LLMOps: evaluation and regression
- Eval datasets; prompt and model versioning; regression tests for prompts; agent trajectory evaluation
- Build the eval harness the final project will use

### Day 25 — AI security
- Prompt injection (direct and indirect), data leakage, tool abuse, excessive permissions, SSRF, output validation
- Red-team Project 3: find three real vulnerabilities, fix them, write SECURITY.md

### Day 26 — AI economics + final project definition ⚔
- Input/output tokens, context size, caching, model selection, agent-loop cost; compute actual costs for Projects 2 and 3
- "Who has this problem, and why would they care?" → PROBLEM.md, SPEC.md, ARCHITECTURE.md, COST.md for the final project

### Days 27–28 — Final project build
- Spec → tasks → tests → implementation, with Claude Code as pair programmer and you as reviewer
- Everything from the production checklist: reliability, security, testing, observability, cost

### Day 29 — Deploy, document, defend → Gate G4
- Deploy; CI green; monitoring on; README/API/OPERATIONS/EVALUATION docs complete
- 60-minute final mock interview: Python, SQL, data, AI, agents, system design, behavioral — using your real projects

### Day 30 — Assessment
- Fundamentals, coding, debugging, data, AI, production, security, cost, architecture, interview, startup
- Honest report: strengths, gaps, what to learn next. No "you're ready" without evidence.

---

## Recurring threads (every day, no exceptions)

- **Interview prep**: ~1h. Python/SQL daily; AI topics from Day 10; system design from Day 14. ⚔ = Hard Interview Mode day.
- **Documentation**: session notes, glossary, cheatsheets, flashcards, PROGRESS.md.
- **Active recall**: every day opens with 5 questions from previous days, answered without notes.
- **Prediction before execution**: every command, every test run.
- **Token economics**: from Day 10, every AI system gets the "where do the tokens go" question.
- **Git**: every day ends with commits pushed. Empty `git log` for a day means the day didn't happen.

## Buffer policy

Days 3, 7, 14, 21 and 28 are allowed to spill into the next day. Nothing else is. If Week 1 Python needs an extra day, it gets it — a weak Python foundation makes every later week slower than the day it would have cost.
