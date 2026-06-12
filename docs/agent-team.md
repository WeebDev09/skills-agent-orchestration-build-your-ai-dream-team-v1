# Agent team

Below is a concise summary of the custom agents that will collaborate to build Mona's Project Pulse dashboard.

- **Designer** (`Gemini 3.1 Pro (copilot)`): Responsible for UI/UX, accessibility, information architecture, interaction flow, and visual design. For Project Pulse the Designer produces a polished dashboard layout, project cards, status badges, responsive styling, and deterministic CSS hooks (for example `.dashboard` and `.project-card`). Rules: stay within files assigned by the Orchestrator, explain tradeoffs, and report design decisions. Definition: [.github/agents/designer.agent.md](.github/agents/designer.agent.md)

- **Orchestrator** (`Claude Opus 4.7 (copilot)`): Coordinates the specialist agents (Planner, Coder, Designer), turns plans into phases, assigns file scopes, and verifies integrated results. Follows delegation and sequencing rules to avoid file conflicts and surface blockers. Definition: [.github/agents/orchestrator.agent.md](.github/agents/orchestrator.agent.md)

- **Coder** (`GPT-5.5 (copilot)`): Implements code with clear structure, explicit errors, and tests. When delivering a runnable Project Pulse app the Coder may create supporting config (for example `.vscode/launch.json`) and follows the repo's patterns. Notable runnable-app guidance: set `cwd` to `${workspaceFolder}/app`, open `index.html` for preview, and keep configs deterministic. Rules: stay within assigned file scope and validate changes. Definition: [.github/agents/coder.agent.md](.github/agents/coder.agent.md)

- **Planner** (`Claude Opus 4.7 (copilot)`): Researches the codebase and produces practical, ordered implementation plans including file assignments, dependencies, parallelizable work, edge cases, validation expectations, and open questions. Definition: [.github/agents/planner.agent.md](.github/agents/planner.agent.md)

Note: the work will be orchestrated from this Codespace using the GitHub Copilot CLI; learners control all git operations (stage/commit/push) as described in each agent's `Git control` section.
