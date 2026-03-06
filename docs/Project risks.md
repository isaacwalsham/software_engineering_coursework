# Project Risks

The following risk register identifies key threats to the successful delivery of the Study Planner across both sprints. Each risk is assessed by likelihood and impact, with a defined mitigation strategy.

---

## Risk Register

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R1 | Team member unavailable during a sprint | Medium | High | All tasks are documented in the backlog with clear descriptions. Responsibilities are shared where possible so no single feature is a single point of failure. |
| R2 | Scope creep — too many features attempted in Sprint 1 | Medium | Medium | Sprint backlog is fixed at the start of each sprint. Team Leader reviews scope weekly and defers non-essential features to Sprint 2. |
| R3 | Integration conflicts between parallel development branches | High | Medium | Feature branches used for all development. Pull requests required before merging to main. Mid-sprint integration checkpoint held to catch conflicts early. |
| R4 | Gantt chart library incompatible or too complex to implement | Low | High | Plotting library evaluated during Week 5 before Sprint 1 begins. Fallback option identified in advance (e.g. custom SVG rendering). |
| R5 | Ambiguity in the hub data file format | Medium | Medium | Data file format defined and documented in `/design/architecture.md` before development begins. FileParser unit tested against the agreed format. |
| R6 | Data not persisting correctly across sessions | Low | High | Persistence layer implemented and tested early in Sprint 1 (Task 4). Daniel Roath responsible for persistence and integration testing. |
| R7 | Circular dependency detection producing incorrect results | Low | Medium | DependencyChecker implemented as an isolated service class. Unit tested independently using known graph cycle-detection test cases before integration. |
| R8 | Insufficient test coverage before the Week 9 prototype demo | Medium | High | Test cases defined upfront in `TestCase.md`. Testing is a shared team responsibility, with Daniel Roath as the primary QA owner for core flows. |
| R9 | Progress calculation logic producing incorrect percentages | Low | Medium | ProgressCalculator implemented as a stateless service. Unit tested in isolation using boundary values (0%, 50%, 100%, >100%). |
| R10 | Final demo features not complete by Week 12 | Low | High | Sprint 2 backlog prioritised so that high-value features (dashboard, milestone Gantt rendering) are completed before lower-priority stretch goals. |

---

## Risk Severity Matrix

|  | **Low Impact** | **Medium Impact** | **High Impact** |
|---|---|---|---|
| **High Likelihood** | | R3 | |
| **Medium Likelihood** | | R2, R5 | R1, R8 |
| **Low Likelihood** | | R7, R9 | R4, R6, R10 |

---

## Mitigation Approach

Risks are reviewed at the start of each sprint. If a risk materialises, the Team Leader (Philip Lush) is responsible for escalating to the module teaching team and adjusting the sprint backlog accordingly. All team members are expected to flag emerging risks as early as possible rather than waiting for the next sprint review.
