# PickMyBrain for Cursor

Ask every expert in your PickMyBrain catalog at once, or one expert by name.
The plugin talks to `https://pickmybrain.com/api/mcp` and signs you in with
OAuth. There is no client secret.

Install it from the Cursor Marketplace once it is listed. Until then, Cursor
can load this repository as a local plugin:

```bash
mkdir -p ~/.cursor/plugins/local/pickmybrain
git clone https://github.com/wois-org/pickmybrain-cursor.git ~/.cursor/plugins/local/pickmybrain
```

Reload the window, enable **pickmybrain** under Customize, and sign in when
Cursor asks. Allow the connection on pickmybrain.com, then ask the agent to
question your experts.

| Tool | Purpose |
|------|---------|
| `ask_experts` | One question to every expert you can see |
| `ask_expert` | One expert, by name |
