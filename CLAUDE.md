# context-mode

Raw tool output floods your context window. Use context-mode MCP tools to keep raw data in the sandbox.

## Think in Code — MANDATORY

When you need to analyze, count, filter, compare, search, parse, transform, or process data: **write code** that does the work via `execute(language, code)` and `console.log()` only the answer. Do NOT read raw data into context to process mentally. Your role is to PROGRAM the analysis, not to COMPUTE it. Write robust, pure JavaScript — no npm dependencies, only Node.js built-ins (`fs`, `path`, `child_process`). Always use `try/catch`, handle `null`/`undefined`, and ensure compatibility with both Node.js and Bun. One script replaces ten tool calls and saves 100x context.

## Tool Selection

1. **GATHER**: `batch_execute(commands, queries)` — Primary tool for research. Runs all commands, auto-indexes, and searches. ONE call replaces many individual steps.
2. **FOLLOW-UP**: `search(queries: ["q1", "q2", ...])` — Use for all follow-up questions. ONE call, many queries.
3. **PROCESSING**: `execute(language, code)` or `execute_file(path, language, code)` — Use for API calls, log analysis, and data processing.
4. **WEB**: `fetch_and_index(url)` then `search(queries)` — Fetch, index, then query. Never dump raw HTML.

## Rules

- DO NOT use Bash for commands producing >20 lines of output — use `execute` or `batch_execute`.
- DO NOT use Read for analysis — use `execute_file`. Read IS correct for files you intend to Edit.
- DO NOT use WebFetch — use `fetch_and_index` instead.
- DO NOT use curl/wget in Bash — use `execute` or `fetch_and_index`.
- Bash is ONLY for git, mkdir, rm, mv, navigation, and short commands.

## Output

- Keep responses under 500 words.
- Write artifacts (code, configs) to FILES — never return them as inline text.
- Return only: file path + 1-line description.

## ASE-Workflow (verbindlich bei jeder Aufgabe)

- **Session-Start:** Vor Planung oder Arbeit `~/.claude/workflows/ase-workflow.md`, `ase-skills.md` und `ase-rezepte.md`
  lesen (Lead zusätzlich `ase-orchestrierung.md`) — bei jeder Aufgabe, auch Recherche und sonstiger Wissensarbeit, und in
  jedem delegierten Worker.

Der ASE-Workflow ist Pflicht. Orchestrierung und Task-Übergabe: `~/.claude/workflows/ase-orchestrierung.md`.

**Verbindliche Referenzen (lesen, nicht raten):** `~/.claude/workflows/ase-workflow.md` — Ablauf, Modi, Bedienregeln ·
`~/.claude/workflows/ase-tools.md` — CLI und Setup · `~/.claude/workflows/ase-skills.md` — Skills je Phase ·
`~/.claude/workflows/review-verfahren.md` — Review und Freigabe (Abschnitte „Review-Auftrag, Diff-Quelle und Rollen“
und „Gemeinsames Freigabe-Gate für A und B“). Die Referenzen sind **bindend** und werden vor
Prozess-/Werkzeugentscheidungen gelesen. Wo der ASE-Workflow gilt, ist die volle ase-Skill-Nutzung je Phase verbindlich.
