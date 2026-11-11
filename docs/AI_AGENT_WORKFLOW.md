# Multi-Agent Workflow & Governance Protocols

## 1. Antigravity Agent Lifecycle & Gate Control

```mermaid
sequenceDiagram
    autonumber
    actor Owner as Human Project Owner
    participant PM as Project Manager Agent
    participant Arch as Software Architect Agent
    participant Dev as Mobile/Backend Agent
    participant QA as QA Agent

    Owner->>PM: Define Feature Task / Requirement
    PM->>Arch: Request Analysis & Architectural Plan
    Arch->>Arch: Inspect Codebase & Draft Plan
    Arch->>PM: Deliver Proposal & Risk Analysis
    PM->>Owner: Present Plan for Explicit Review (WAIT GATE)
    Note over Owner,PM: Execution stops completely. No files modified.
    Owner->>PM: "Approved. Proceed with implementation."
    PM->>Dev: Dispatch implementation subtask
    Dev->>Dev: Write Code & Surgical Edits
    Dev->>QA: Hand off to automated test harness
    QA->>QA: Run Jest, Typescript & E2E checks
    QA->>PM: Report test results & coverage
    PM->>Owner: Deliver Final Report & Diff for Acceptance
```

---

## 2. Hard Stop Protocol & Guardrails

1. **The "Wait Gate" is Inviolate**: An agent must conclude its turn immediately after presenting an implementation plan requiring human approval. It must never append implementation code to the planning turn.
2. **Context Window Protection**: Agents should not read massive log files or bundle dumps. They use surgical line reads (`read_file` with ranges).
3. **No Phantom Tools**: Agents must strictly use the native tools declared in the Antigravity environment (`read_file`, `write_file`, `edit_file`, `run_command`, `schedule`, `search_marketplace`, `swarm`).
