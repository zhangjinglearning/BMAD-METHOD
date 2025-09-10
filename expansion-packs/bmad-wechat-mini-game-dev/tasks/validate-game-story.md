# Validate Game Story Task

## Purpose

To comprehensively validate a WeChat Mini Game development story draft before implementation begins, ensuring it contains all necessary WeChat Mini Game-specific technical context (object architecture, JavaScript language strategy, 60+ FPS performance targets), TDD requirements, and implementation details. This specialized validation prevents hallucinations, ensures WeChat Mini Game development readiness, and validates game-specific acceptance criteria and testing approaches.

## SEQUENTIAL Task Execution (Do not proceed until current Task is complete)

### 0. Load Core Configuration and Inputs

- Load `.bmad-wechat-mini-game-dev/config.yaml` from the project root
- If the file does not exist, HALT and inform the user: "core-config.yaml not found. This file is required for story validation."
- Extract key configurations: `devStoryLocation`, `gdd.*`, `gamearchitecture.*`, `workflow.*`
- Identify and load the following inputs:
  - **Story file**: The drafted game story to validate (provided by user or discovered in `devStoryLocation`)
  - **Parent epic**: The epic containing this story's requirements from GDD
  - **Architecture documents**: Based on configuration (sharded or monolithic)
  - **Game story template**: `expansion-packs/bmad-wechat-mini-game-dev/templates/game-story-tmpl.yaml` for completeness validation

### 1. Game Story Template Completeness Validation

- Load `expansion-packs/bmad-wechat-mini-game-dev/templates/game-story-tmpl.yaml` and extract all required sections
- **Missing sections check**: Compare story sections against game story template sections to verify all WeChat Mini Game-specific sections are present:
  - WeChat Mini Game Technical Context
  - Object Architecture & Event Flow
  - Scene & Resource Requirements
  - Language Strategy (JavaScript)
  - Performance Requirements (60+ FPS target)
  - Platform Export Settings
  - Integration Points
  - TDD Testing Strategy
- **Placeholder validation**: Ensure no template placeholders remain unfilled (e.g., `{{EpicNum}}`, `{{StoryNum}}`, `{{GameMechanic}}`, `_TBD_`)
- **Game-specific sections**: Verify presence of WeChat Mini Game development specific sections
- **Structure compliance**: Verify story follows game story template structure and formatting

### 2. WeChat Mini Game Project Structure and Resource Validation

- **WeChat Mini Game file paths clarity**: Are WeChat Mini Game-specific paths clearly specified?
- **Plugin dependencies**: Are required plugins or libraries identified and documented?
- **Scene structure relevance**: Is relevant object hierarchy and scene tree structure included?
- **Scene organization**: Are scene instancing and inheritance patterns clearly specified?
- **Resource pipeline**: Are texture imports, Animation resources, and Audio assets properly planned?
- **Directory structure**: Do new WeChat Mini Game resources follow project structure according to architecture docs?
- **Custom Resource requirements**: Are resource classes and export presets identified?
- **Language compliance**: Are JavaScript best practices enforced?

### 3. WeChat Mini Game Object Architecture Validation

- **Object class specifications**: Are custom object classes sufficiently detailed?
- **Object dependencies**: Are object relationships and event connections clearly mapped?
- **WeChat Mini Game lifecycle usage**: Are lifecycle methods appropriately planned?
- **Event system integration**: Are event emissions, connections, and custom events specified?
- **UI requirements**: Are UI elements, anchoring, and theme system requirements defined?
- **Performance considerations**: Are process modes optimized?

### 4. Game Mechanics and Systems Validation

- **Core loop integration**: Does the story properly integrate with established game core loop?
- **Player input handling**: Are input handling requirements specified?
- **Game state management**: Are state transitions and save/load system requirements clear?
- **UI/UX integration**: Are UI elements, anchoring, and theme system requirements defined?
- **Audio integration**: Are audio nodes, bus routing, and sound pooling specified?
- **Animation systems**: Are animation and transition requirements clear?
- **Physics integration**: Are physics bodies, collision layers, and physics settings specified?
- **Object pooling**: Are pooling strategies defined for frequently spawned entities?

### 5. WeChat Mini Game-Specific Acceptance Criteria Assessment

- **TDD testing**: Are tests defined for all criteria?
- **Visual validation**: Are visual/aesthetic acceptance criteria measurable and testable?
- **Performance criteria**: Is 60+ FPS target specified with frame time <16.67ms?
- **Platform compatibility**: Are export template requirements for different platforms addressed?
- **Input validation**: Are input actions for touch covered?
- **Audio criteria**: Are audio bus levels, stream players, and audio pooling specified?
- **Animation validation**: Are animation smoothness, timing, and blend requirements defined?

### 6. WeChat Mini Game Testing and Validation Instructions Review

- **TDD Framework**: Are TDD approaches with Red-Green-Refactor cycle specified?
- **Performance profiling**: Are WeChat Mini Game Profiler usage and 60+ FPS validation steps defined?
- **Export testing**: Are export template validation steps for target platforms specified?
- **Scene testing**: Are scene instancing, transitions, and event flow testing approaches clear?
- **Resource validation**: Are texture compression, import settings, and pooling tests defined?
- **Platform testing**: Are platform-specific export settings and input methods specified?
- **Memory leak testing**: Are event cleanup and object lifecycle validation steps included?

### 7. WeChat Mini Game Performance and Optimization Validation

- **Frame rate targets**: Is 60+ FPS minimum clearly specified for all platforms?
- **Memory budgets**: Are scene memory, resource memory, and pooling limits defined?
- **Draw call optimization**: Are rendering batches and viewport optimization approaches specified?
- **Mobile performance**: Are mobile export settings and touch optimization addressed?
- **Resource optimization**: Are import settings, compression, and preloading strategies clear?
- **Language optimization**: Are JavaScript best practices specified?
- **Loading time targets**: Are scene transitions <3 seconds and resource streaming defined?

### 8. WeChat Mini Game Platform and Export Considerations

- **Export templates**: Are platform-specific export templates and settings documented?
- **Platform features**: Are platform-specific WeChat Mini Game features properly configured?
- **Data persistence**: Are storage usage and save system requirements specified?
- **Input handling**: Are input configurations for each platform defined?
- **Performance targets**: Are platform-specific 60+ FPS optimizations addressed?
- **Export security**: Are release vs debug export settings properly configured?

### 9. WeChat Mini Game Development Task Sequence Validation

- **TDD workflow order**: Do tasks follow TDD cycle (write tests first, then implement, then refactor)?
- **Object hierarchy dependencies**: Are parent objects created before child objects?
- **Resource dependencies**: Are resources created before scenes that use them?
- **Event connections**: Are event emitters created before receivers?
- **Testing integration**: Are test creation tasks before implementation?
- **Export integration**: Are export preset configurations properly sequenced?
- **Performance validation**: Are profiling checkpoints placed throughout development?

### 10. WeChat Mini Game Anti-Hallucination Verification

- **WeChat Mini Game API accuracy**: Every WeChat Mini Game API reference must be verified against current WeChat Mini Game documentation
- **Plugin verification**: All plugin references must be valid
- **Object architecture alignment**: Object relationships must match architecture specifications
- **Performance claims verification**: 60+ FPS targets must be realistic for target platforms
- **Resource pipeline accuracy**: All import settings and resource configurations must be valid

### 11. WeChat Mini Game Development Agent Implementation Readiness

- **WeChat Mini Game context completeness**: Can the story be implemented without consulting external WeChat Mini Game documentation?
- **Language specification clarity**: Are JavaScript choices and patterns unambiguous?
- **Resource requirements clarity**: Are all resources, scenes, and import settings defined?
- **Object relationship clarity**: Are all object interactions and event flows explicitly defined?
- **TDD approach completeness**: Are TDD approaches fully specified?
- **Performance validation readiness**: Are 60+ FPS validation approaches clearly defined?

### 12. Generate WeChat Mini Game Story Validation Report

Provide a structured validation report including:

#### Game Story Template Compliance Issues

- Missing WeChat Mini Game-specific sections from game story template
- Unfilled placeholders or template variables specific to game development
- Missing object specifications or resource requirements
- Missing TDD test specifications
- Language strategy gaps

#### Critical WeChat Mini Game Issues (Must Fix - Story Blocked)

- Missing essential WeChat Mini Game technical information for implementation
- No TDD test specifications
- Performance targets not meeting 60+ FPS requirement
- Incomplete object architecture or event flow
- Missing object pooling for spawned entities

#### WeChat Mini Game-Specific Should-Fix Issues (Important Quality Improvements)

- Unclear object hierarchy or event connection patterns
- Incomplete resource pipeline or import settings
- Task sequencing not following TDD cycle
- Missing platform export template specifications
- Inadequate performance profiling checkpoints

#### Game Development Nice-to-Have Improvements (Optional Enhancements)

- Additional WeChat Mini Game performance optimization context
- Enhanced resource creation guidance and best practices
- Clarifications for WeChat Mini Game-specific patterns (events, groups)
- Additional platform export considerations
- Enhanced profiler usage guidance

#### WeChat Mini Game Anti-Hallucination Findings

- Unverifiable WeChat Mini Game API claims or outdated references
- Inconsistencies with WeChat Mini Game project architecture documents
- Invented objects, events, or development patterns
- Performance claims not achieving 60+ FPS

#### WeChat Mini Game Platform and Performance Validation

- **Performance Assessment**: 60+ FPS validation, frame time <16.67ms
- **Platform Compatibility Check**: Export templates, Input, platform features
- **Resource Pipeline Validation**: Import settings, compression, pooling strategies
- **WeChat Mini Game Version Compliance**: Compatibility with latest version
- **Language Performance**: JavaScript best practices enforcement

#### Final WeChat Mini Game Development Assessment

- **GO**: Story ready for WeChat Mini Game implementation with TDD and 60+ FPS targets
- **NO-GO**: Story requires WeChat Mini Game-specific fixes before implementation
- **TDD Readiness Score**: 1-10 scale based on test coverage planning
- **Performance Readiness**: Can maintain 60+ FPS? Yes/No/Unknown
- **Platform Export Readiness**: Assessment of export template preparedness

#### Recommended Next Steps

Based on validation results, provide specific recommendations for:

- WeChat Mini Game technical documentation improvements needed
- TDD test specifications to add
- Performance profiling setup for 60+ FPS validation
- Platform export template configuration needs
- Object pooling implementation requirements
```
