# Correct Course Task - WeChat Mini Game Development

## Purpose

- Guide a structured response to WeChat Mini Game development change triggers using the `.bmad-wechat-mini-game-dev/checklists/game-change-checklist`.
- Analyze the impacts of changes on game features, object systems, and performance targets (60+ FPS).
- Explore WeChat Mini Game-specific solutions (e.g., JavaScript optimization, scene restructuring, platform export adjustments).
- Draft specific, actionable proposed updates to affected game artifacts (e.g., GDD sections, technical specs, WeChat Mini Game project settings).
- Produce a consolidated "WeChat Mini Game Development Change Proposal" document for review and approval.
- Ensure clear handoff path for changes requiring fundamental redesign, language migration, or architecture updates.

## Instructions

### 1. Initial Setup & Mode Selection

- **Acknowledge Task & Inputs:**
  - Confirm with the user that the "WeChat Mini Game Development Correct Course Task" is being initiated.
  - Verify the change trigger (e.g., 60+ FPS performance issue, JavaScript migration need, object system refactor, platform export problem).
  - Confirm access to relevant game artifacts:
    - Game Design Document (GDD)
    - Technical Design Documents
    - WeChat Mini Game Architecture specifications (object hierarchy, event flow)
    - Performance budgets (60+ FPS minimum) and platform requirements
    - Current sprint's game stories with TDD test coverage
    - Asset import settings and resource management
    - Language strategy documentation (JavaScript)
  - Confirm access to `.bmad-wechat-mini-game-dev/checklists/game-change-checklist`.

- **Establish Interaction Mode:**
  - Ask the user their preferred interaction mode:
    - **"Incrementally (Default & Recommended):** Work through the game-change-checklist section by section, discussing findings and drafting changes collaboratively. Best for complex object restructuring, language migrations, or performance optimizations."
    - **"YOLO Mode (Batch Processing):** Conduct batched analysis and present consolidated findings. Suitable for straightforward scene optimizations or export setting adjustments."
  - Confirm the selected mode and inform: "We will now use the game-change-checklist to analyze the change and draft proposed updates specific to our WeChat Mini Game development context with 60+ FPS targets and TDD practices."

### 2. Execute Game Development Checklist Analysis

- Systematically work through the game-change-checklist sections:
  1. **Change Context & Game Impact**
  2. **Feature/System Impact Analysis**
  3. **Technical Artifact Conflict Resolution**
  4. **Performance & Platform Evaluation**
  5. **Path Forward Recommendation**

- For each checklist section:
  - Present WeChat Mini Game-specific prompts and considerations
  - Analyze impacts on:
    - WeChat Mini Game scenes and object hierarchies
    - Event connections and dependencies
    - Performance metrics (60+ FPS requirement, frame time, draw calls)
    - JavaScript boundaries
    - Resource loading and object pooling
    - Platform export templates and settings
    - TDD test coverage
  - Discuss findings with performance profiler data
  - Record status: `[x] Addressed`, `[N/A]`, `[!] Further Action Needed`
  - Document WeChat Mini Game-specific decisions and language choices

### 3. Draft Game-Specific Proposed Changes

Based on the analysis and agreed path forward:

- **Identify affected game artifacts requiring updates:**
  - GDD sections (mechanics, systems, progression)
  - Technical specifications (object architecture, 60+ FPS targets)
  - WeChat Mini Game-specific configurations (project settings, export presets)
  - Game story modifications (TDD requirements, language choices)
  - Resource import settings and compression
  - Platform export template configurations
  - Test suite updates

- **Draft explicit changes for each artifact:**
  - **Game Stories:** Revise story text, TDD test requirements, JavaScript language selection
  - **Technical Specs:** Update object hierarchies, event architectures, 60+ FPS validation
  - **WeChat Mini Game Configurations:** Propose project settings, rendering options, export templates
  - **GDD Updates:** Modify feature descriptions, balance parameters, progression systems
  - **Resource Specifications:** Adjust import settings, compression, pooling strategies
  - **Performance Targets:** Ensure 60+ FPS minimum, frame time <16.67ms, draw call budgets
  - **Test Coverage:** Update tests

- **Include WeChat Mini Game-specific details:**
  - Scene tree structure changes
  - Object composition updates
  - Event refactoring needs
  - Shader/material optimizations
  - Object pooling implementations
  - Export preset modifications

### 4. Generate "WeChat Mini Game Development Change Proposal"

- Create a comprehensive proposal document containing:

  **A. Change Summary:**
  - Original issue (60+ FPS violation, language inefficiency, object bottleneck)
  - WeChat Mini Game systems affected (scenes, objects, events)
  - Platform/performance implications (frame time impact)
  - Chosen solution approach (JavaScript optimization, pooling)

  **B. Technical Impact Analysis:**
  - WeChat Mini Game object architecture changes needed
  - Performance implications (profiler metrics, FPS measurements)
  - Language strategy adjustments
  - Resource loading and pooling modifications
  - Platform export compatibility effects
  - TDD test suite impacts

  **C. Specific Proposed Edits:**
  - For each game story: "Change Story GS-X.Y from: [old] To: [new with TDD requirements]"
  - For technical specs: "Update WeChat Mini Game Architecture Section X: [object/event changes]"
  - For GDD: "Modify [Feature] in Section Y: [updates with performance targets]"
  - For project.config.json: "Change [Setting] from [old_value] to [new_value]"

  **D. Implementation Considerations:**
  - Required WeChat Mini Game version
  - Resource reimport with optimized settings
  - Scene and object refactoring requirements
  - JavaScript performance optimization needs
  - Object pooling implementation
  - Platform export template testing
  - TDD test updates (Red-Green-Refactor cycle)

### 5. Finalize & Determine Next Steps

- Obtain explicit approval for the "WeChat Mini Game Development Change Proposal"
- Verify 60+ FPS targets are maintained post-change
- Provide the finalized document to the user

- **Based on change scope:**
  - **Minor adjustments (can be handled in current sprint):**
    - Confirm task completion
    - Verify TDD tests are updated
    - Suggest handoff to game-developer agent for implementation
    - Note required performance profiling validation
  - **Major changes (require replanning):**
    - Clearly state need for deeper technical review
    - Recommend engaging Game Architect for object restructuring
    - Provide proposal as input for architecture revision
    - Flag any 60+ FPS risks or TDD coverage gaps

## Output Deliverables

- **Primary:** "WeChat Mini Game Development Change Proposal" document containing:
  - WeChat Mini Game-specific change analysis
  - Technical impact assessment with object/event context
  - Language strategy implications
  - Performance validation against 60+ FPS target
  - Clearly drafted updates for all affected game artifacts
  - TDD test coverage requirements
  - Implementation guidance

- **Secondary:** Annotated game-change-checklist showing:
  - Technical decisions made
  - Performance trade-offs considered (profiler data)
  - Platform export accommodations
  - WeChat Mini Game-specific implementation notes
  - Required test updates
```
