# BMad Knowledge Base - WeChat Mini Game Development

## Overview

This is the game development expansion of BMad-Method (Breakthrough Method of Agile AI-driven Development), specializing in creating 2D games using the WeChat Mini Game framework with JavaScript. The system introduces a modular architecture with improved dependency management, bundle optimization, and support for both web and IDE environments, specifically optimized for WeChat Mini Game development workflows.

### Key Features for Game Development

- **Game-Specialized Agent System**: AI agents for each game development role (Designer, Developer, Scrum Master, QA)
- **WeChat Mini Game-Optimized Build System**: Automated dependency resolution for game assets and scenes
- **Dual Environment Support**: Optimized for both web UIs and game development IDEs
- **Game Development Resources**: Specialized templates, tasks, and checklists for WeChat Mini Game games
- **Performance-First Approach**: Built-in optimization patterns for cross-platform game deployment (60+ FPS target)
- **TDD Enforcement**: Test-driven development with JavaScript

### Game Development Focus

- **Target Engine**: WeChat Mini Game with JavaScript
- **Platform Strategy**: Cross-platform (Desktop, Mobile) with 2D support
- **Development Approach**: Agile story-driven development with TDD and performance focus
- **Performance Target**: 60+ FPS minimum on target devices
- **Architecture**: Object-based architecture using the WeChat Mini Game scene system and events

### When to Use BMad for Game Development

- **New Game Projects (Greenfield)**: Complete end-to-end game development from concept to deployment
- **Existing Game Projects (Brownfield)**: Feature additions, level expansions, and gameplay enhancements
- **Game Team Collaboration**: Multiple specialized roles working together on game features
- **Game Quality Assurance**: Structured testing with TDD, performance validation, and gameplay balance
- **Game Documentation**: Professional Game Design Documents, technical architecture, user stories

## How BMad Works for Game Development

### The Core Method

BMad transforms you into a "Player Experience CEO" - directing a team of specialized game development AI agents through structured workflows. Here's how:

1. **You Direct, AI Executes**: You provide game vision and creative decisions; agents handle implementation details
2. **Specialized Game Agents**: Each agent masters one game development role (Designer, Developer, Scrum Master, QA)
3. **Game-Focused Workflows**: Proven patterns guide you from game concept to deployed WeChat Mini Game
4. **Clean Handoffs**: Fresh context windows ensure agents stay focused and effective for game development

### The Two-Phase Game Development Approach

#### Phase 1: Game Design & Planning (Web UI - Cost Effective)

- Use large context windows for comprehensive game design
- Generate complete Game Design Documents and technical architecture
- Leverage multiple agents for creative brainstorming and mechanics refinement
- Create once, use throughout game development

#### Phase 2: Game Development (IDE - Implementation)

- Shard game design documents into manageable pieces
- Execute focused SM → Dev cycles for game features
- One game story at a time, sequential progress
- Real-time WeChat Mini Game operations, JavaScript coding, and game testing

### The Game Development Loop

```text
1. Game SM Agent (New Chat) → Creates next game story from sharded docs
2. You → Review and approve game story
3. Game Dev Agent (New Chat) → Implements approved game feature in WeChat Mini Game (TDD-first)
4. QA Agent (New Chat) → Reviews code, enforces TDD, validates performance
5. You → Verify game feature completion and 60+ FPS
6. Repeat until game epic complete
```

### Why This Works for Games

- **Context Optimization**: Clean chats = better AI performance for complex game logic
- **Role Clarity**: Agents don't context-switch = higher quality game features
- **Incremental Progress**: Small game stories = manageable complexity
- **Player-Focused Oversight**: You validate each game feature = quality control
- **Design-Driven**: Game specs guide everything = consistent player experience
- **Performance-First**: Every decision validated against 60+ FPS target

### Core Game Development Philosophy

#### Player-First Development

You are developing games as a "Player Experience CEO" - thinking like a game director with unlimited creative resources and a singular vision for player enjoyment.

#### Game Development Principles

1. **MAXIMIZE_PLAYER_ENGAGEMENT**: Push the AI to create compelling gameplay. Challenge mechanics and iterate.
2. **PERFORMANCE_IS_KING**: 60+ FPS is the minimum, not the target. Profile everything.
3. **TDD_MANDATORY**: Tests written first, no exceptions.
4. **GAMEPLAY_QUALITY_CONTROL**: You are the ultimate arbiter of fun. Review all game features.
5. **CREATIVE_OVERSIGHT**: Maintain the high-level game vision and ensure design alignment.
6. **ITERATIVE_REFINEMENT**: Expect to revisit game mechanics. Game development is not linear.
7. **CLEAR_GAME_INSTRUCTIONS**: Precise game requirements lead to better implementations.
8. **DOCUMENTATION_IS_KEY**: Good game design docs lead to good game features.
9. **START_SMALL_SCALE_FAST**: Test core mechanics, then expand and polish.
10. **EMBRACE_CREATIVE_CHAOS**: Adapt and overcome game development challenges.

## Getting Started with Game Development

### Quick Start Options for Game Development

#### Option 1: Web UI for Game Design

**Best for**: Game designers who want to start with comprehensive planning

1. Navigate to `dist/teams/` (after building)
2. Copy `wechat-mini-game-team.txt` content
3. Create new Gemini Gem or CustomGPT
4. Upload file with instructions: "Your critical operating instructions are attached, do not break character as directed"
5. Type `/help` to see available game development commands

#### Option 2: IDE Integration for Game Development

**Best for**: WeChat Mini Game developers using Cursor, Claude Code, Windsurf, Trae, Cline, Roo Code, Github Copilot

```bash
# Interactive installation (recommended)
npx bmad-method install
# Select the bmad-wechat-mini-game-dev expansion pack when prompted
```

**Installation Steps for Game Development**:

- Choose "Install expansion pack" when prompted
- Select "bmad-wechat-mini-game-dev" from the list
- Select your IDE from supported options:
  - **Cursor**: Native AI integration with WeChat Mini Game support
  - **Claude Code**: Anthropic's official IDE
  - **Windsurf**: Built-in AI capabilities
  - **Trae**: Built-in AI capabilities
  - **Cline**: VS Code extension with AI features
  - **Roo Code**: Web-based IDE with agent support
  - **GitHub Copilot**: VS Code extension with AI peer programming assistant

**Verify Game Development Installation**:

- `.bmad-core/` folder created with all core agents
- `.bmad-wechat-mini-game-dev/` folder with game development agents
- IDE-specific integration files created
- Game development agents available with `/BmadW` prefix

### Environment Selection Guide for Game Development

**Use Web UI for**:

- Game design document creation and brainstorming
- Cost-effective comprehensive game planning (especially with Gemini)
- Multi-agent game design consultation
- Creative ideation and mechanics refinement

**Use IDE for**:

- WeChat Mini Game project development and JavaScript coding
- Scene operations and object hierarchy management
- Game story management and implementation workflow
- WeChat Mini Game testing, profiling, and debugging

**Cost-Saving Tip for Game Development**: Create large game design documents in web UI, then copy to `docs/game-design-doc.md` and `docs/architecture.md` in your WeChat Mini Game project before switching to IDE for development.

### IDE-Only Game Development Workflow Considerations

**Can you do everything in IDE?** Yes, but understand the game development tradeoffs:

**Pros of IDE-Only Game Development**:

- Single environment workflow from design to WeChat Mini Game deployment
- Direct WeChat Mini Game project operations from start
- No copy/paste between environments
- Immediate WeChat Mini Game project integration

**Cons of IDE-Only Game Development**:

- Higher token costs for large game design document creation
- Smaller context windows for comprehensive game planning
- May hit limits during creative brainstorming phases
- Less cost-effective for extensive game design iteration
- **Note**: Gemini CLI with Gemini Pro's 1m context window, for the planning phase, makes IDE-Only Game Development feasible

**CRITICAL RULE for Game Development**:

- **ALWAYS use Game SM agent for story creation** - Never use bmad-master or bmad-orchestrator
- **ALWAYS use Game Dev agent for WeChat Mini Game implementation** - Never use bmad-master or bmad-orchestrator
- **Why this matters**: Game SM and Game Dev agents are specifically optimized for WeChat Mini Game workflows
- **No exceptions**: Even if using bmad-master for design, switch to Game SM → Game Dev for implementation

## Core Configuration for Game Development (core-config.yaml)

**New in V4**: The `expansion-packs/bmad-wechat-mini-game-dev/core-config.yaml` file enables BMad to work seamlessly with any WeChat Mini Game project structure, providing maximum flexibility for game development.

### Game Development Configuration

The expansion pack follows the standard BMad configuration patterns. Copy your core-config.yaml file to expansion-packs/bmad-wechat-mini-game-dev/ and add Game-specific configurations to your project's `core-config.yaml`:

```yaml
markdownExploder: true
prd:
  prdFile: docs/prd.md
  prdVersion: v4
  prdSharded: true
  prdShardedLocation: docs/prd
  epicFilePattern: epic-{n}*.md
architecture:
  architectureFile: docs/architecture.md
  architectureVersion: v4
  architectureSharded: true
  architectureShardedLocation: docs/architecture
gdd:
  gddVersion: v4
  gddSharded: true
  gddLocation: docs/game-design-doc.md
  gddShardedLocation: docs/gdd
  epicFilePattern: epic-{n}*.md
gamearchitecture:
  gamearchitectureFile: docs/architecture.md
  gamearchitectureVersion: v3
  gamearchitectureLocation: docs/architecture.md
  gamearchitectureSharded: true
  gamearchitectureShardedLocation: docs/architecture
gamebriefdocLocation: docs/game-brief.md
levelDesignLocation: docs/level-design.md
customTechnicalDocuments: null
devDebugLog: .ai/debug-log.md
devStoryLocation: docs/stories
slashPrefix: BmadW
# Sharded architecture files for developer reference
devLoadAlwaysFiles:
  - docs/architecture/9-coding-standards.md
  - docs/architecture/3-tech-stack.md
  - docs/architecture/8-wechat-mini-game-project-structure.md
```

## Complete Game Development Workflow

### Planning Phase (Web UI Recommended - Especially Gemini for Game Design!)

**Ideal for cost efficiency with Gemini's massive context for game brainstorming:**

**For All Game Projects**:

1. **Game Concept Brainstorming**: `/bmadw/game-designer` - Use `*game-design-brainstorming` task
2. **Game Brief**: Create foundation game document using `game-brief-tmpl`
3. **Game Design Document Creation**: `/bmadw/game-designer` - Use `game-design-doc-tmpl` for comprehensive game requirements
4. **Game Architecture Design**: `/bmadw/game-architect` - Use `game-architecture-tmpl` for WeChat Mini Game technical foundation
5. **Level Design Framework**: `/bmadw/game-designer` - Use `level-design-doc-tmpl` for level structure planning
6. **Document Preparation**: Copy final documents to WeChat Mini Game project as `docs/game-design-doc.md`, `docs/game-brief.md`, `docs/level-design.md` and `docs/architecture.md`

#### Example Game Planning Prompts

**For Game Design Document Creation**:

```text
"I want to build a [genre] 2D game in WeChat Mini Game that [core gameplay].
Help me brainstorm mechanics and create a comprehensive Game Design Document."
```

**For Game Architecture Design**:

```text
"Based on this Game Design Document, design a scalable WeChat Mini Game architecture
that can handle [specific game requirements] with 60+ FPS performance."
```

### Critical Transition: Web UI to WeChat Mini Game IDE

**Once game planning is complete, you MUST switch to IDE for WeChat Mini Game development:**

- **Why**: WeChat Mini Game development workflow requires scene operations, JavaScript coding, and real-time testing
- **Cost Benefit**: Web UI is more cost-effective for large game design creation; IDE is optimized for WeChat Mini Game development
- **Required Files**: Ensure `docs/game-design-doc.md` and `docs/architecture.md` exist in your WeChat Mini Game project

### WeChat Mini Game IDE Development Workflow

**Prerequisites**: Game planning documents must exist in `docs/` folder of WeChat Mini Game project

1. **Document Sharding** (CRITICAL STEP for Game Development):
   - Documents created by Game Designer/Architect (in Web or IDE) MUST be sharded for development
   - Use core BMad agents or tools to shard:
     a) **Manual**: Use core BMad `shard-doc` task if available
     b) **Agent**: Ask core `@bmad-master` agent to shard documents
   - Shards `docs/game-design-doc.md` → `docs/game-design/` folder
   - Shards `docs/architecture.md` → `docs/architecture/` folder
   - **WARNING**: Do NOT shard in Web UI - copying many small files to WeChat Mini Game is painful!

2. **Verify Sharded Game Content**:
   - At least one `feature-n.md` file in `docs/game-design/` with game stories in development order
   - WeChat Mini Game system documents and coding standards for game dev agent reference
   - Sharded docs for Game SM agent story creation

Resulting WeChat Mini Game Project Folder Structure:

- `docs/game-design/` - Broken down game design sections
- `docs/architecture/` - Broken down WeChat Mini Game architecture sections
- `docs/game-stories/` - Generated game development stories

3. **Game Development Cycle** (Sequential, one game story at a time):

   **CRITICAL CONTEXT MANAGEMENT for WeChat Mini Game Development**:
   - **Context windows matter!** Always use fresh, clean context windows
   - **Model selection matters!** Use most powerful thinking model for Game SM story creation
   - **ALWAYS start new chat between Game SM, Game Dev, and QA work**

   **Step 1 - Game Story Creation**:
   - **NEW CLEAN CHAT** → Select powerful model → `/bmadw/game-sm` → `*draft`
   - Game SM executes create-game-story task using `game-story-tmpl`
   - Review generated story in `docs/game-stories/`
   - _Optional_ - Use `/bmadw/game-po` -> `*validate-story-draft (story)` to confirm alignment
   - Update status from "Draft" to "Approved"

   **Step 2 - WeChat Mini Game Story Implementation (TDD)**:
   - **NEW CLEAN CHAT** → `/bmadw/game-developer`
   - Agent asks which game story to implement
   - Include story file content to save game dev agent lookup time
   - **CRITICAL**: Game Dev writes tests FIRST
   - Game Dev implements to make tests pass
   - Game Dev maintains File List of all WeChat Mini Game/JavaScript changes
   - Game Dev validates 60+ FPS performance
   - Game Dev marks story as "Ready for Review" when complete with all tests passing

   **Step 3 - Game QA Review**:
   - **NEW CLEAN CHAT** → `/bmadw/game-qa` → execute review-story task
   - QA enforces TDD compliance (tests written first)
   - QA validates 60+ FPS performance
   - QA can refactor and improve WeChat Mini Game code directly
   - QA appends results to story's QA Results section
   - If approved: Status → "Done"
   - If changes needed: Status stays "Review" with unchecked items for game dev

   **Step 4 - Repeat**: Continue Game SM → Game Dev → QA cycle until all game feature stories complete

**Important**: Only 1 game story in progress at a time, worked sequentially until all game feature stories complete.

### Game Story Status Tracking Workflow

Game stories progress through defined statuses:

- **Draft** → **Approved** → **InProgress** → **Ready for Review** → **Done**

Each status change requires user verification and approval before proceeding.

### Game Development Workflow Types

#### Greenfield Game Development

- Game concept brainstorming and mechanics design
- Game design requirements and feature definition
- WeChat Mini Game system architecture and technical design
- Game development execution with TDD
- Game testing, performance optimization (60+ FPS), and deployment

#### Brownfield Game Enhancement (Existing WeChat Mini Game Projects)

**Key Concept**: Brownfield game development requires comprehensive documentation of your existing WeChat Mini Game project for AI agents to understand game mechanics, object patterns, and technical constraints.

**Brownfield Game Enhancement Workflow**:

1. **Upload WeChat Mini Game project to Web UI** (GitHub URL, files, or zip)
2. **Create adapted Game Design Document**: `/bmadw/game-designer` - Modify `game-design-doc-tmpl` to include:
   - Analysis of existing scene structure
   - Integration points for new features
   - Save game compatibility requirements
   - Risk assessment for changes

3. **Game Architecture Planning**:
   - Use `/bmadw/game-architect` with `game-architecture-tmpl`
   - Focus on how new features integrate with existing WeChat Mini Game systems
   - Plan for gradual rollout and testing

4. **Story Creation for Enhancements**:
   - Use `/bmadw/game-sm` with `*create-game-story`
   - Stories should explicitly reference existing scenes/scripts to modify
   - Include integration testing requirements

**Critical Success Factors for Game Development**:

1. **Game Documentation First**: Always document existing code thoroughly before making changes
2. **WeChat Mini Game Context Matters**: Provide agents access to relevant scenes and scripts
3. **Gameplay Integration Focus**: Emphasize compatibility and non-breaking changes to game mechanics
4. **Incremental Approach**: Plan for gradual rollout and extensive game testing
5. **Performance Validation**: Every change must maintain 60+ FPS

## Document Creation Best Practices for Game Development

### Required File Naming for Game Framework Integration

- `docs/game-design-doc.md` - Game Design Document
- `docs/architecture.md` - WeChat Mini Game System Architecture Document

**Why These Names Matter for Game Development**:

- Game agents automatically reference these files during WeChat Mini Game development
- Game sharding tasks expect these specific filenames
- Game workflow automation depends on standard naming

### Cost-Effective Game Document Creation Workflow

**Recommended for Large Game Documents (Game Design Document, Game Architecture):**

1. **Use Web UI**: Create game documents in web interface for cost efficiency
2. **Copy Final Output**: Save complete markdown to your WeChat Mini Game project
3. **Standard Names**: Save as `docs/game-design-doc.md` and `docs/architecture.md`
4. **Switch to WeChat Mini Game IDE**: Use IDE agents for WeChat Mini Game development and smaller game documents

### Game Document Sharding

Game templates with Level 2 headings (`##`) can be automatically sharded:

**Original Game Design Document**:

```markdown
## Core Gameplay Mechanics

## Player Progression System

## Level Design Framework

## Technical Requirements
```

**After Sharding**:

- `docs/game-design/core-gameplay-mechanics.md`
- `docs/game-design/player-progression-system.md`
- `docs/game-design/level-design-framework.md`
- `docs/game-design/technical-requirements.md`

Use the `shard-doc` task or `@kayvan/markdown-tree-parser` tool for automatic game document sharding.

## Game Agent System

### Core Game Development Team

| Agent            | Role                   | Primary Functions                                | When to Use                                  |
| ---------------- | ---------------------- | ------------------------------------------------ | -------------------------------------------- |
| `game-designer`  | Game Designer          | Game mechanics, creative design, GDD             | Game concept, mechanics, creative direction  |
| `game-developer` | WeChat Mini Game Developer | JavaScript implementation, TDD, optimization    | All WeChat Mini Game development tasks (tests first!)   |
| `game-sm`        | Game Scrum Master      | Game story creation, sprint planning             | Game project management, workflow            |
| `game-architect` | Game Architect         | WeChat Mini Game system design, performance architecture    | Complex WeChat Mini Game systems, 60+ FPS planning      |
| `game-qa`        | Game QA & TDD Enforcer | TDD enforcement, performance validation, testing | Code review, test verification, optimization |

### Game Agent Interaction Commands

#### IDE-Specific Syntax for Game Development

**Game Agent Loading by IDE**:

- **Claude Code**: `/bmadw/game-designer`, `/bmadw/game-developer`, `/bmadw/game-sm`, `/bmadw/game-architect`, `/bmadw/game-qa`
- **Cursor**: `@bmadw/game-designer`, `@bmadw/game-developer`, `@bmadw/game-sm`, `@bmadw/game-architect`, `@bmadw/game-qa`
- **Windsurf**: `/bmadw/game-designer`, `/bmadw/game-developer`, `/bmadw/game-sm`, `/bmadw/game-architect`, `/bmadw/game-qa`
- **Trae**: `@bmadw/game-designer`, `@bmadw/game-developer`, `@bmadw/game-sm`, `@bmadw/game-architect`, `@bmadw/game-qa`
- **Roo Code**: Select mode from mode selector with bmadw prefix
- **GitHub Copilot**: Open the Chat view (`⌃⌘I` on Mac, `Ctrl+Alt+I` on Windows/Linux) and select the appropriate game agent

**Common Game Development Task Commands**:

- `*help` - Show available game development commands
- `*status` - Show current game development context/progress
- `*exit` - Exit the game agent mode
- `*game-design-brainstorming` - Brainstorm game concepts and mechanics (Game Designer)
- `*draft` - Create next game development story (Game SM agent)
- `*review {story}` - Review story with TDD enforcement (Game QA agent)
- `*enforce-tdd {story}` - Verify tests written first (Game QA agent)
- `*correct-course-game` - Course correction for game development issues
- `*advanced-elicitation` - Deep dive into game requirements

## Game-Specific Development Guidelines

### WeChat Mini Game + JavaScript Standards

**Project Structure**:

```text
WeChatMiniGameProject/
├── images/             # Image assets
├── js/                 # JavaScript scripts
│   ├── libs/           # Third-party libraries
│   ├── base/           # Base classes
│   ├── player/         # Player-related scripts
│   ├── enemies/        # Enemy scripts
│   ├── systems/        # Game systems
│   ├── ui/             # UI scripts
│   └── utils/          # Utility scripts
├── audio/              # Audio assets
├── game.js             # Game entry point
├── game.json           # Game configuration
├── project.config.json # Project configuration
└── project.private.config.json # Private project configuration
```

**Performance Requirements**:

- Maintain 60+ FPS minimum on target devices
- Frame time under 16.67ms consistently
- Memory usage under platform-specific limits
- Loading times under 3 seconds for scenes
- Input latency under 50ms

**Code Quality**:

- Modern JavaScript with best practices
- Object-based architecture (composition over inheritance)
- Event-based communication between systems
- JSON-driven data management
- TDD with 80% minimum test coverage

### Game Development Story Structure

**Story Requirements**:

- Clear reference to Game Design Document section
- Specific acceptance criteria for game functionality
- Technical implementation details for WeChat Mini Game
- Performance requirements (60+ FPS validation)
- Testing requirements (tests written FIRST)

**Story Categories**:

- **Core Mechanics**: Fundamental gameplay systems
- **Scene Content**: Individual scenes and level implementation
- **UI/UX**: UI elements and player experience features
- **Performance**: Optimization and technical improvements
- **Polish**: Visual effects, audio, and game feel enhancements

### Quality Assurance for Games

**Testing Approach (TDD Mandatory)**:

- Unit tests written FIRST
- Integration tests for scene interactions
- Performance benchmarking with the WeChat Mini Game profiler
- Gameplay testing and balance validation
- Cross-platform compatibility testing
- 80% minimum test coverage

**Performance Monitoring**:

- Frame rate consistency tracking (60+ FPS)
- Draw call optimization
- Memory usage monitoring
- Scene loading performance
- Input responsiveness validation
- Battery usage optimization (mobile)

## Usage Patterns and Best Practices for Game Development

### Environment-Specific Usage for Games

**Web UI Best For Game Development**:

- Initial game design and creative brainstorming phases
- Cost-effective large game document creation
- Game agent consultation and mechanics refinement
- Multi-agent game workflows with orchestrator

**WeChat Mini Game IDE Best For Game Development**:

- Active WeChat Mini Game development with TDD
- Scene and object hierarchy management
- Game story management and development cycles
- Performance profiling and optimization

### Quality Assurance for Game Development

- Use appropriate game agents for specialized tasks
- Follow Agile ceremonies and game review processes
- Use game-specific checklists:
  - `game-architect-checklist` for architecture reviews
  - `game-change-checklist` for change validation
  - `game-design-checklist` for design reviews
  - `game-story-dod-checklist` for story quality (TDD compliance)
  - `game-po-checklist` for product owner validation
- Regular validation with game templates

### Performance Optimization for Game Development

- Use specific game agents vs. `bmad-master` for focused WeChat Mini Game tasks
- Choose appropriate game team size for project needs
- Leverage game-specific technical preferences for consistency
- Regular context management and cache clearing for WeChat Mini Game workflows
- Profile everything, optimize based on data

## Game Development Team Roles

### Game Designer

- **Primary Focus**: Game mechanics, player experience, design documentation
- **Key Outputs**: Game Brief, Game Design Document, Level Design Framework
- **Specialties**: Brainstorming, game balance, player psychology, creative direction

### Game Developer

- **Primary Focus**: WeChat Mini Game implementation with TDD, JavaScript excellence, 60+ FPS optimization
- **Key Outputs**: Working game features with tests, optimized WeChat Mini Game code, performance validation
- **Specialties**: TDD practices, JavaScript, object architecture, cross-platform development

### Game Scrum Master

- **Primary Focus**: Game story creation, development planning, agile process
- **Key Outputs**: Detailed implementation stories, sprint planning, quality assurance
- **Specialties**: Story breakdown, developer handoffs, process optimization

### Game Architect

- **Primary Focus**: WeChat Mini Game system design, performance architecture
- **Key Outputs**: Technical architecture, performance budgets, optimization strategies
- **Specialties**: Object patterns, event architecture, 60+ FPS planning

### Game QA

- **Primary Focus**: TDD enforcement, test verification, performance validation
- **Key Outputs**: Test coverage reports, performance metrics, code quality assessment
- **Specialties**: Testing frameworks, profiling, optimization validation

## Platform-Specific Considerations

### Cross-Platform Development

- Use the WeChat Mini Game API for platform-agnostic input
- Export templates for each target platform
- Test on all target platforms regularly
- Optimize for different screen resolutions and aspect ratios
- Platform-specific performance targets

### Mobile Optimization

- Touch input with the WeChat Mini Game API
- Battery usage optimization
- Performance scaling for different device capabilities
- App store compliance and export settings
- Reduced draw calls and texture memory

### Performance Targets

- **Desktop**: 60+ FPS at native resolution (144 FPS for high-refresh displays)
- **Mobile**: 60 FPS on mid-range devices minimum
- **Loading**: Scene transitions under 2 seconds
- **Memory**: Within platform-specific limits

## Success Metrics for Game Development

### Technical Metrics

- Frame rate consistency (>95% of time at 60+ FPS)
- Frame time variance (<2ms variation)
- Memory usage within budgets
- Loading time targets met
- Zero critical bugs in core gameplay systems
- 80%+ test coverage (TDD compliance)

### Player Experience Metrics

- Input latency under 50ms
- Tutorial completion rate >80%
- Level completion rates appropriate for difficulty curve
- Average session length meets design targets
- Player retention and engagement metrics

### Development Process Metrics

- All stories have tests written FIRST
- Story completion within estimated timeframes
- Code quality metrics (test coverage, static analysis)
- Documentation completeness and accuracy
- Team velocity and delivery consistency

## Common WeChat Mini Game Development Patterns

### Scene Management

- Use scene inheritance for variant levels
- Global managers for persistent systems
- Scene transitions with loading screens
- Resource preloading for smooth gameplay

### Object Architecture

- Composition over inheritance with scene instances
- Event-based communication between objects
- Object groups for efficient queries
- Tool scripts for editor enhancement

### Performance Patterns

- Object pooling for frequently spawned objects
- MultiMesh for many identical objects
- LOD systems with visibility ranges
- Occlusion culling for complex scenes

## Success Tips for Game Development

- **Use Gemini for game design planning** - The team-game-dev bundle provides collaborative game expertise
- **Enforce TDD religiously** - Tests first, implementation second, no exceptions
- **Profile constantly** - Measure don't guess
- **Follow the Game SM → Game Dev → QA cycle** - This ensures systematic game progress
- **Keep conversations focused** - One game agent, one WeChat Mini Game task per conversation
- **Review everything** - Always verify 60+ FPS before marking features complete

## Contributing to BMad-Method Game Development

### Game Development Contribution Guidelines

For full details, see `CONTRIBUTING.md`. Key points for game development:

**Fork Workflow for Game Development**:

1. Fork the repository
2. Create game development feature branches
3. Submit PRs to `next` branch (default) or `main` for critical game development fixes only
4. Keep PRs small: 200-400 lines ideal, 800 lines maximum
5. One game feature/fix per PR

**Game Development PR Requirements**:

- Clear descriptions (max 200 words) with What/Why/How/Testing for game features
- Use conventional commits (feat:, fix:, docs:) with game context
- Atomic commits - one logical game change per commit
- Must align with game development guiding principles
- Include performance impact assessment

**Game Development Core Principles**:

- **Game Dev Agents Must Be Lean**: Minimize dependencies, save context for WeChat Mini Game code
- **Natural Language First**: Everything in markdown, no code in game development core
- **Core vs Game Expansion Packs**: Core for universal needs, game packs for WeChat Mini Game specialization
- **Game Design Philosophy**: "Game dev agents code WeChat Mini Game, game planning agents plan gameplay"
- **Performance First**: Every change validated against 60+ FPS target
- **TDD Mandatory**: Tests before implementation, always

## Game Development Expansion Pack System

### This Game Development Expansion Pack

This WeChat Mini Game Development expansion pack extends BMad-Method beyond traditional software development into professional game development. It provides specialized game agent teams, WeChat Mini Game templates, and game workflows while keeping the core framework lean and focused on general development.

### Why Use This Game Development Expansion Pack?

1. **Keep Core Lean**: Game dev agents maintain maximum context for WeChat Mini Game coding
2. **Game Domain Expertise**: Deep, specialized WeChat Mini Game and game development knowledge
3. **Community Game Innovation**: Game developers can contribute and share WeChat Mini Game patterns
4. **Modular Game Design**: Install only game development capabilities you need
5. **Performance Focus**: Built-in 60+ FPS validation and optimization patterns
6. **TDD Enforcement**: Mandatory test-first development practices

### Using This Game Development Expansion Pack

1. **Install via CLI**:

   ```bash
   npx bmad-method install
   # Select "Install game development expansion pack" option
   ```

2. **Use in Your Game Workflow**: Installed game agents integrate seamlessly with existing BMad agents

### Creating Custom Game Development Extensions

Use the **expansion-creator** pack to build your own game development extensions:

1. **Define Game Domain**: What game development expertise are you capturing?
2. **Design Game Agents**: Create specialized game roles with clear WeChat Mini Game boundaries
3. **Build Game Resources**: Tasks, templates, checklists for your game domain
4. **Test & Share**: Validate with real WeChat Mini Game use cases, share with game development community

**Key Principle**: Game development expansion packs democratize game development expertise by making specialized WeChat Mini Game and game design knowledge accessible through AI agents.

## Getting Help with Game Development

- **Commands**: Use `*/*help` in any environment to see available game development commands
- **Game Agent Switching**: Use `*/*switch game-agent-name` with orchestrator for role changes
- **Game Documentation**: Check `docs/` folder for WeChat Mini Game project-specific context
- **Game Community**: Discord and GitHub resources available for game development support
- **Game Contributing**: See `CONTRIBUTING.md` for full game development guidelines

This knowledge base provides the foundation for effective game development using the BMad-Method framework with specialized focus on WeChat Mini Game creation using JavaScript with mandatory TDD practices and 60+ FPS performance targets.
```
