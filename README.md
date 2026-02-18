# Manfred 🦀

Manfred is a lean, Rust-forged AI operator that lives directly inside your development environment. The mission is simple: build an autonomous teammate that edits files, manages repos, and orchestrates background jobs *on your machine* without bouncing every action through a distant API farm.

> **Status:** The project is in active design & prototyping. The README lays out the intent, workflows, and roadmap while the first implementation is assembled.

---

## Why Another Assistant?

Most "AI assistants" are text buddies with short memories. Manfred takes the opposite approach:

- **Local-first execution** – Commands run next to your code, with direct access to git, shells, editors, schedulers, and hardware sensors.
- **Deterministic behavior** – Every action is grounded in observable commands, files, or cron jobs so you can audit and reproduce decisions.
- **Structured memory** – Daily journals + long-term notes capture decisions, preferences, and recurring tasks rather than raw chat transcripts.
- **Opinionated autonomy** – The agent is expected to take initiative. Asking for permission on every keystroke defeats the point.

---

## Guiding Principles

- **Treat the repo as home** – Configuration, memory, and operating procedures live inside the repository, versioned like code.
- **Tools over chitchat** – Shells, git, schedulers, web search, and editors are first-class tools; conversation is auxiliary.
- **Clear audit trail** – Every significant action should map to a command or file diff you can inspect later.
- **Graceful failure** – If a task cannot be completed safely, fail loudly with context and next steps.
- **Respect for the operator** – No data exfiltration, no silent external calls, no surprises.

---

## High-Level Architecture

| Layer | Purpose |
|-------|---------|
| **Core runtime (Rust)** | Owns the command loop, tool adapters, and capability routing.
| **Memory subsystem** | Maintains daily logs (`memory/YYYY-MM-DD.md`), curated `MEMORY.md`, and task-specific scratch pads.
| **Skill adapters** | Declarative wrappers for external tools (git, cron, web search, etc.) with per-tool safety policies.
| **Autonomy engine** | Plans, executes, and monitors multi-step tasks; manages retries and escalation paths.
| **Interface bridges** | Surfaces output to chat (Discord/Signal/etc.) or local dashboards without leaking sensitive context.

---

## Roadmap

| Milestone | Highlights |
|-----------|------------|
| **MVP (WIP)** | Boot CLI loop, embed memory files, execute shell/git safely, wire Discord updates. |
| **Operator Toolkit** | Add task templates (repo maintenance, dependency bumps, release prep), structured status reports, and cron-driven routines. |
| **Observability Pass** | Action logging, diff previews, audit exports, configurable verbosity. |
| **Expandable Skills** | Hot-pluggable skill packs (e.g., cloud deploy, home automation) with per-skill capability declarations. |

---

## Getting Started

> Until the initial binary lands, clone the repo and follow updates here.

1. **Install prerequisites**
   - Rust toolchain (`rustup`, latest stable)
   - `cargo fmt` / `cargo clippy` components
2. **Clone the repo**
   ```bash
   git clone https://github.com/manfred-rs/manfred-rs.git
   cd manfred-rs
   ```
3. **Build & run (soon)**
   ```bash
   cargo run --bin manfred
   ```
   The binary will read the workspace files (`SOUL.md`, `USER.md`, `memory/…`) and connect to configured messaging bridges.

When the first tagged release ships, installation scripts and pre-built artifacts for Linux/macOS will be documented here.

---

## Development Workflow

- **Formatting:** `cargo fmt`
- **Linting:** `cargo clippy --all-targets --all-features`
- **Testing:** `cargo test`
- **Memory hygiene:** keep daily `memory/YYYY-MM-DD.md` notes lightweight and regularly promote durable context into `MEMORY.md`.
- **Heartbeat routines:** encode recurring checks in `HEARTBEAT.md` before reaching for cron jobs.

---

## Contributing

Contributions are welcome once the core runtime lands. Until then you can:

- File issues describing desired skills, automation targets, or integration points.
- Draft design notes (PRs against documentation are encouraged).
- Share reproducible workflows that an autonomous repo companion should master.

---

## License

License information will be published alongside the first code drop. Until then, treat the content here as all-rights-reserved.

---

Manfred aims to be the assistant that actually touches your code, not just talks about it. Stick around as the first binaries take shape.
