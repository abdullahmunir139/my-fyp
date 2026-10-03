---
source: Q9.txt
date: 2026-10-03
model: opencode/big-pickle
agent: opencode
instance: 1
---
# Installing Graphify on Windows OS — Guide

This guide installs **Graphify** — the tool that turns a folder into a queryable
knowledge graph (`graphify-out/graph.json`) — on Windows 10/11. It also shows how
to wire it into this context-engine repo.

> The PyPI package is spelled **`graphifyy`** (double "y"). The command it
> installs is **`graphify`** (single "y"). Do not confuse the two.

## What you get

| Output | Purpose |
|--------|---------|
| `graphify-out/graph.json` | Full graph data (nodes + edges) |
| `graphify-out/graph.html` | Interactive browser view |
| `graphify-out/GRAPH_REPORT.md` | Plain-language audit report |

---

## 1. Prerequisites

Install these first (each opens an installer — click through defaults):

| Tool | Why | Get it |
|------|-----|--------|
| Python 3.10+ | Runtime for graphify | <https://www.python.org/downloads/windows/> |
| uv (recommended) | Clean isolated tool installs | <https://docs.astral.sh/uv/getting-started/installation/> |
| Git (optional) | Cloning / commit-hook setup | <https://git-scm.com/download/win> |

**Critical Python step:** In the Python installer, tick **"Add python.exe to
PATH"** on the first screen before clicking Install. If you miss it, re-run the
installer and choose *Modify → Add to PATH*.

Verify in a **new** PowerShell window:

```powershell
python --version
pip --version
```

---

## 2. Install Graphify

### Option A — uv (recommended)

`uv` installs graphify into its own isolated environment and puts the `graphify`
command on your PATH — no virtualenv juggling.

```powershell
# Install uv if you don't have it
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

# Install Graphify
uv tool install graphifyy
```

### Option B — pip

```powershell
python -m pip install --upgrade pip
python -m pip install graphifyy
```

If you want the optional Gemini semantic backend for docs/papers/images:

```powershell
python -m pip install "graphifyy[gemini]"
```

> Plain `pip install graphify` (single "y") installs an unrelated package or
> fails — always use **`graphifyy`**.

---

## 3. Verify the install

Close and reopen PowerShell (so PATH refreshes), then:

```powershell
graphify --version
```

If that errors, try the module form:

```powershell
python -m graphify --version
```

### Fixing "graphify is not recognized"

1. Find the Scripts folder:
   - uv: `%USERPROFILE%\.local\bin`
   - pip: `%APPDATA%\Python\Python3xx\Scripts`
2. Add it to PATH:
   - Press `Win`, type **"environment variables"**, open *Edit the system
     environment variables*.
   - **Environment Variables → User variables → Path → Edit → New**, paste the
     folder, save.
3. Open a new PowerShell window and retry.

---

## 4. Build the graph for this repo

Run these **from the repository root only** (never inside a submodule):

```powershell
cd C:\path\to\my-fyp-abdullah
graphify update .
```

`graphify update .` is **AST-only** — no API key, no token cost. It indexes code
plus your Q/A/T/E context files into `graphify-out/graph.json`.

Then query it before browsing files (this repo's forced first step):

```powershell
graphify query "graphify install windows"
graphify path "SYSTEM.md" "INDEX.md"
graphify explain "Guides Module"
```

---

## 5. Windows-specific notes

- **PowerShell execution policy:** if the `uv` one-liner is blocked, run
  PowerShell as Administrator once and set
  `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`.
- **Long paths:** deep node_modules-style paths can exceed the 260-char limit.
  Enable long paths as Administrator:
  ```powershell
  reg add "HKLM\SYSTEM\CurrentControlSet\Control\FileSystem" /v LongPathsEnabled /t REG_DWORD /d 1 /f
  ```
  Then enable it for Git too: `git config --system core.longpaths true`.
- **Windows Terminal is easiest** — use the *PowerShell* profile, not the legacy
  console, for correct UTF-8 output of the graph report.
- **No API key needed.** Graphify reads `GEMINI_API_KEY`/`GOOGLE_API_KEY` *only*
  if already set. It never reads `OPENAI_API_KEY` or `ANTHROPIC_API_KEY`.

---

## 6. Command reference

```powershell
graphify update .                 # rebuild/extend graph (AST, free)
graphify query "<question>"       # BFS traversal — broad answer
graphify query "<q>" --dfs        # trace a single path
graphify path "<A>" "<B>"         # shortest path between two nodes
graphify explain "<concept>"      # plain-language node explanation
graphify export html              # rebuild graph.html
```

---

## 7. Troubleshooting

| Symptom | Fix |
|---------|-----|
| `graphify` not recognized | Reopen terminal; add Scripts dir to PATH (§3) |
| `python` not recognized | Reinstall Python with *Add to PATH* checked |
| `graphify-out/` missing | Run `graphify update .` from repo root |
| `graph.json` empty | Run `graphify update .` again; check files are inside the scanned dir |
| Queries return nothing | Run `graphify update .`, then requery |
| `uv` install blocked | Set execution policy (§5) or use pip (Option B) |

## Rules of use in this repo

- `graphify-out/` is **READ-ONLY** for agents — never hand-edit graph files.
- Run `graphify update .` **only from the repo root**.
- After any file change, run `graphify update .` so the graph stays current.
