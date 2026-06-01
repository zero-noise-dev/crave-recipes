# Claude Workflow — Quick Reference

## Viewing Project Content

| Command | Description |
|---|---|
| `DISPLAY` | Show the Tasks section of CLAUDE.md (pending + done) |
| `DISPLAY CLAUDE` | Show full contents of CLAUDE.md |

---

## Starting Work

| Command | Description |
|---|---|
| `ASK [description]` | Ask a question — reads CLAUDE.md only if needed |
| `BATCH` | Work through multiple small changes in one session — single COMMIT at the end |

---

## Taking Action Mid-Session

| Command | Description |
|---|---|
| `COMMIT` | Finalise a change — writes index.html to disk and commits to git |

---

## Managing Tasks

| Command | Description |
|---|---|
| `ADD TASK [description]` | Add a new pending task to the Tasks section of CLAUDE.md |
| `DONE [description]` | Mark a task as complete and move it to Done in CLAUDE.md |

---

## Maintenance

| Command | Description |
|---|---|
| `REVIEW` | Health check — flags anything stale in CLAUDE.md or TODO.md. No changes made |

---

## Typical Workflows

```
DISPLAY → ASK [question] → COMMIT
```
```
BATCH → [list of small changes] → COMMIT
```
```
ADD TASK [description]
```
```
DONE [description]
```

---

## File Locations

All files are read and written directly from disk — no uploads or downloads required.

| File | Path |
|---|---|
| `CLAUDE.md` | `C:\Projects\crave-website\CLAUDE.md` |
| `claude-quickref.md` | `C:\Projects\crave-website\claude\claude-quickref.md` |
| `index.html` | `C:\Projects\crave-website\index.html` |
