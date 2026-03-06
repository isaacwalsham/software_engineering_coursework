# Planning – Project Roadmap

## Timeline Overview

The project is structured across two sprints within the CMP-5012B module schedule. The table below maps major milestones and deliverables across all 12 weeks.

| Milestone / Task | W1 | W2 | W3 | W4 | W5 | W6 | W7 | W8 | W9 | W10 | W11 | W12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Requirements Analysis | ● | ● | ● | | | | | | | | | |
| System Design | | ● | ● | ● | | | | | | | | |
| Implementation Plan | | | ● | ● | | | | | | | | |
| **Report Submission** | | | | | ● | | | | | | | |
| Sprint 1 – Core Features | | | | | | ● | ● | ● | | | | |
| **Prototype Demo (W9)** | | | | | | | | | ● | | | |
| Sprint 2 – Extended Features | | | | | | | | | ● | ● | ● | |
| **Final Demo and Submission** | | | | | | | | | | | | ● |

---

## Key Milestones

| Milestone | Week | Date | Description |
|---|---|---|---|
| Requirements and Design Report | Week 6 | 6 March 2026 | Team submission — this document |
| Prototype Demo | Week 9 | approx. 27 March 2026 | Formative feedback session on Sprint 1 features |
| Final Demo and Submission | Week 12 | 15 May 2026 | Full system demonstration and source code submission |

---

## Sprint 1 Goals (Weeks 6–8)

By the end of Sprint 1, the system must demonstrate the following working features:

- [ ] User authentication (login)
- [ ] Module data file import and validation
- [ ] Module and assessment display from imported data
- [ ] Task creation with dependency support
- [ ] Study activity logging (single task)
- [ ] Progress calculation and display
- [ ] Basic timeline chart rendering
- [ ] Basic dashboard showing upcoming deadlines

---

## Sprint 2 Goals (Weeks 9–11)

By the end of Sprint 2, the system must additionally demonstrate:

- [ ] Milestone creation and chart rendering
- [ ] Activity linked to multiple tasks
- [ ] Deadline update feature
- [ ] Circular dependency detection and rejection
- [ ] Full dashboard with completed, upcoming, and missed deadline classification
- [ ] Full regression test suite passing
- [ ] Polished UI and consistent error handling throughout

---

## Project Timeline
```mermaid
gantt
    title Study Planner – Project Timeline
    dateFormat  YYYY-MM-DD
    axisFormat  W%W

    section Documentation
    Requirements Analysis       :done,    req,  2026-01-19, 2026-02-06
    System Design               :done,    des,  2026-01-26, 2026-02-13
    Implementation Plan         :done,    imp,  2026-02-02, 2026-02-20
    Report Submission           :milestone, rep, 2026-03-06, 0d

    section Sprint 1 (Weeks 6-8)
    Domain Classes and Auth     :active,  s1a,  2026-03-09, 2026-03-13
    File Import and Parsing     :         s1b,  2026-03-09, 2026-03-16
    Task Management             :         s1c,  2026-03-09, 2026-03-20
    Activity Logging            :         s1d,  2026-03-16, 2026-03-23
    Progress Calculator         :         s1e,  2026-03-16, 2026-03-23
    Chart Rendering             :         s1f,  2026-03-16, 2026-03-27
    Dashboard Basic             :         s1g,  2026-03-23, 2026-03-27
    Sprint 1 Testing            :         s1t,  2026-03-23, 2026-03-27

    section Prototype Demo
    Week 9 Prototype Demo       :milestone, demo1, 2026-03-27, 0d

    section Sprint 2 (Weeks 9-11)
    Milestones Feature          :         s2a,  2026-03-30, 2026-04-10
    Multi-Task Activities       :         s2b,  2026-03-30, 2026-04-10
    Deadline Updates            :         s2c,  2026-03-30, 2026-04-17
    Dependency Cycle Detection  :         s2d,  2026-04-07, 2026-04-17
    Dashboard Enhancement       :         s2e,  2026-04-07, 2026-04-24
    Full Regression Testing     :         s2t,  2026-04-17, 2026-05-08

    section Final Submission
    Final Demo and Submission   :milestone, final, 2026-05-15, 0d
```

---

## Notes

- Sprint dates are approximate and subject to adjustment based on formative feedback received at the Week 9 prototype demo
- All sprint tasks and owners are detailed in [`sprint-plan.md`](sprint-plan.md)
- The full prioritised task list is in [`backlog.md`](backlog.md)
