# Game Development Change Navigation Checklist (WeChat Mini Game)

**Purpose:** To systematically guide the Game SM agent and user through analysis and planning when a significant change (performance issue, platform constraint, technical blocker, gameplay feedback) is identified during WeChat Mini Game development.

**Instructions:** Review each item with the user. Mark `[x]` for completed/confirmed, `[N/A]` if not applicable, or add notes for discussion points.

[[LLM: INITIALIZATION INSTRUCTIONS - GAME CHANGE NAVIGATION

Changes during game development are common - performance issues, platform constraints, gameplay feedback, and technical limitations are part of the process.

Before proceeding, understand:

1. This checklist is for SIGNIFICANT changes affecting game architecture or features
2. Minor tweaks (shader adjustments, UI positioning) don't require this process
3. The goal is to maintain playability while adapting to technical realities
4. Performance (60+ FPS) and player experience are paramount
5. Consider JavaScript implementation options

Required context:

- The triggering issue (performance metrics, crash logs, feedback)
- Current development state (implemented features, current sprint)
- Access to GDD, technical specs, and performance budgets
- Understanding of remaining features and milestones
- Current language usage (JavaScript) per system

APPROACH:
This is an interactive process. Discuss performance implications, platform constraints, and player impact. The user makes final decisions, but provide expert WeChat Mini Game dev guidance.

REMEMBER: Game development is iterative. Changes often lead to better gameplay and performance.]]

---

## 1. Understand the Trigger & Context

[[LLM: Start by understanding the game-specific issue. Ask technical questions:

- What performance metrics triggered this? (FPS, frame time, memory)
- Is this platform-specific or universal?
- Can we reproduce it consistently?
- What WeChat Mini Game profiler data do we have?
- Are we hitting WeChat Mini Game engine limits?

Focus on measurable impacts and technical specifics.]]

- [ ] **Identify Triggering Element:** Clearly identify the game feature/system revealing the issue.
- [ ] **Define the Issue:** Articulate the core problem precisely.
  - [ ] Performance bottleneck (CPU/GPU/Memory)?
  - [ ] Draw call or batching issue?
  - [ ] Platform-specific limitation?
  - [ ] WeChat Mini Game engine constraint?
  - [ ] Object tree complexity issue?
  - [ ] Event overhead problem?
  - [ ] Physics engine bottleneck?
  - [ ] Gameplay/balance issue from playtesting?
  - [ ] Asset import or resource loading problem?
  - [ ] Export template or platform issue?
- [ ] **Assess Performance Impact:** Document specific metrics (current FPS, target 60+ FPS, frame time ms, draw calls, memory usage).
- [ ] **Gather Technical Evidence:** Note WeChat Mini Game profiler data, performance monitor stats, platform test results, player feedback.

## 2. Game Feature Impact Assessment

[[LLM: Game features are interconnected in the object system. Evaluate systematically:

1. Can we optimize the current feature without changing gameplay?
2. Do dependent scenes/objects need adjustment?
3. Are there WeChat Mini Game-specific optimizations available?
4. Does this affect our performance budget allocation?

Consider both technical and gameplay impacts.]]

- [ ] **Analyze Current Sprint Features:**
  - [ ] Can the current feature be optimized?
    - [ ] Object pooling for frequently instantiated objects?
    - [ ] LOD system implementation?
    - [ ] Draw call batching improvements?
  - [ ] Does it need gameplay simplification?
  - [ ] Should it be platform-specific (high-end only)?
- [ ] **Analyze Dependent Systems:**
  - [ ] Review all scenes and objects interacting with the affected feature.
  - [ ] Do physics bodies need optimization?
  - [ ] Are UI systems impacted?
  - [ ] Do storage save/load systems require changes?
  - [ ] Are multiplayer events affected?
  - [ ] Do event connections need optimization?
- [ ] **Summarize Feature Impact:** Document effects on object hierarchy, scene structure, and technical architecture.

## 3. Game Artifact Conflict & Impact Analysis

[[LLM: Game documentation drives development. Check each artifact:

1. Does this invalidate GDD mechanics?
2. Are technical architecture assumptions still valid?
3. Do performance budgets need reallocation?
4. Are platform requirements still achievable?

Missing conflicts cause performance issues later.]]

- [ ] **Review GDD:**
  - [ ] Does the issue conflict with core gameplay mechanics?
  - [ ] Do game features need scaling for performance?
  - [ ] Are progression systems affected?
  - [ ] Do balance parameters need adjustment?
- [ ] **Review Technical Architecture:**
  - [ ] Does the issue conflict with WeChat Mini Game architecture (scene structure, object hierarchy)?
  - [ ] Are global manager systems impacted?
  - [ ] Do shader/rendering approaches need revision?
  - [ ] Are resource structures optimal for the scale?
- [ ] **Review Performance Specifications:**
  - [ ] Are target framerates (60+ FPS) still achievable?
  - [ ] Do memory budgets need reallocation?
  - [ ] Are load time targets realistic?
  - [ ] Do we need platform-specific targets?
  - [ ] Are draw call budgets exceeded?
- [ ] **Review Asset Specifications:**
  - [ ] Do texture import settings need adjustment?
  - [ ] Are mesh instance counts appropriate?
  - [ ] Do audio bus configurations need changes?
  - [ ] Is the animation tree complexity sustainable?
  - [ ] Are particle system limits appropriate?
- [ ] **Summarize Artifact Impact:** List all game documents requiring updates.

## 4. Path Forward Evaluation

[[LLM: Present WeChat Mini Game-specific solutions with technical trade-offs:

1. What's the performance gain (FPS improvement)?
2. How much rework is required?
3. What's the player experience impact?
4. Are there platform-specific solutions?
5. Can we leverage new WeChat Mini Game features?

Be specific about WeChat Mini Game implementation details.]]

- [ ] **Option 1: Optimization Within Current Design:**
  - [ ] Can performance be improved through WeChat Mini Game optimizations?
    - [ ] Object pooling with object reuse?
    - [ ] MultiMesh for instancing?
    - [ ] Viewport optimization?
    - [ ] Occlusion culling setup?
    - [ ] Batch draw calls?
    - [ ] Optimize event connections?
    - [ ] Reduce object tree depth?
  - [ ] Define specific optimization techniques.
  - [ ] Estimate performance improvement potential.
- [ ] **Option 2: Feature Scaling/Simplification:**
  - [ ] Can the feature be simplified while maintaining fun?
  - [ ] Identify specific elements to scale down.
  - [ ] Define platform-specific variations.
  - [ ] Assess player experience impact.
- [ ] **Option 3: Architecture Refactor:**
  - [ ] Would restructuring improve performance significantly?
  - [ ] Identify WeChat Mini Game-specific refactoring needs:
    - [ ] Scene composition changes?
    - [ ] Object hierarchy optimization?
    - [ ] Event system redesign?
    - [ ] Global manager restructuring?
    - [ ] Resource management improvements?
  - [ ] Estimate development effort.
- [ ] **Option 4: Scope Adjustment:**
  - [ ] Can we defer features to post-launch?
  - [ ] Should certain features be platform-exclusive?
  - [ ] Do we need to adjust milestone deliverables?
- [ ] **Select Recommended Path:** Choose based on performance gain vs. effort.

## 5. Game Development Change Proposal Components

[[LLM: The proposal must include technical specifics:

1. Performance metrics (before/after projections with FPS targets)
2. WeChat Mini Game implementation details (objects, scenes, scripts)
3. Platform-specific considerations
4. Testing requirements
5. Risk mitigation strategies

Make it actionable for game developers.]]

(Ensure all points from previous sections are captured)

- [ ] **Technical Issue Summary:** Performance/technical problem with metrics.
- [ ] **Feature Impact Summary:** Affected objects, scenes, and systems.
- [ ] **Performance Projections:** Expected improvements from chosen solution (target 60+ FPS).
- [ ] **Implementation Plan:** WeChat Mini Game-specific technical approach.
  - [ ] Object hierarchy changes
  - [ ] Scene restructuring needs
  - [ ] Resource optimization
  - [ ] Event flow improvements
- [ ] **Platform Considerations:** Any platform-specific implementations.
- [ ] **Testing Strategy:**
  - [ ] Unit tests for JavaScript changes
  - [ ] Performance benchmarks
  - [ ] Platform validation approach
- [ ] **Risk Assessment:** Technical risks and mitigation plans.
- [ ] **Updated Game Stories:** Revised stories with technical constraints.

## 6. Final Review & Handoff

[[LLM: Game changes require technical validation. Before concluding:

1. Are performance targets (60+ FPS) clearly defined?
2. Is the WeChat Mini Game implementation approach clear?
3. Do we have rollback strategies?
4. Are test scenarios defined?
5. Is platform testing covered?

Get explicit approval on technical approach.

FINAL REPORT:
Provide a technical summary:

- Performance issue and root cause
- Chosen solution with expected FPS gains
- Implementation approach in WeChat Mini Game (objects, scenes, language)
- Testing and validation plan
- Timeline and milestone impacts

Keep it technically precise and actionable.]]

- [ ] **Review Checklist:** Confirm all technical aspects discussed.
- [ ] **Review Change Proposal:** Ensure WeChat Mini Game implementation details are clear.
- [ ] **Performance Validation:** Define how we'll measure success (profiler metrics).
- [ ] **Test Coverage:** Ensure test coverage planned.
- [ ] **User Approval:** Obtain approval for technical approach.
- [ ] **Developer Handoff:** Ensure game-dev agent has all technical details needed.

---
```
