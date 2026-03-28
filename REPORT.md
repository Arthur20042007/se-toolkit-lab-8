# Lab 8 — Report

Paste your checkpoint evidence below. Add screenshots as image files in the repo and reference them with `![description](path)`.

## Task 1A — Bare agent

<!-- Paste the agent's response to "What is the agentic loop?" and "What labs are available in our LMS?" -->

## Task 1B — Agent with LMS tools

<!-- Paste the agent's response to "What labs are available?" and "Describe the architecture of the LMS system" -->

## Task 1C — Skill prompt

<!-- Paste the agent's response to "Show me the scores" (without specifying a lab) -->

## Task 2A — Deployed agent

```text
nanobot-1  | 🐈 Starting nanobot gateway version 0.1.4.post5 on port 18790...
nanobot-1  | 2026-03-28 15:49:57.663 | INFO     | nanobot.channels.manager:_init_channels:58 - WebChat channel enabled
nanobot-1  | ✓ Channels enabled: webchat
nanobot-1  | ✓ Heartbeat: every 1800s
nanobot-1  | 2026-03-28 15:49:57.668 | INFO     | nanobot.cron.service:start:202 - Cron service started with 0 jobs
nanobot-1  | 2026-03-28 15:50:00.406 | INFO     | nanobot.agent.loop:run:280 - Agent loop started
```

## Task 2B — Web client

WebSocket connection test through Caddy:
```text
Response: {"type":"text","content":"Here are the available labs:\n\n| Lab ID | Title |\n|--------|-------|\n| lab-01 | Lab 01 – Products, Architecture & Roles |\n| lab-02 | Lab 02 — Run, Fix, and Deploy a Backend Service |\n| lab-03 | Lab 03 — Backend API: Explore, Debug, Implement, Deploy |\n| lab-04 | Lab 04 — Testing, Front-end, and AI Agents |\n| lab-05 | Lab 05 — Data Pipeline and Analytics Dashboard |\n| lab-06 | Lab 06 — Build Your Own Agent |\n| lab-07 | Lab 07 — Build a Client with an AI Coding Agent |\n| lab-08 | lab-08 |\n\nYou can ask me about any specific lab's performance metrics, completion rates, pass rates, top learners, submission timeline, or group performance. Just let me know which lab you're interested in!","format":"markdown"}
```

Verified end-to-end path through Caddy reverse-proxy:
- Flutter UI accessible at `/flutter`
- WebSocket connection available at `/ws/chat` with `access_key` authentication.
- Agent uses `mcp_lms` to fetch real data and `mcp_webchat` to deliver structured messages.

## Task 3A — Structured logging

<!-- Paste happy-path and error-path log excerpts, VictoriaLogs query screenshot -->

## Task 3B — Traces

<!-- Screenshots: healthy trace span hierarchy, error trace -->

## Task 3C — Observability MCP tools

<!-- Paste agent responses to "any errors in the last hour?" under normal and failure conditions -->

## Task 4A — Multi-step investigation

<!-- Paste the agent's response to "What went wrong?" showing chained log + trace investigation -->

## Task 4B — Proactive health check

<!-- Screenshot or transcript of the proactive health report that appears in the Flutter chat -->

## Task 4C — Bug fix and recovery

<!-- 1. Root cause identified
     2. Code fix (diff or description)
     3. Post-fix response to "What went wrong?" showing the real underlying failure
     4. Healthy follow-up report or transcript after recovery -->
