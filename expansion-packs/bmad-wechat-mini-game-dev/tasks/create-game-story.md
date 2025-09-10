# Create Game Story Task

## Purpose

To identify the next logical game story based on project progress and epic definitions, and then to prepare a comprehensive, self-contained, and actionable story file using the `Game Story Template`. This task ensures the story is enriched with all necessary technical context, WeChat Mini Game-specific requirements (object architecture, JavaScript language selection, 60+ FPS performance targets), TDD test requirements, and acceptance criteria, making it ready for efficient implementation by a Game Developer Agent with minimal need for additional research or finding its own context.

## SEQUENTIAL Task Execution (Do not proceed until current Task is complete)

### 0. Load Core Configuration and Check Workflow

- Load `.bmad-wechat-mini-game-dev/config.yaml` from the project root
- If the file does not exist, HALT and inform the user: "core-config.yaml not found. This file is required for story creation. You can either: 1) Copy core-config.yaml from GITHUB bmad-core/ and configure it for your game project OR 2) Run the BMad installer against your project to upgrade and add the file automatically. Please add and configure before proceeding."
- Extract key configurations: `devStoryLocation`, `prd.*`, `architecture.*`, `workflow.*`

### 1. Identify Next Story for Preparation

#### 1.1 Locate Epic Files and Review Existing Stories

- Based on `prdSharded` from config, locate epic files (sharded location/pattern or monolithic PRD sections)
- If `devStoryLocation` has story files, load the highest `{epicNum}.{storyNum}.story.md` file
- **If highest story exists:**
  - Verify status is 'Done'. If not, alert user: "ALERT: Found incomplete story! File: {lastEpicNum}.{lastStoryNum}.story.md Status: [current status] Check if TDD tests are passing. You should fix this story first, but would you like to accept risk & override to create the next story in draft?"
  - If proceeding, select next sequential story in the current epic
  - If epic is complete, prompt user: "Epic {epicNum} Complete: All stories in Epic {epicNum} have been completed. Would you like to: 1) Begin Epic {epicNum + 1} with story 1 2) Select a specific story to work on 3) Cancel story creation"
  - **CRITICAL**: NEVER automatically skip to another epic. User MUST explicitly instruct which story to create.
- **If no story files exist:** The next story is ALWAYS 1.1 (first story of first epic)
- Announce the identified story to the user: "Identified next story for preparation: {epicNum}.{storyNum} - {Story Title}"

### 2. Gather Story Requirements and Previous Story Context

- Extract story requirements from the identified epic file or PRD section
- If previous story exists, review Dev Agent Record sections for:
  - Completion Notes and Debug Log References
  - Implementation deviations and technical decisions
  - WeChat Mini Game-specific challenges (object structure, event connections, 60+ FPS violations)
  - Language decisions (JavaScript choices and rationale)
  - Resource loading and object pooling implementations
  - TDD test coverage and any failing tests
- Extract relevant insights that inform the current story's preparation

### 3. Gather Architecture Context

#### 3.1 Determine Architecture Reading Strategy

- **If `architectureVersion: >= v3` and `architectureSharded: true`**: Read `{architectureShardedLocation}/index.md` then follow structured reading order below
- **Else**: Use monolithic `architectureFile` for similar sections

#### 3.2 Read Architecture Documents Based on Story Type

**For ALL Game Stories:** tech-stack.md, wechat-mini-game-project-structure.md, coding-standards.md, test-strategy and standards.md

**For Gameplay/Mechanics Stories, additionally:** gameplay-systems-architecture.md, object-architecture-details.md, physics-configuration.md, input-system-architecture.md, state-machine-architecture.md, resource-architecture.md

**For UI/UX Stories, additionally:** object-architecture-details.md, ui-architecture.md, ui-component-system.md, ui-state-management.md, scene-management-architecture.md

**For Backend/Services Stories, additionally:** resource-architecture.md, data-persistence-architecture.md, save-system-implementation.md, analytics-integration.md, multiplayer-architecture.md

**For Graphics/Rendering Stories, additionally:** rendering-settings.md, shader-guidelines.md, sprite-management.md, particle-systems.md

**For Audio Stories, additionally:** audio-architecture.md, audio-mixing-configuration.md, sound-bank-management.md

#### 3.3 Extract Story-Specific Technical Details

Extract ONLY information directly relevant to implementing the current story. Do NOT invent new patterns, systems, or standards not in the source documents.

Extract:

- Specific WeChat Mini Game objects and their inheritance hierarchy
- Language selection rationale (JavaScript for each component)
- Object composition patterns and event connections
- Scene and resource organization requirements
- Input handling configurations
- Physics settings and collision layers
- UI element anchoring and theme specifications
- Resource naming conventions and folder structures
- Performance budgets (60+ FPS minimum, frame time <16.67ms, draw calls)
- Platform export settings (desktop, mobile)
- TDD requirements

ALWAYS cite source documents: `[Source: architecture/{filename}.md#{section}]`

### 4. WeChat Mini Game-Specific Technical Analysis

#### 4.1 Language Strategy Analysis

- Document JavaScript enforcement
- Identify interop boundaries between JavaScript and other languages
- Note any plugin requirements
- Specify object pooling needs for spawned entities

#### 4.2 Scene and Object Planning

- Identify which scenes will be modified or created
- List scene inheritance and composition patterns
- Document object tree structure with parent-child relationships
- Specify scene instancing and pooling requirements
- Plan event connections between objects
- Define global manager needs

#### 4.3 Object Architecture

- Define custom object classes needed
- Specify Resource classes for data management
- Document event emission and connection patterns
- Note UI components and theme requirements
- Plan export variables for inspector configuration

#### 4.4 Resource Requirements

- List texture requirements with import settings
- Define Animation needs
- Specify Audio resources and bus routing
- Document shader and material requirements
- Note font resources and theme variations
- Plan resource preloading vs lazy loading strategy

### 5. Populate Story Template with Full Context

- Create new story file: `{devStoryLocation}/{epicNum}.{storyNum}.story.md` using Game Story Template
- Fill in basic story information: Title, Status (Draft), Story statement, Acceptance Criteria from Epic/PRD
- **`Dev Notes` section (CRITICAL):**
  - CRITICAL: This section MUST contain ONLY information extracted from architecture documents and PRD. NEVER invent or assume technical details.
  - Include ALL relevant technical details from Steps 2-4, organized by category:
    - **Previous Story Insights**: Key learnings from previous story implementation
    - **Language Strategy**: JavaScript decisions for each component [with source references]
    - **Object Architecture**: Specific objects, inheritance, event patterns [with source references]
    - **Scene Specifications**: Scene modifications, object trees, instancing [with source references]
    - **Input Configuration**: Input handling [with source references]
    - **UI Implementation**: UI elements, anchoring, themes [with source references]
    - **Resource Pipeline**: Resource requirements, import settings, pooling strategy
    - **Performance Targets**: 60+ FPS requirement, frame time budget, profiler metrics
    - **Platform Considerations**: Export template differences, platform-specific code
    - **TDD Requirements**: Test-first development
  - Every technical detail MUST include its source reference: `[Source: architecture/{filename}.md#{section}]`
  - If information for a category is not found in the architecture docs, explicitly state: "No specific guidance found in architecture docs"
- **`Tasks / Subtasks` section:**
  - Generate detailed, sequential list of technical tasks based ONLY on: Epic/PRD Requirements, Story AC, Reviewed Architecture Information
  - Include WeChat Mini Game-specific tasks:
    - Write failing tests FIRST (TDD Red phase)
    - Scene setup and object hierarchy creation
    - Object implementation
    - Event connection and event handling
    - Input integration
    - Physics configuration
    - UI with responsive anchoring
    - Performance profiling (maintain 60+ FPS)
    - Make tests pass (TDD Green phase)
    - Refactor while keeping tests green (TDD Refactor phase)
  - Each task must reference relevant architecture documentation
  - Include testing as explicit subtasks
  - Link tasks to ACs where applicable (e.g., `Task 1 (AC: 1, 3)`)
- Add notes on WeChat Mini Game project structure alignment or discrepancies found in Step 4

### 6. Story Draft Completion and Review

- Review all sections for completeness and accuracy
- Verify all source references are included for technical details
- Ensure WeChat Mini Game-specific requirements are comprehensive:
  - All scenes and object trees documented
  - Event connections clear
  - Resource requirements specified
  - 60+ FPS performance targets defined
  - TDD test requirements explicit
- Update status to "Draft" and save the story file
- Execute `.bmad-wechat-mini-game-dev/tasks/execute-checklist` `.bmad-wechat-mini-game-dev/checklists/game-story-dod-checklist`
- Provide summary to user including:
  - Story created: `{devStoryLocation}/{epicNum}.{storyNum}.story.md`
  - Status: Draft
  - Language strategy decisions (JavaScript components)
  - Key WeChat Mini Game objects and systems included
  - Scene/object modifications required
  - Resource requirements identified
  - TDD test coverage planned
  - Performance impact assessment (60+ FPS maintained?)
  - Any deviations or conflicts noted between PRD and architecture
  - Checklist Results
  - Next steps: For complex WeChat Mini Game features, suggest the user review the story draft and optionally test critical assumptions in the WeChat Mini Game Editor

### 7. WeChat Mini Game-Specific Validation

Before finalizing, ensure:

- [ ] TDD approach specified (tests to write first)
- [ ] All object inheritance and composition patterns documented
- [ ] Event connections and event flow mapped
- [ ] Scene instancing and pooling strategy defined
- [ ] Input handling configured
- [ ] UI follows WeChat Mini Game anchoring best practices
- [ ] Performance profiling points identified (60+ FPS validation)
- [ ] Resource import settings documented
- [ ] Platform export settings noted
- [ ] Object pooling implemented for spawned entities

This task ensures game development stories are immediately actionable and enable efficient AI-driven development of WeChat Mini Game features with mandatory TDD practices and 60+ FPS performance targets.
```
