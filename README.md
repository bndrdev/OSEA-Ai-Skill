# # OSEA-AI-Skill: AI Cybersecurity Skill for Secure Code Review

> A zero-trust AI skill for vulnerability research, secure code auditing, and hardened defensive architecture.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![AI Skill](https://img.shields.io/badge/Type-AI%20Skill-blue)]()

---

## Table of Contents

- [What is OSEA?](#what-is-osea)
- [Why OSEA?](#why-osea)
- [Quick Start](#quick-start)
- [Standard Pipeline](#standard-pipeline)
- [Compatibility](#compatibility)
- [Contributing](#contributing)
- [License](#license)
- [Disclaimer](#disclaimer)

---

## What is OSEA?

OSEA is a standardized AI skill (prompt framework) that turns a general-purpose LLM into a **zero-trust security auditor**. You feed it code or system architecture, and it returns a structured security analysis — threat model, root cause, and production-ready hardened code.

It is **not** a standalone tool or scanner. It is a set of instructions you drop into your AI environment (Claude, GPT, etc.) to make it think like a red-team analyst.

---

## Why OSEA?

- **Zero naive assumptions** — treats every input as untrusted by default.
- **Structured output** — no vague "this looks risky" answers. You get a 4-block report.
- **Defensive by design** — every finding comes with a hardened replacement, not just a warning.
- **Model-agnostic** — works with any LLM that accepts a system prompt.

---

## Quick Start

1. Open [`Skill.md`](./Skill.md) and copy its full contents.
2. Paste it into your AI's **system prompt** or environment context.
3. Send your code snippet or architecture description.
4. Read the 4-block analysis.

### Example Prompt

After loading the skill, send something like this:

```javascript
app.get('/user/:id', (req, res) => {
  db.query(`SELECT * FROM users WHERE id = ${req.params.id}`, (err, rows) => {
    res.json(rows);
  });
});
```

---

## Standard Pipeline

When active, OSEA follows a fixed 4-block execution pipeline:

| Block | Focus Area | Description |
|-------|------------|-------------|
| **Block 1** | **THREAT MODEL** | Identifies potential entry points and memory/logic risks. |
| **Block 2** | **ANALYSIS** | Evaluates execution mechanisms and potential failure states. |
| **Block 3** | **ROOT-CAUSE BREAKDOWN** | Explains underlying technical flaws at the logic or runtime level. |
| **Block 4** | **HARDENED DEFENSE** | Provides production-ready defensive replacement code. |

### Expected Output Shape

Here is exactly what you get back from each block:

| Block | What you get |
|-------|--------------|
| **1. THREAT MODEL** | Entry points, trust boundaries, memory/logic risks |
| **2. ANALYSIS** | Execution path, failure states, exploitability |
| **3. ROOT-CAUSE BREAKDOWN** | The underlying flaw at logic or runtime level |
| **4. HARDENED DEFENSE** | Production-ready replacement code |

---

## Compatibility

| Environment | Status |
|-------------|--------|
| Claude (Projects / system prompt) |  Works |
| ChatGPT (Custom Instructions / GPTs) |  Works |
| Local LLMs (Ollama, LM Studio) |  Works via system prompt |
| IDE AI assistants (Cursor, Copilot Chat) |  Depends on prompt injection support |

> Modify this table based on what you have actually tested.

---

## Contributing

Contributions, feedback, and defensive security enhancements are welcome.

- Open an **Issue** for bugs or ideas
- Submit a **Pull Request** for improvements
- Star the repo if you find it useful 

---

## License

Released under the **MIT License**. See [`LICENSE`](./LICENSE) for details.

---

## Disclaimer

OSEA is intended for **defensive security** and **authorized auditing only**. Do not use it to attack systems you do not own or have explicit permission to test.
