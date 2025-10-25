# RL Ollama Coder – Binary Quickstart

End users receive the compiled build (`run_cli`) and do **not** need Python, pip, or a virtual environment. Follow the steps below to launch the Textual UI and start coding with your Ollama server.

---

## 1. Get the Files

1. Download the release archive (e.g., `rl_ollama_coder_linux.zip` or `rl_ollama_coder_windows.zip`).
2. Extract the archive to any folder (no install step is required).

The extracted folder contains:

- `run_cli` (Linux/macOS) or `run_cli.exe` (Windows)
- Supporting `ai_cli` resources, configuration defaults, and assets

---

## 2. Run the TUI

| Platform | Command |
| --- | --- |
| Linux/macOS | `./run_cli` |
| Windows (PowerShell/CMD) | `run_cli.exe` |

> **Note:** On Linux/macOS you may need to grant execute permission once: `chmod +x run_cli`.

The executable bundles Python and all dependencies; double-clicking also works, but running from a terminal keeps the log visible.

---

## 3. First Launch

1. The TUI opens with a status panel (session/model/workspace/connection) and a chat log.
2. Type anything to send your first prompt to Ollama. If the UI reports “Disconnected,” open the `settings` command to enter the correct Ollama URL/model.

Configuration files (config + SQLite history) are stored in `~/.config/rl_ollama_coder/` on Linux/macOS or `%APPDATA%\rl_ollama_coder\` on Windows, so future builds pick up your saved values automatically.

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
- **Permission errors on Linux/macOS** – Make sure `run_cli` is executable (`chmod +x run_cli`). If your Ollama instance uses a self-signed cert, configure it in `config.yaml`.

Enjoy building with the RL Ollama Coder TUI—no Python install, no setup pains, just run the bundled binary and start collaborating with your local model.

- **Prompt** at bottom shows current commands (`settings`, `/history`, `/set-workspace <path>`, `/open-workspace`, `exit`).
- **Status panel** (top left) lists current session ID, model, workspace path, and connection status (`Connected`/`Disconnected`).
- **Chat log** in middle displays system messages, your input, model responses (rendered Markdown), and tool output.

## 4. Key Commands

| Command | Description |
| --- | --- |
| `settings` | Reconfigure Ollama URL/model (input prompts appear inline). |
| `/history` | List saved sessions and load one by number. |
| `/set-workspace <path>` | Persist and switch to a new workspace directory. |
| `/open-workspace` | Jump back to the last saved workspace. |
| `exit` / `quit` | End the current TUI session. |

## 5. Tool Confirmations

When the AI requests a tool (e.g., `run_shell_command`, file writes, background processes), the TUI temporarily asks:

```
AI wants to run command: 'mkdir proj && cd proj'. Allow? (y = yes, n = no, a = yes to all)
```

Type `y`, `n`, or `a` in the input box. The UI stays interactive while tools run, and background processes log to `~/.config/.../process_logs`.

## 6. Logs

Runtime events (busy state, tool approvals, connection errors) go to `~/.config/rl_ollama_coder/ai_cli.log`. Background process logs are placed in `~/.config/rl_ollama_coder/process_logs/<id>.log`.

## 7. Troubleshooting

- **“Could not find Python interpreter”** – ensure `venv` exists before running `run_cli.py`.
- **No response received** – check that Ollama server is reachable; reconnect via `settings`.
- **Stuck tool prompt** – the input box remains unlocked; simply answer `y/n/a`. Use `Ctrl+C` to exit in emergencies.

That’s it—launch the TUI, connect to your Ollama server, and start coding with background tasks, file edits, and shell commands all orchestrated from one terminal view. Have fun!
