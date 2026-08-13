## Governance for AI agents. Automation you control and own.

An AI agent that runs shell commands, edits files and calls APIs needs someone
to have said, in advance and in writing, what it may touch. In contenox that is
a file in your repository: **what may run**, **what needs a human**, and **what
starts work**. The task engine enforces it, and anything no rule covers fails
closed — it asks.

It runs on your machine, against your files, with your keys, on the model you
picked.

### Why that holds

Apache-2.0. No account, and nothing phones home
without you turning it on.

The hosted relay at [app.contenox.com](https://app.contenox.com) is optional and
separate: it lets you reach a session running on your own machine from a
browser. It stores no session content, and nothing needs it.

### Start

```bash
curl -fsSL https://contenox.com/install.sh | sh
contenox setup
```

### Where things are

- **[contenox](https://github.com/contenox/contenox)** — the runtime, the task
  engine, the CLI and the terminal UI.
- **[Documentation](https://contenox.com/docs/)** — start with
  [what contenox is](https://contenox.com/docs/guide/what-contenox-is/), then
  [the quickstart](https://contenox.com/docs/guide/quickstart/).
- **[Legal](https://contenox.com/legal)** — terms, privacy, imprint, security
  and sub-processors for the hosted service.

Questions: [hello@contenox.com](mailto:hello@contenox.com)
