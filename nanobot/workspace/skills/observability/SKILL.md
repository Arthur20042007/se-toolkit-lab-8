---
name: observability
description: Use observability tools (logs and traces) to investigate system issues
always: true
---

# Observability Skill

You can see the system's "eyes" — logs and traces. Use these tools when a user reports an error, asks about system health, or when a tool call fails.

## Strategy

When investigating failures (e.g., when the user asks "What went wrong?" or "Check system health"):

1. **Service-level Health**: Start with `mcp_obs_logs_error_count` on a short recent window (e.g., 5 or 10 minutes) for likely services such as "Learning Management Service".
2. **Detailed Logs**: Use `mcp_obs_logs_search` with a query like `_time:10m severity:ERROR` to find specific log records.
3. **Trace Correlation**: If an error log contains a `trace_id`, fetch the full trace using `mcp_obs_traces_get`. This shows exactly where the request failed in the stack.
4. **Summarization**: Provide a single coherent explanation that:
   - Cites **log evidence** (e.g., "Logs show a `db_query` failure in the backend...")
   - Cites **trace evidence** (e.g., "...and the matching trace `e242...` confirms the span for PostgreSQL timed out.")
   - Identifies the **affected service** and **root cause**.
   - **Do not dump raw JSON.** Be concise and technical.

## Specific Tasks

### What went wrong? / Check system health
Follow the multi-step investigation flow above:
- `mcp_obs_logs_error_count`
- `mcp_obs_logs_search`
- `mcp_obs_traces_get` (if a trace ID is found)
- Summarize with citations.

### Any errors in the last X minutes?
- Use `mcp_obs_logs_search` with `_time:Xm severity:ERROR`.
- If errors are found, optionally fetch a trace for the most recent one to add more context.

### Proactive Health Checks (Cron)
If the user asks to schedule a health check:
- Use the `cron` tool to schedule a recurring job.
- Each run should perform the investigation flow above and post a summary.
- If no errors are found, report that the system looks healthy.
