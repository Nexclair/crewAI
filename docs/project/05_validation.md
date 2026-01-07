# CrewAI Validation Strategy

> [!NOTE]
> For the documentation workflow and standards, see [README.md](../../README.md) and [01_constitution.md](01_constitution.md).

This document defines how requirements are validated to ensure compliance with the **04_requirements_registry.md** and the **01_constitution.md**.

## Validation Levels

| Level | Method | Tool | Target |
| :--- | :--- | :--- | :--- |
| **Unit** | Automated | Pytest (+ plugins like `asyncio`) | Core logic, Agent class, Task class. |
| **Integration**| Automated | Pytest (+ `recording`, `vcrpy`) | Crew/Flow orchestration, YAML parsing. |
| **E2E** | Automated | Pytest (+ `subprocess`) | Complete agent workflows, CLI commands. |
| **Linting** | Automated | Ruff | Code style, formatting, and quick fixes. |
| **Type Check** | Automated | Mypy | Static type safety and interface validation. |
| **Security** | Automated | Bandit | Automated security vulnerability scanning. |
| **Manual** | Human | Shell | UI/UX fidelity in AMP Suite. |
| **AI-Audit** | Agent | Antigravity | Principle compliance (Agent-First, 5-Minute Rule). |

---

## Requirement Validation Mapping

### Core Framework (FR-CORE)
- **Validation**: Unit / E2E
- **Method**: Run `uv run pytest` across different Python environments (3.10-3.13).
- **Success**: All tests pass; no dependency conflicts.

### Crew Orchestration (FR-CREW)
- **Validation**: Integration / E2E
- **Method**: Mock LLM responses to verify sequential/hierarchical task flow.
- **Success**: Output matches expected sequential order or manager delegation logic.

### Flow Orchestration (FR-FLOW)
- **Validation**: Integration
- **Method**: Verify event triggers and routing logic in `test_flows.py`.
- **Success**: Correct methods called based on events and router returns.

---

## The "Constitutional Audit" (AI-Audit)
Before any feature is marked `[x] Done` in the registry, it must pass a Constitutional Audit:
1. **No Ghost Code**: Does every new function correlate to a Req ID in 04?
2. **Agent-First**: Can an LLM summarize this module's intent in <30 seconds?
3. **Standalone Check**: Verify no accidental leaks of LangChain dependencies in core logic.

---

## Definition of Done (Validation)
A requirement is considered **Validated** when:
1. All associated Automated tests pass (`pytest`).
2. AI-Audit has confirmed compliance with the **01_Constitution**.
3. Manual verification has been signed off for UI-related features (AMP Suite).
