# CrewAI Requirements Registry

> [!NOTE]
> For the documentation workflow and standards, see [README.md](../../README.md) and [01_constitution.md](01_constitution.md).

**Verifiable Requirements for Test Design**
**Version 1.0** | **2026-01-07**

---

## Legend

**ID Format:** `[CATEGORY]-[FEATURE]-[NUMBER]`

**Categories:**
* **FR**: Functional Requirement
* **UI**: User Interface Requirement
* **SEC**: Security Requirement
* **INT**: Integration Requirement

**Implementation Status:**
* `[x]` **Done**: Fully implemented.
* `[/]` **In Progress**: Partially implemented.
* `[ ]` **Not Started**: Scheduled.

---

## Core Framework (FR-CORE)

| ID | Status | Category | Requirement Description | Verifiable Outcome |
| :--- | :---: | :--- | :--- | :--- |
| FR-CORE-001 | [x] | FR | Support Python >=3.10 <3.14. | `uv run` and `uv pip` install works on specified versions. |
| FR-CORE-002 | [x] | FR | Standalone execution without LangChain. | `uv run pytest` passes without LangChain in environment. |
| FR-CORE-003 | [x] | FR | YAML-based configuration for Agents/Tasks. | Agents/Tasks initialized correctly from `.yaml` files. |

## Crew Orchestration (FR-CREW)

| ID | Status | Category | Requirement Description | Verifiable Outcome |
| :--- | :---: | :--- | :--- | :--- |
| FR-CREW-001 | [x] | FR | Sequential process execution. | Tasks executed in order assigned in `crew.py`. |
| FR-CREW-002 | [x] | FR | Hierarchical process execution with Manager. | Manager agent correctly delegates tasks and validates results. |
| FR-CREW-003 | [x] | FR | Role-based agent collaboration. | Agents utilize provided `role`, `goal`, and `backstory` in prompts. |

## Flow Orchestration (FR-FLOW)

| ID | Status | Category | Requirement Description | Verifiable Outcome |
| :--- | :---: | :--- | :--- | :--- |
| FR-FLOW-001 | [x] | FR | Event-driven triggers (`@start`, `@listen`). | Methods execute based on decorated flow events. |
| FR-FLOW-002 | [x] | FR | Conditional routing (`@router`). | Flow branches correctly based on method return value. |
| FR-FLOW-003 | [x] | FR | Structured state management. | Flow state (Pydantic) persisted and accessible across steps. |

## CLI & Tooling (FR-CLI)

| ID | Status | Category | Requirement Description | Verifiable Outcome |
| :--- | :---: | :--- | :--- | :--- |
| FR-CLI-001 | [x] | FR | `crewai create crew` command. | New project scaffold generated with correct directory structure. |
| FR-CLI-002 | [x] | FR | `crewai run` command. | Kickoff execution from the project root. |

## Enterprise/AMP (INT-AMP)

| ID | Status | Category | Requirement Description | Verifiable Outcome |
| :--- | :---: | :--- | :--- | :--- |
| INT-AMP-001 | [/] | INT | Tracing and Observability integration. | Agent metrics/traces visible in Crew Control Plane. |
| INT-AMP-002 | [/] | INT | Cloud & On-premise deployment support. | Framework successfully deployed in both environments. |

---

## Feature Codes
* **CORE**: Core Framework logic.
* **CREW**: Crew-based autonomous collaboration.
* **FLOW**: Event-driven workflow orchestration.
* **CLI**: Command-line interface utilities.
* **AMP**: Enterprise AMP Suite features.
