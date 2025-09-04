# BMad Expansion Pack: WeChat Mini-Game Development

**Version:** 1.0.0
**Author:** Jules (AI Assistant)

## Overview

This expansion pack provides a comprehensive, structured environment for developing WeChat Mini-Games using the BMad Method. It is built based on the official WeChat Mini Game documentation and aligns with the best practices of other game development packs in the BMad ecosystem.

This pack includes specialized agents, a detailed development workflow, document templates, and quality-control checklists to guide you from concept to release.

---

## Components

### Core Configuration
*   **`config.yaml`**: Contains the metadata for this expansion pack.

### Specialist Agents
*   **`@wechat-game-designer`**: An expert agent for planning your game, with deep knowledge of the WeChat Mini Game engine-like environment (scenes, entities, components).
*   **`@wechat-game-dev`**: A specialized developer agent for implementing game features in TypeScript, following the platform's best practices.

### Data & Guidelines
*   **`data/development-guidelines.md`**: The central source of truth for all technical standards, derived from official documentation. Both agents are aware of these guidelines.

### Workflows
*   **`workflows/wechat-game-dev-greenfield.yaml`**: Defines a step-by-step development process from creating a GDD to implementation, mirroring the official WeChat lifecycle.

### Templates
*   **`templates/gdd-wechat-template.yaml`**: A template for creating a Game Design Document tailored for WeChat Mini-Games.

### Tasks
*   **`tasks/scaffold-wechat-page.md`**: A task for the `@wechat-game-dev` agent to quickly scaffold new pages.

### Checklists
*   **`checklists/game-story-dod-checklist.md`**: A "Definition of Done" checklist to ensure every story is completed to a consistent quality standard.

### Web UI Support
*   **`agent-teams/wechat-mini-game-team.yaml`**: Defines the agent team for use in web-based AI platforms, allowing you to load the entire team at once.

---

## Quick-Start Workflow

The primary workflow is defined in `workflows/wechat-game-dev-greenfield.yaml`. You can use the `@bmad-orchestrator` in a web UI to guide you through it, or follow the steps manually in an IDE:

1.  **Plan Your Game:**
    ```bash
    @wechat-game-designer *create-doc {template: 'gdd-wechat-template.yaml', game_name: 'YourGame'}
    ```
2.  **Implement Features:**
    ```bash
    @wechat-game-dev *develop-story {path/to/story.md}
    ```
