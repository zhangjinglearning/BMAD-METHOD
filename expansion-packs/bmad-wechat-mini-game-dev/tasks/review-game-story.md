# review-game-story

Perform a comprehensive WeChat Mini Game story review with quality gate decision, focusing on TDD compliance, 60+ FPS performance validation, and JavaScript language strategy. This adaptive, risk-aware review creates both a story update and a detailed gate file.

## Inputs

```yaml
required:
  - story_id: '{epic}.{story}' # e.g., "1.3"
  - story_path: '{devStoryLocation}/{epic}.{story}.*.md' # Path from core-config.yaml
  - story_title: '{title}' # If missing, derive from story file H1
  - story_slug: '{slug}' # If missing, derive from title (lowercase, hyphenated)
```

## Prerequisites

- Story status must be "Review"
- Developer has completed all tasks and updated the File List
- All tests are passing
- Performance profiler shows 60+ FPS maintained
- TDD cycle (Red-Green-Refactor) was followed

## Review Process - Adaptive Test Architecture

### 1. Risk Assessment (Determines Review Depth)

**Auto-escalate to deep review when:**

- Performance drops below 60 FPS
- No TDD tests written
- Object pooling missing for spawned entities
- Diff > 500 lines
- Previous gate was FAIL/CONCERNS
- Story has > 5 acceptance criteria
- Event connections not properly cleaned up

### 2. Comprehensive Analysis

**A. Requirements Traceability**

- Map each acceptance criteria to tests
- Verify TDD was followed (tests written first)
- Identify coverage gaps (target 80% minimum)
- Verify all objects have corresponding test cases
- Check event emission tests exist

**B. Code Quality Review**

- Object architecture and scene composition
- JavaScript best practices
- Event connection patterns
- Object pooling implementation
- Resource preloading vs lazy loading
- WeChat Mini Game best practices adherence
- Performance profiler validation (60+ FPS)

**C. Test Architecture Assessment**

- Test coverage for JavaScript components
- TDD compliance (Red-Green-Refactor cycle)
- Scene testing with test doubles
- Event testing patterns
- Object mocking appropriateness
- Edge case and error scenario coverage
- Test execution performance impact

**D. Non-Functional Requirements (NFRs)**

- Performance: 60+ FPS maintained, frame time <16.67ms
- Memory: Scene memory usage, object pooling
- Draw Calls: Within platform budgets
- Platform Compatibility: Export template validation
- Input Latency: <50ms for player controls
- Load Times: Scene transitions <3 seconds
- Reliability: Event cleanup, object lifecycle

**E. WeChat Mini Game Testability Evaluation**

- Object Testability: Can objects be tested in isolation?
- Event Observability: Can event emissions be verified?
- Scene Testing: Can scenes be tested without full game?
- Performance Testing: Can FPS be validated in tests?
- Platform Testing: Export templates testable?

**F. Technical Debt Identification**

- Missing TDD tests
- Missing object pools for spawned entities
- Unoptimized object trees
- Event connection leaks
- Performance bottlenecks below 60 FPS

### 3. Active Refactoring

- Implement object pooling for spawned entities
- Run tests to ensure changes don't break
- Profile to verify 60+ FPS maintained
- Document all changes in QA Results section
- Do NOT alter story content beyond QA Results section
- Do NOT change story Status or File List

### 4. Standards Compliance Check

- Verify adherence to WeChat Mini Game coding standards
- Verify TDD approach (tests written first)
- Check object naming conventions
- Validate event naming patterns
- Ensure 60+ FPS performance targets met

### 5. Acceptance Criteria Validation

- Verify each AC is fully implemented
- Check TDD tests exist for each AC
- Validate performance within 60+ FPS
- Verify object pooling where needed
- Check platform export compatibility
- Validate input handling across devices

### 6. Documentation and Comments

- Verify JavaScript documentation comments
- Ensure export variables have tooltips
- Document performance optimizations
- Document event flow and connections

## Output 1: Update Story File - QA Results Section ONLY

**CRITICAL**: You are ONLY authorized to update the "QA Results" section of the story file. DO NOT modify any other sections.

**QA Results Anchor Rule:**

- If `## QA Results` doesn't exist, append it at end of file
- If it exists, append a new dated entry below existing entries
- Never edit other sections

After review and any refactoring, append your results to the story file in the QA Results section:

```markdown
## QA Results

### Review Date: [Date]

### Reviewed By: Pony (WeChat Mini Game Test Architect)

### Code Quality Assessment

[Overall assessment of implementation quality]

### Refactoring Performed

[List any refactoring you performed with explanations]

- **File**: [filename]
  - **Change**: [what was changed]
  - **Why**: [reason for change]
  - **How**: [how it improves the code]

### Compliance Check

- WeChat Mini Game Standards: [✓/✗] [notes if any]
- TDD Compliance: [✓/✗] [test coverage]
- Performance (60+ FPS): [✓/✗] [profiler results]
- Object Pooling: [✓/✗] [for spawned entities]
- All ACs Met: [✓/✗] [notes if any]

### Improvements Checklist

[Check off items you handled yourself, leave unchecked for dev to address]

- [x] Implemented object pool for bullets (js/systems/bullet_pool.js)
- [x] Added missing tests for event emissions
- [ ] Add performance benchmarks to test suite
- [ ] Optimize draw calls in particle system

### Performance Review

- Frame Rate: [Current FPS] (Target: 60+)
- Frame Time: [ms] (Target: <16.67ms)
- Draw Calls: [count] (Budget: [platform specific])
- Memory Usage: [MB] (Limit: [platform specific])
- Object Pools: [Implemented/Missing]

### Files Modified During Review

[If you modified files, list them here - ask Dev to update File List]

### Gate Status

Gate: {STATUS} → docs/qa/gates/{epic}.{story}-{slug}.yml
Risk profile: docs/qa/assessments/{epic}.{story}-risk-{YYYYMMDD}.md
NFR assessment: docs/qa/assessments/{epic}.{story}-nfr-{YYYYMMDD}.md

# Note: Paths should reference core-config.yaml for custom configurations

### Recommended Status

[✓ Ready for Done] / [✗ Changes Required - See unchecked items above]
(Story owner decides final status)
```

## Output 2: Create Quality Gate File

**Template and Directory:**

- Render from `templates/qa-gate-tmpl.yaml`
- Create `docs/qa/gates/` directory if missing (or configure in core-config.yaml)
- Save to: `docs/qa/gates/{epic}.{story}-{slug}.yml`

Gate file structure:

```yaml
schema: 1
story: '{epic}.{story}'
story_title: '{story title}'
gate: PASS|CONCERNS|FAIL|WAIVED
status_reason: '1-2 sentence explanation of gate decision'
reviewer: 'Pony (WeChat Mini Game Test Architect)'
updated: '{ISO-8601 timestamp}'

top_issues: [] # Empty if no issues
waiver: { active: false } # Set active: true only if WAIVED

# Extended fields (optional but recommended):
quality_score: 0-100 # 100 - (20*FAILs) - (10*CONCERNS) or use technical-preferences.md weights
expires: '{ISO-8601 timestamp}' # Typically 2 weeks from review

evidence:
  tests_reviewed: { count }
  risks_identified: { count }
  trace:
    ac_covered: [1, 2, 3] # AC numbers with test coverage
    ac_gaps: [4] # AC numbers lacking TDD coverage
    fps_validation: "60+ FPS on all target platforms"

nfr_validation:
  performance:
    status: PASS|CONCERNS|FAIL
    fps: '60+|<60'
    frame_time: 'ms value'
    notes: 'Profiler findings'
  tdd_compliance:
    status: PASS|CONCERNS|FAIL
    test_coverage: 'percentage'
    notes: 'Test-first validation'
  reliability:
    status: PASS|CONCERNS|FAIL
    notes: 'Event cleanup, object lifecycle'

recommendations:
  immediate: # Must fix before production
    - action: 'Fix FPS drops below 60'
      refs: ['scenes/game.js']
    - action: 'Add object pooling for particles'
      refs: ['js/particle_spawner.js']
  future: # Can be addressed later
    - action: 'Consider a different approach for physics system'
      refs: ['js/physics_manager.js']
```

### Gate Decision Criteria

**Deterministic rule (apply in order):**

If risk_summary exists, apply its thresholds first (≥9 → FAIL, ≥6 → CONCERNS), then NFR statuses, then top_issues severity.

1. **Risk thresholds (if risk_summary present):**
   - If any risk score ≥ 9 → Gate = FAIL (unless waived)
   - Else if any score ≥ 6 → Gate = CONCERNS

2. **Test coverage gaps (if trace available):**
   - If any P0 test from test-design is missing → Gate = CONCERNS
   - If security/data-loss P0 test missing → Gate = FAIL

3. **Issue severity:**
   - If any `top_issues.severity == high` → Gate = FAIL (unless waived)
   - Else if any `severity == medium` → Gate = CONCERNS

4. **NFR statuses:**
   - If any NFR status is FAIL → Gate = FAIL
   - Else if any NFR status is CONCERNS → Gate = CONCERNS
   - Else → Gate = PASS

- WAIVED only when waiver.active: true with reason/approver

Detailed criteria:

- **PASS**: All critical requirements met, no blocking issues
- **CONCERNS**: Non-critical issues found, team should review
- **FAIL**: Critical issues that should be addressed
- **WAIVED**: Issues acknowledged but explicitly waived by team

### Quality Score Calculation

```text
quality_score = 100 - (20 × number of FAILs) - (10 × number of CONCERNS)
Bounded between 0 and 100
```

If `technical-preferences.md` defines custom weights, use those instead.

### Suggested Owner Convention

For each issue in `top_issues`, include a `suggested_owner`:

- `dev`: Code changes needed
- `sm`: Requirements clarification needed
- `po`: Business decision needed

## Key Principles

- You are a WeChat Mini Game Test Architect ensuring 60+ FPS and TDD compliance
- You have authority to add object pooling and optimize performance
- Always validate with the WeChat Mini Game profiler data
- Focus on performance-based prioritization
- Ensure test coverage meets 80% target
- Provide actionable WeChat Mini Game-specific recommendations

## Blocking Conditions

Stop the review and request clarification if:

- Performance drops below 60 FPS
- No TDD tests exist
- Story file is incomplete or missing critical sections
- File List is empty or clearly incomplete
- Object pooling missing for frequently spawned entities
- Critical object architecture issues that require discussion

## Completion

After review:

1. Update the QA Results section in the story file
2. Create the gate file in `docs/qa/gates/`
3. Recommend status: "Ready for Done" or "Changes Required" (owner decides)
4. If files were modified, list them in QA Results and ask Dev to update File List
5. Always provide constructive feedback and actionable recommendations
```
