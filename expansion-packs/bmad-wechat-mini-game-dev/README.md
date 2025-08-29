# BMad Expansion Pack: WeChat Mini-Game Development

**Version:** 1.1.0

## Overview

This expansion pack provides specialized agents, templates, and tasks to accelerate the development of games for the WeChat Mini-Game platform using the BMad Method.

It is designed to help you plan your game's structure, mechanics, and integration with WeChat's unique social and monetization features, as well as to speed up common development tasks.

---

## Components

### Specialist Agents

*   **`@wechat-game-designer`**
    *   An expert agent for planning and designing your WeChat mini-game. Its persona is optimized for the technical challenges of the Mini Game platform.
*   **`@wechat-game-dev`**
    *   A specialized developer agent fluent in the WeChat Mini Game framework, its APIs, and performance optimizations. This agent should be used for all implementation tasks.

### Document Template

*   **`gdd-wechat-template.yaml`**
    *   A YAML-based template for a Game Design Document that includes special sections for WeChat-specific features like social login, sharing, and monetization.

### Tasks

*   **`scaffold-wechat-page`**
    *   A task that can be used by the `@wechat-game-dev` agent to quickly create the four necessary files (`.js`, `.wxml`, `.wxss`, `.json`) for a new page in your mini-game.

---

## Quick-Start Workflow

### 1. Plan Phase

1.  **Create the Game Design Document:** Use the specialized designer to plan your game (e.g., for a Tetris game).
    ```bash
    @wechat-game-designer *create-doc {template: 'gdd-wechat-template.yaml', game_name: 'Tetris'}
    ```
2.  **Shard the GDD:** Use the Product Owner to break the design into actionable stories.
    ```bash
    @po shard docs/gdd.md
    ```

### 2. Development Phase

This phase is an iterative cycle for building each feature of your game.

1.  **Initial Scaffolding (Optional):** If you need to create new pages, use the specialized dev agent.
    ```bash
    @wechat-game-dev *scaffold-wechat-page
    ```
2.  **Development Cycle:** Repeat the following steps for each story.
    *   **Draft Story:**
        ```bash
        @sm *draft
        ```
    *   **Implement Story:** Use the specialized developer agent.
        ```bash
        @wechat-game-dev *develop-story {path/to/story.md}
        ```
    *   **Review Story:** Get a quality review from the Test Architect.
        ```bash
        @qa *review {path/to/story.md}
        ```
