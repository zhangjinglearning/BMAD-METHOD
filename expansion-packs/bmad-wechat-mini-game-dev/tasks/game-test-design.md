<!-- Powered by BMAD™ Core -->

# game-test-design

Create comprehensive WeChat Mini Game test scenarios with appropriate test level recommendations for game feature implementation.

## Inputs

```yaml
required:
  - story_id: '{epic}.{story}' # e.g., "1.3"
  - story_path: '{devStoryLocation}/{epic}.{story}.*.md' # Path from core-config.yaml
  - story_title: '{title}' # If missing, derive from story file H1
  - story_slug: '{slug}' # If missing, derive from title (lowercase, hyphenated)
```

## Purpose

Design a complete WeChat Mini Game test strategy that identifies what to test, at which level (unit/integration/playtesting). This ensures efficient test coverage for game mechanics, systems, and player experience while maintaining appropriate test boundaries.

## Dependencies

```yaml
data:
  - game-test-levels-framework.md # Unit/Integration/Playtesting decision criteria
  - game-test-priorities-matrix.md # P0/P1/P2/P3 classification for game features
```

## Process

### 1. Analyze Story Requirements

Break down each acceptance criterion into testable game scenarios. For each AC:

- Identify the core game mechanic or system to test
- Determine input variations (controls, player actions)
- Consider edge cases (collision boundaries, resource limits)
- Note platform-specific behaviors
- Identify performance requirements (FPS, memory)

### 2. Apply Game Test Level Framework

**Reference:** Load `game-test-levels-framework.md` for detailed criteria

Quick rules for WeChat Mini Game:

- **Unit Tests**: Game logic, damage calculations, inventory systems, state machines
- **Integration Tests**: Scene interactions, event connections, save/load, physics
- **Playtesting**: Full gameplay loops, difficulty balance, fun factor, performance on target hardware

### 3. Assign Priorities

**Reference:** Load `test-priorities-matrix.md` for classification

Quick priority assignment for games:

- **P0**: Game-breaking bugs, save corruption, core mechanics, progression blockers
- **P1**: Combat systems, player movement, UI responsiveness, multiplayer sync
- **P2**: Visual effects, audio, achievements, secondary mechanics
- **P3**: Cosmetics, easter eggs, optional content

### 4. Design Test Scenarios

For each identified test need, create:

```yaml
test_scenario:
  id: '{epic}.{story}-{LEVEL}-{SEQ}'
  requirement: 'AC reference'
  priority: P0|P1|P2|P3
  level: unit|integration|playtest
  framework: Manual
  description: 'What game feature/mechanic is being tested'
  justification: 'Why this level and framework were chosen'
  test_scene: 'res://tests/{TestSceneName}.tscn' # For automated tests
  mitigates_risks: ['PERF-001', 'GAME-002'] # From risk profile
```

### 5. Validate Coverage

Ensure:

- Every AC has at least one test
- No duplicate coverage across levels
- Critical paths have multiple levels
- Risk mitigations are addressed

## Outputs

### Output 1: Test Design Document

**Save to:** `qa.qaLocation/assessments/{epic}.{story}-test-design-{YYYYMMDD}.md`

```markdown
# Test Design: Story {epic}.{story}

Date: {date}
Designer: Quinn (Game Test Architect)

## Game Test Strategy Overview

- Total test scenarios: X
- Unit tests: Y (A%)
- Integration tests: Z (B%)
- Playtesting scenarios: W (C%)
- Priority distribution: P0: X, P1: Y, P2: Z

## Test Scenarios by Acceptance Criteria

### AC1: {description}

#### Scenarios

| ID           | Level       | Framework | Priority | Test                          | Justification                |
| ------------ | ----------- | --------- | -------- | ----------------------------- | ---------------------------- |
| 1.3-UNIT-001 | Unit        | Manual    | P0       | Player damage calculation     | Core combat logic            |
| 1.3-INT-001  | Integration | Manual    | P0       | Enemy AI pathfinding          | Navigation behavior   |
| 1.3-PLAY-001 | Playtest    | Manual    | P1       | Boss fight difficulty balance | Player experience validation |

[Continue for all ACs...]

## Risk Coverage

[Map test scenarios to identified risks if risk profile exists]

## Recommended Execution Order

1. P0 Unit tests (fail fast)
2. P0 Integration tests
3. P0 E2E tests
4. P1 tests in order
5. P2+ as time permits
```

### Output 2: Gate YAML Block

Generate for inclusion in quality gate:

```yaml
test_design:
  scenarios_total: X
  by_level:
    unit: Y
    integration: Z
    playtest: W
  by_priority:
    p0: A
    p1: B
    p2: C
  coverage_gaps: [] # List any ACs without tests
  performance_tests: [] # FPS, memory, load time tests
```

### Output 3: Trace References

Print for use by trace-requirements task:

```text
Test design matrix: qa.qaLocation/assessments/{epic}.{story}-test-design-{YYYYMMDD}.md
P0 tests identified: {count}
```

## Game Testing Quality Checklist

Before finalizing, verify:

- [ ] Every AC has test coverage
- [ ] Physics and collision tests use proper test scenes
- [ ] Performance tests target minimum spec hardware
- [ ] Multiplayer tests cover desync scenarios
- [ ] Save/load tests verify data integrity
- [ ] Platform-specific tests for each export target
- [ ] Test scenes are properly organized in tests/

## Key Game Testing Principles

- **Shift left**: Test game logic early with unit tests before full integration
- **Performance first**: Profile early and often, test on min spec
- **Player experience**: Balance automated tests with human playtesting
- **Scene isolation**: Test components in minimal scenes to reduce dependencies
- **Fast feedback**: Unit tests in CI/CD, integration tests nightly, playtests per sprint
- **Platform coverage**: Test exports on all target platforms regularly
```
