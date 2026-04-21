# Copilot adapter

## Install
```bash
mkdir -p .github
cp adapters/copilot/.github/copilot-instructions.md .github/copilot-instructions.md
```

Or:
```bash
./install.sh copilot
```

## What it wires up
- **`.github/copilot-instructions.md`** — repository-level custom instructions
  that GitHub Copilot CLI and the Copilot VS Code extension inject into every
  session. Points the model at the portable brain in `.agent/`.

  GitHub Copilot reads this file automatically when it is present at
  `.github/copilot-instructions.md` in the project root. No extra
  configuration is required.

## Verify
Open a Copilot chat (VS Code or `gh copilot`) and ask
"What files should you read before acting?" — it should mention
`.agent/AGENTS.md`.

## Notes
GitHub Copilot does not expose a first-class hook system, so post-execution
memory logging is the agent's responsibility. The instructions file directs
Copilot to call `memory_reflect.py` after significant actions. If you want
automated logging, run the standalone-python conductor in parallel as a
background process.
