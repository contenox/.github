## An agent server

**Every AI product runs one. Nobody ships you one.**

contenox is that layer as a server you run yourself — on your machine, on any
model. Every action is checked against your policy before it happens.

### You don't build an agent. You declare one.

```
.contenox/
  agents/
    reviewer.md               # one agent, one file
    triage.md                 # another
  agents.toml                 # the knobs a declaration cannot reach

.claude/agents/               # already have agents? read where they are
```

Markdown with a YAML frontmatter header — the same file Claude Code reads. Drop
it in and the next run picks it up: no build step, no plugin API, nothing to
convert.

### How much agency? You decide — in writing.

```json
{
  "default_action": "approve",
  "compute": { "maxToolCalls": 300, "maxTokens": 2000000, "onExhausted": "finish_stuck" },
  "rules": [
    { "tools": "local_fs", "tool": "*", "action": "deny",
      "when": [{ "key": "path", "op": "glob",
                 "value": "**/{.ssh,.aws,.kube,.config/gcloud}/**" }] },
    { "tools": "local_fs", "tool": "read_file", "action": "allow" },
    { "tools": "local_fs", "tool": "write_file", "action": "approve" },
    { "tools": "local_shell", "tool": "local_shell", "action": "allow",
      "when": [{ "key": "command", "op": "command_prefix_allowlist",
                 "value": "go test,go vet,ls,cat,grep,npm test,pytest" }] }
  ]
}
```

Secrets are unreachable. Reads pass silently, those seven commands run without
asking, writes stop for a human. Anything no rule matches fails closed, because
nothing said otherwise — plus hard ceilings on tool calls and tokens.

That file is in your repo. Editing it changes what the agent may do — no
rebuild, no redeploy. `contenox vet` checks it before anything runs under it.

### It survives you closing the laptop

```bash
contenox mission fire reviewer "review the payment-retry PR for regressions" --wait
# ⏸ two regressions found, patch drafted — apply it to the branch?
#   no answer: run checkpointed, ask saved, process released

# days pass. then, from any terminal that reaches your models:
contenox approvals respond 8f3c --answer "yes, apply it"
# checkpoint resumed — exactly once. mission landed.
```

No babysitting a terminal, no timed-out approvals, no silent changes.

---

Runs on your machine. Any provider — Ollama, vLLM, OpenAI, Anthropic, Bedrock,
Vertex, Gemini. Speaks ACP, so Zed, JetBrains, AionUi, OpenClaw and the terminal
UI drive the same agent. Apache-2.0, one binary, no account, and nothing phones
home unless you turn it on.

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
