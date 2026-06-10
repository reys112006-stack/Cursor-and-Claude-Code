# Cursor-and-Claude-Code
Job task
A complete guide and documentation log for setting up Anthropic's native terminal agent (`@anthropic-ai/claude-code`) inside the Cursor editor, running entirely for free by routing requests through a custom API proxy gateway to the Google Gemini API (`gemini-2.5-pro`).

---

## Tools Installed & Configured

* **Cursor Editor & Integrated Terminal**: The primary workspace environment used to execute commands and manage project files.
* **Node.js & NPM (v11.13.0+)**: The JavaScript runtime required to install and run the global CLI tool.
* **Claude Code CLI (`@anthropic-ai/claude-code`)**: Anthropic's official terminal-based autonomous coding agent.
* **Google AI Studio Key**: A free-tier developer API key used to authenticate with the Gemini engine.
* **Requesty API Proxy Gateway**: The routing bridge (`https://router.requesty.ai/v1`) used to translate Anthropic formatting into valid Google Gemini requests.

---
##  Steps Completed Successfully

### Privilege Elevation & Installation
The implementation process systematically achieved a fully functional local agent environment, breaking past standard authentication boundaries:

* **System Privilege Elevation & Package Deployment**: Initialized a PowerShell instance within Cursor, adjusted script execution scopes to mitigate system restriction blocks, and executed a global installation of the command-line interface: ``powershell
  
 Environment Interception Setup: Injected the designated proxy router routing string and the developer API key explicitly into the active Windows environment session: [Environment]::SetEnvironmentVariable("ANTHROPIC_BASE_URL", "[https://router.requesty.ai/v1](https://router.requesty.ai/v1)", "User")
  [Environment]::SetEnvironmentVariable("ANTHROPIC_API_KEY", "My Passkey", "User")

  Autonomous Code Execution: Initialized the agent engine against the target model matrix, verified stable network handshakes, and observed the agent autonomously construct a complete, multi-section web layout (index.html) containing over 600 lines of valid code directly in the workspace directory.

 
— What issues you ran into and how you solved them

Issue 1: Hanging Terminal at Web Login Screen

- Symptom: The CLI initially ignored the environment keys, froze the terminal window, and generated a massive OAuth link trying to force a browser sign-in.

- Fix: Force-closed the frozen terminal session, manually wrote {"hasCompletedOnboarding": true} to .claude.json, and explicitly fed the environment variables to the terminal line before starting.

Issue 2: Terminal Dropping Path Recognition (npm or Claude not recognized)

- Symptom: Windows suddenly forgot where Node.js lived between terminal restarts, throwing red error blocks.

- Fix: Manually appended the Node and global NPM folder paths back into the active shell instance:

Issue 3: Pre-Execution Model Validation Error

- Symptom: Upon startup, Claude Code spit out a warning saying `google/gemini-2.5-pro` might not exist or that access was restricted.

- Fix: Disregarded the notice—because the underlying environment router hooks were solid, the agent still pushed the instructions through to the key, successfully building out our files without further errors.

