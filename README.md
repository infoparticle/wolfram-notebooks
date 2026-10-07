# Quant Math Course (Wolfram Language / WLJS)

- `claude-wolfram.wln` — the course notebook
- `PROGRESS.md` — which modules are done and what comes next
- `CLAUDE.md` — how Claude should teach and format output in this course

## Setting up another machine

1. Install [WLJS Notebook](https://wljs.io) and the free Wolfram Engine (activate with a Wolfram ID).
2. Clone this repo. Keeping it at `~/Documents/WLJS Notebooks/MyNotebooks` makes it show up in the
   WLJS file browser.
3. Install Claude Code and register the notebook's MCP server (the WLJS app must be running):

   ```
   claude mcp add --transport http --scope user wljs-notebook http://127.0.0.1:20564/
   ```

   The port is the one used on the desktop; check the WLJS settings if it differs.
4. Start `claude` **from this folder** so it picks up `CLAUDE.md` and `PROGRESS.md`.

## Moving between machines

Save in WLJS (the file is rewritten whole), then:

```
git pull                      # before starting
git add -A && git commit -m "..." && git push    # when done
```

Don't leave the notebook open and edited on two machines at once — the `.wln` file does not merge.
