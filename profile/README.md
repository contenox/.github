## Guardrails for AI agents

Every tool call is evaluated against an envelope — a JSON policy in your repo —
before it runs: `allow`, `approve`, or `deny`. A call no rule matches takes
`default_action`, and a malformed envelope refuses to load rather than silently
disarming. Triggers are declared the same way: schedules, signed webhooks,
browser forms.

Runs on your machine against local SQLite. Any provider — Ollama, vLLM, OpenAI,
Anthropic, Bedrock, Vertex, Gemini, Mistral, OpenRouter. Speaks ACP, so Zed,
JetBrains and the terminal UI drive the same agent. Apache-2.0, one binary, no
account, and nothing phones home unless you turn it on.

```bash
curl -fsSL https://contenox.com/install.sh | sh
contenox setup
```

The hosted relay at [app.contenox.com](https://app.contenox.com) is optional and
separate: it reaches a session running on your own machine from a browser. It
stores no session content, and nothing requires it.

### Where things are

- **[contenox](https://github.com/contenox/contenox)** — runtime, task engine,
  CLI, terminal UI.
- **[Docs](https://contenox.com/docs/)** —
  [quickstart](https://contenox.com/docs/guide/quickstart/),
  [envelope format](https://contenox.com/docs/guide/hitl/),
  [JSON Schema](https://contenox.com/schema/hitl-policy-v1.schema.json).
- **[Security](https://contenox.com/legal/security)** — reporting a
  vulnerability.
- **[Legal](https://contenox.com/legal)** — terms, privacy, imprint,
  sub-processors for the hosted service.

[hello@contenox.com](mailto:hello@contenox.com)
