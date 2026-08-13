## An agent server

This is an agent, configured:

```json
{
  "default_action": "approve",
  "rules": [
    { "tools": "local_fs", "tool": "*", "action": "deny",
      "when": [{ "key": "path", "op": "glob",
                 "value": "**/{.ssh,.aws,.kube}/**" }] },

    { "tools": "local_shell", "tool": "local_shell", "action": "allow",
      "when": [{ "key": "command", "op": "command_prefix_allowlist",
                 "value": "go test,go build,git status" }] }
  ]
}
```

Secrets are unreachable. Those three commands run without asking. Everything
else stops and asks, because nothing said otherwise.

That file is in your repo. Editing it changes what the agent may do — no
rebuild, no redeploy. Triggers are declared the same way: schedules, signed
webhooks, browser forms.

Runs on your machine. Any provider — Ollama, vLLM, OpenAI,
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
