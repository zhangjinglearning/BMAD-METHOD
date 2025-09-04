# BMad Expansion Pack: WeChat Mini-Game Development

**Version:** 1.0.0
**Author:** Jules (AI Assistant)

## Overview

This expansion pack provides a comprehensive, structured environment for developing WeChat Mini-Games using the BMad Method. It includes specialized agents, templates, and quality-control checklists that align with the best practices of other game development packs in the BMad ecosystem.

This pack is designed to help you plan your game's structure, mechanics, and integration with WeChat's unique features, while ensuring a high-quality, maintainable codebase.

---

## Components

### Core Configuration

*   **`config.yaml`**: Contains the metadata for this expansion pack.

### Specialist Agents

*   **`@wechat-game-designer`**: An expert agent for planning your game. It is aware of the technical standards in `development-guidelines.md`.
*   **`@wechat-game-dev`**: A specialized developer agent for implementing game features, also aware of the development guidelines.

### Data & Guidelines

*   **`data/development-guidelines.md`**: The central source of truth for all technical preferences, coding standards, and anti-patterns for your project. Both agents use this file for context.

### Templates

*   **`templates/gdd-wechat-template.yaml`**: A YAML-based template for creating a comprehensive Game Design Document tailored for WeChat Mini-Games.

### Tasks

*   **`tasks/scaffold-wechat-page.md`**: A task for the `@wechat-game-dev` agent to quickly scaffold new pages.

### Checklists

*   **`checklists/game-story-dod-checklist.md`**: A "Definition of Done" checklist to ensure every story is completed to a consistent quality standard.

### Web UI Support

*   **`agent-teams/wechat-mini-game-team.yaml`**: Defines the agent team for use in web-based AI platforms. Use the `web-builder.js` tool to bundle this team for upload to a Custom GPT or other web UI.

---

## Quick-Start Workflow

### 1. Plan Phase

1.  **Create the Game Design Document:**
    ```bash
    @wechat-game-designer *create-doc {template: 'gdd-wechat-template.yaml', game_name: 'YourGame'}
    ```
2.  **Shard the GDD:**
    ```bash
    @po shard docs/gdd.md
    ```

### 2. Development Phase

1.  **Draft a Story:**
    ```bash
    @sm *draft
    ```
2.  **Implement the Story:**
    ```bash
    @wechat-game-dev *develop-story {path/to/story.md}
    ```
3.  **Review and Verify:** Before marking as done, use the checklist and have the `@qa` agent review.
    ```bash
    @qa *review {path/to/story.md}
    ```
