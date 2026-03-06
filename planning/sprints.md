# Planning – Sprint Plan

The project follows an adapted Scrum approach across two sprints within the CMP-5012B module schedule.

---

## Sprint Overview

| Sprint | Weeks | Focus | Key Milestone |
|---|---|---|---|
| Sprint 1 | Weeks 6–8 | Core features: import, task creation, activity logging, progress calculation, basic Gantt chart and dashboard | Prototype demo – Week 9 |
| Sprint 2 | Weeks 9–11 | Extended features: milestones, multi-task activities, deadline updates, dependency detection, full testing | Final demo – Week 12 |

---

## Team Member Roles

| Member | Role | Primary Responsibility |
|---|---|---|
| Philip Lush | Team Leader | Sprint coordination, architectural consistency, authentication, dashboard |
| Tate Jeffries | Developer | Task management, file upload, UI rendering |
| Isaac Walsham | Developer | Activity logging, milestone management, multi-task linking |
| Ashwin Anand | Developer | Progress calculation, Gantt chart implementation |
| Daniel Roath | Developer / QA | Persistence, testing, deadline management, dependency cycle detection |

---

## Sprint 1 – Task Allocation (Weeks 6–8)

| # | Task | Description | Owner | Priority | User Story |
|---|---|---|---|---|---|
| 1 | Login UI | Create username and password input fields, submit button, connect to authentication controller | Philip Lush | High | System Req |
| 2 | Credential Validation | Compare inputs with stored login data, compare password hashes, return true or false | Philip Lush | High | System Req |
| 3 | Auth Error Handling | Display error message on failed authentication; prevent login | Philip Lush | High | System Req |
| 4 | Domain Classes | Create domain classes: Module, Assessment, Task, StudyActivity, SemesterProfile with getters/setters | Philip Lush | High | System Req |
| 5 | File Upload Restrictions | Restrict file type on upload; return upload status; accept `.csv` and `.json` | Tate Jeffries | Medium | System Req |
| 6 | File Parser Integration | Validate file structure; extract module, assessment, and deadline data | Tate Jeffries | Medium | System Req |
| 7 | Assign Objects to SemesterProfile | Create Module and Task domain objects and assign them to the SemesterProfile | Tate Jeffries | Medium | System Req |
| 8 | Render Imported Data | Display imported module and assessment data in the UI | Tate Jeffries | High | System Req |
| 9 | File Validation Error Handling | Display error if the user uploads an empty or unsupported file | Tate Jeffries | High | US-01 |
| 10 | Study Session Duration Field | Allow the user to select a task, enter a duration, and save as a study session | Isaac Walsham | Medium | US-02 |
| 11 | Study Session Validation | Reject negative, zero, or non-numeric duration values; display error; prevent submission | Isaac Walsham | Medium | US-02 |
| 12 | Associate Activity with Task | Store cumulative hours of study sessions; link activity to task | Isaac Walsham | Low | US-02 |
| 13 | Task Progress Calculator | Calculate `(Hours Completed / Required Hours) × 100`; display in task UI | Ashwin Anand | Low | US-02 |
| 14 | Approaching/Overdue Reminder | Compare deadlines to system date; colour-code task UI based on imminence | Daniel Roath | Medium | All Users |
| 15 | Gantt Chart Implementation | Using a plotting library, render a timeline with date axis, semester line, and task bars | Ashwin Anand | High | US-03 |
| 16 | Task Progress in Gantt | Represent start date, deadline, and completion status within task bars | Ashwin Anand | Low | US-03 |
| 17 | Subtask / Parent Task Linking | Update parent task progress when subtasks are completed | Tate Jeffries | Medium | US-04 |
| 24 | Unit and Integration Tests (Sprint 1) | Implement test cases for core flows: import → task creation → activity logging → progress | Daniel Roath | High | All |

---

## Sprint 2 – Task Allocation (Weeks 9–11)

| # | Task | Description | Owner | Priority | User Story |
|---|---|---|---|---|---|
| 18 | Milestone Creation UI | Allow the user to create milestones with a name, deadline, and linked tasks | Isaac Walsham | Medium | US-06 |
| 19 | Milestone Gantt Rendering | Display milestones as diamond markers at their deadline position on the chart | Ashwin Anand | Medium | US-06 |
| 20 | Multi-Task Activity Linking | Allow a single activity to be linked to multiple tasks; update all task progress | Isaac Walsham | Medium | US-07 |
| 21 | Deadline Update Feature | Allow the user to edit deadlines; recalculate dashboard status and re-render chart | Daniel Roath | Medium | US-08 |
| 22 | Dashboard Deadline Classification | Classify deadlines as completed, upcoming, or missed; render progress bars | Philip Lush | High | US-05 |
| 23 | Circular Dependency Detection | Detect and reject circular task dependency chains | Daniel Roath | Medium | US-04 |
| 24 | Unit and Integration Tests (Sprint 2) | Full regression testing of Sprint 2 features and Sprint 1 core flows | Daniel Roath | High | All |

---

## Collaboration and Shared Responsibility

Although responsibilities are divided for efficiency, both sprints are delivered collectively:

- All members participate in design validation sessions
- Code reviews are conducted before integration into main
- Integration checkpoints occur mid-sprint to reduce last-minute conflicts
- Testing is treated as a shared team responsibility — not isolated to one individual
- All members must be present and contribute during the Week 12 final demonstration

This structure reflects agile principles and supports effective parallel development within a five-member team.
