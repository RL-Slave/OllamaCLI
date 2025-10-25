# RL Ollama Coder – Binary Quickstart

End users receive the compiled build (`run_cli`) and do **not** need Python, pip, or a virtual environment. Follow the steps below to launch the Textual UI and start coding with your Ollama server.

---

## 1. Get the Files

((Windows Comming soon))
1. Download the Linux release archive (e.g., `rl_ollama_coder_linux.zip`).
2. Extract the archive to any folder (no install step is required).

The extracted folder contains the `run_cli` binary plus supporting assets/config.

---

## 2. Run the TUI

Run from a terminal for best logging/UX:

```bash
chmod +x run_cli   # first launch only
./run_cli
```

Everything is packaged—no Python or venv required.

---

## 3. First Launch

1. The TUI opens with a status panel (session/model/workspace/connection) and a chat log.
2. Type anything to send your first prompt to Ollama. If the UI reports “Disconnected,” open the `settings` command to enter the correct Ollama URL/model.

Configuration files (config + SQLite history) are stored in `~/.config/rl_ollama_coder/`, so future builds pick up your saved values automatically.

---

## 4. Built-In Commands

| Command | Description |
| --- | --- |
| `settings` | Change Ollama URL/model from inside the TUI. |
| `/history` | Browse & load previous chat sessions. |
| `/set-workspace <path>` | Set a working directory used for file listings and context. |
| `/open-workspace` | Jump back to the saved workspace path. |
| `exit` / `quit` | Close the TUI. |

Everything else works through natural language prompts—just tell the assistant what to build or inspect.

---

## 5. Tool Approvals & Background Tasks

- When the AI wants to run a shell command, edit files, or start background services, a prompt appears inside the chat log:  
  `Allow? (y = yes, n = no, a = yes to all)`  
  Type your response and hit Enter; input remains active during long operations.
- Long-running processes (servers, scripts, etc.) can be started/stopped via the assistant. Their output is written to `process_logs/<id>.log` inside the config directory so you can inspect or tail them later.

---

## 6. Logs

| File | Purpose |
| --- | --- |
| `~/.config/rl_ollama_coder/ai_cli.log` | General activity (connection status, errors, approvals). |
| `~/.config/rl_ollama_coder/process_logs/*.log` | Output from background processes the AI starts. |

Send these logs when reporting issues—they capture everything happening even if the UI seems paused.

---

## 7. Troubleshooting

- **“Disconnected”** – Ensure your Ollama server is reachable from the current machine and update the URL via `settings`.
- **Tool prompts stuck** – The input box never locks; if a prompt lingers, type `y`, `n`, or `a`. Use `Ctrl+C` only if you want to quit immediately.
- **Permission errors** – Make sure `run_cli` is executable (`chmod +x run_cli`). If your Ollama instance uses a self-signed cert, configure it in `config.yaml`.

Enjoy building with the RL Ollama Coder TUI—no Python install, no setup pains, just run the bundled Linux binary and start collaborating with your local model.
