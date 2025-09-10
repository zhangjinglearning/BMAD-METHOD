<!-- Powered by BMAD™ Core -->

# apply-qa-fixes

Implement fixes based on QA results (gate and assessments) for a specific WeChat Mini Game story. This task is for the Game Developer agent to systematically consume QA outputs and apply game code/test changes while only updating allowed sections in the story file.

## Purpose

- Read QA outputs for a game story (gate YAML + assessment markdowns)
- Create a prioritized, deterministic fix plan for game features
- Apply game code and test changes to close gaps and address issues
- Update only the allowed story sections for the Game Developer agent

## Inputs

```yaml
required:
  - story_id: '{epic}.{story}' # e.g., "2.2"
  - qa_root: from `.bmad-wechat-mini-game-dev/config.yaml` key `qa.qaLocation` (e.g., `docs/project/qa`)
  - story_root: from `.bmad-wechat-mini-game-dev/config.yaml` key `devStoryLocation` (e.g., `docs/project/stories`)
  - project_root: WeChat Mini Game project root directory (containing project.config.json)

optional:
  - story_title: '{title}' # derive from story H1 if missing
  - story_slug: '{slug}' # derive from title (lowercase, hyphenated)
```

## QA Sources to Read

- Gate (YAML): `{qa_root}/gates/{epic}.{story}-*.yml`
  - If multiple, use the most recent by modified time
- Assessments (Markdown):
  - Test Design: `{qa_root}/assessments/{epic}.{story}-test-design-*.md`
  - Traceability: `{qa_root}/assessments/{epic}.{story}-trace-*.md`
  - Risk Profile: `{qa_root}/assessments/{epic}.{story}-risk-*.md`
  - NFR Assessment: `{qa_root}/assessments/{epic}.{story}-nfr-*.md`

## Prerequisites

- WeChat Mini Game developer tools installed and configured
- Testing frameworks installed
- Project builds successfully in the WeChat Mini Game Editor
- Test commands available

## Process (Do not skip steps)

### 0) Load Core Config & Locate Story

- Read `.bmad-wechat-mini-game-dev/config.yaml` and resolve `qa_root`, `story_root`, and `project_root`
- Locate story file in `{story_root}/{epic}.{story}.*.md`
  - HALT if missing and ask for correct story id/path

### 1) Collect QA Findings

- Parse the latest gate YAML:
  - `gate` (PASS|CONCERNS|FAIL|WAIVED)
  - `top_issues[]` with `id`, `severity`, `finding`, `suggested_action`
  - `nfr_validation.*.status` and notes
  - `trace` coverage summary/gaps
  - `test_design.coverage_gaps[]`
  - `risk_summary.recommendations.must_fix[]` (if present)
- Read any present assessment markdowns and extract explicit gaps/recommendations

### 2) Build Deterministic Fix Plan (Priority Order)

Apply in order, highest priority first:

1. High severity items in `top_issues` (gameplay/performance/stability/maintainability)
2. NFR statuses: all FAIL must be fixed → then CONCERNS
3. Test Design `coverage_gaps` (prioritize P0 gameplay scenarios)
4. Trace uncovered requirements (AC-level, especially gameplay mechanics)
5. Risk `must_fix` recommendations
6. Medium severity issues, then low

Guidance:

- Prefer tests closing coverage gaps before/with code changes
- Keep changes minimal and targeted; follow WeChat Mini Game best practices and project architecture
- Respect scene organization and object hierarchy
- Follow JavaScript style guide

### 3) Apply Changes

- Implement game code fixes per plan:
  - JavaScript: Follow style guide, use events for decoupling
- Add missing tests to close coverage gaps:
  - Unit tests in `test/unit/` for game logic
  - Integration tests in `test/integration/` for scene interactions
- Follow WeChat Mini Game patterns:
  - Global manager patterns for global game state
  - Event-based communication between objects
  - JSON files for data management
  - Scene inheritance for reusable components

### 4) Validate

- Run tests
- Check for script errors in the WeChat Mini Game Editor
- Validate scene references and object paths
- Run game in editor to verify no runtime errors
- Test gameplay mechanics manually if needed
- Verify performance (check FPS, memory usage)
- Iterate until all tests pass and no errors

### 5) Update Story (Allowed Sections ONLY)

CRITICAL: Dev agent is ONLY authorized to update these sections of the story file. Do not modify any other sections (e.g., QA Results, Story, Acceptance Criteria, Dev Notes, Testing):

- Tasks / Subtasks Checkboxes (mark any fix subtask you added as done)
- Dev Agent Record →
  - Agent Model Used (if changed)
  - Debug Log References (test results, console output)
  - Completion Notes List (what changed, why, how)
  - File List (all added/modified/deleted files)
- Change Log (new dated entry describing applied fixes)
- Status (see Rule below)

Status Rule:

- If gate was PASS and all identified gaps are closed → set `Status: Ready for Done`
- Otherwise → set `Status: Ready for Review` and notify QA to re-run the review

### 6) Do NOT Edit Gate Files

- Dev does not modify gate YAML. If fixes address issues, request QA to re-run `review-story` to update the gate

## Blocking Conditions

- Missing `.bmad-wechat-mini-game-dev/config.yaml`
- Story file not found for `story_id`
- No QA artifacts found (neither gate nor assessments)
  - HALT and request QA to generate at least a gate file (or proceed only with clear developer-provided fix list)
- WeChat Mini Game project file (`project.config.json`) not found
- Testing framework not properly installed

## Completion Checklist

- WeChat Mini Game project builds without errors
- All tests pass
- No script errors in the WeChat Mini Game Editor
- All high severity `top_issues` addressed
- NFR FAIL → resolved; CONCERNS minimized or documented
- Coverage gaps closed or explicitly documented with rationale
- Gameplay features tested and working
- Story updated (allowed sections only) including File List and Change Log
- Status set according to Status Rule

## Example: Story 2.2 - Player Movement System

Given gate `docs/project/qa/gates/2.2-*.yml` shows

- `coverage_gaps`: Jump mechanics edge cases untested (AC2)
- `coverage_gaps`: Input buffering not tested (AC4)
- `top_issues`: Performance drops when multiple players active

Fix plan:

- Add test for jump height variation based on button hold time
- Add test for input buffering during state transitions
- Optimize player movement script using object pooling for effects
- Test with parameterized tests for different player counts
- Re-run tests and update Dev Agent Record + File List accordingly

## Key Principles

- Deterministic, risk-first prioritization
- Minimal, maintainable changes following WeChat Mini Game best practices
- Tests validate gameplay behavior and close gaps
- Respect WeChat Mini Game's object-based architecture and event system
- Maintain clear separation between game logic and presentation
- Strict adherence to allowed story update areas
- Gate ownership remains with QA; Game Developer signals readiness via Status
```
