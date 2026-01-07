# CrewAI Constitution

> [!NOTE]
> For the documentation workflow and standards, see [README.md](../../README.md) and [strive_handbook.md](../strive/strive_handbook.md).

## Core Principles

### Independence from Frameworks
CrewAI is a lean, standalone multi-agent orchestration framework. It must remain completely independent of LangChain or other agent frameworks to ensure maximum performance and minimal technical debt.

### The "Agent-First" Rule
All documentation and code must be structured so that an AI agent with a 32k context window can understand the module's purpose without reading the entire repository. This includes:
- Clear file headers with "Intent" and "Dependencies".
- Traceable Requirement IDs for every functional block.

### Production-Grade Reliability
Every feature must be designed for reliability and scalability in production environments. This includes robust error handling, secure state management, and comprehensive observability.

### Seamless Collaboration
Crews must be optimized for autonomous collaboration, while Flows must provide precise control. The framework should enable the synergy between these two paradigms.

## Architectural Standards

### Event-Driven Orchestration (Flows)
Flows must utilize an event-driven architecture to manage complex execution paths with fine-grained control and consistent state management.

### Autonomous Agency (Crews)
Crews must empower agents with true autonomy, dynamic task delegation, and role-based collaboration.

### Graphics-as-Code First
Visualizations and diagrams (e.g., in CrewAI AMP) must be derivable from declarative schemas or code to ensure they stay synchronized with the system state.

## Documentation Ethics

### No "Ghost" Code
Code without a corresponding Requirement ID in `04_requirements_registry.md` is considered technical debt. New features must start in `02_specifications.md` and flow downstream.

### The 5-Minute Rule
A new developer (or agent) should be able to understand the "Intent" of any file in the source directory within 5 minutes of reading its header and the relevant documentation.
