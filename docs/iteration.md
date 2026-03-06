# Iteration Review

## Review of Selected User Stories

We selected three user stories as the core of the system for Sprint 1:

| User Story | Summary | Why Core |
|---|---|---|
| **US-01** – Import Data | Load module and deadline data from a UEA data file | Without this, there is no planning data in the system |
| **US-02** – Log Progress | Log time or tasks completed against a specific module | This is the primary action students use to track their work |
| **US-05** – Dashboard | Display module status and percentage completion | This is the essential feedback loop that makes the system useful |

### Minimum Viable Scope Per Story

**US-01 – Import Data**
- Must work: read UEA data file correctly; save deadlines without losing any dates
- Can wait: drag and drop UI, multiple file format support, automated error correction

**US-02 – Log Progress**
- Must work: log time or tasks completed against a module; save actual progress to compare against deadlines
- Can wait: stopwatch timer, photo and note attachments, edit and delete log entries

**US-05 – Dashboard**
- Must work: calculate percentage complete from logged data; show module name and status (On Track / Behind Schedule)
- Can wait: interactive Gantt chart, theming and colour customisation, progress sharing

---

## Issues Identified During Review

After reviewing our diagrams and wireframes, the following inconsistencies and gaps were found. These need to be resolved to ensure our interaction artefacts stay consistent across user stories, UX design, architecture, and interaction models, and to avoid design drift as artefacts evolve.

---

### Issue 1 – One Sequence Diagram Models the Wrong User Story

We selected US-01, US-02, and US-05 as our three core stories, but one of the current sequence diagrams models **US-03** instead. This creates a direct mismatch between our prioritised requirements and our interaction modelling.

Each sequence diagram should be linked to one of the core user stories. We should have interaction models for two to three core behaviours — currently we do not.

---

### Issue 2 – US-02 Is Underrepresented in Interaction Models

We have a wireframe for logging a study session, but we do not currently have a sequence diagram for **US-02 Log Progress**. Since this is one of the three agreed core stories, it requires its own interaction model showing the flow from the student entering progress data through to the system saving it and updating the task record.

---

### Issue 3 – US-05 Scope Is Drifting Toward Advanced Features

Our dashboard-related materials include ideas such as a Gantt or workload view. However, our agreed must-work scope for US-05 is more focused:

- Calculate percentage of work done from US-02 logs
- Show module name
- Show module status: On Track or Behind Schedule

The more advanced Gantt-style behaviour is closer to a future enhancement than our minimum viable Sprint 1 version. This scope drift needs to be corrected before implementation begins.

---

### Issue 4 – Dashboard Wireframe Does Not Show Status Labels

The current dashboard wireframe shows module bars and dates, but does not clearly show a textual status such as **On Track** or **Behind Schedule**. This is part of the must-work definition of US-05 and must be visible in the wireframe before the sprint begins.

---

### Issue 5 – Import Sequence Has Unclear Persistence Behaviour

In the import happy path, the system appears to create and save an empty timetable early in the flow, then insert module and deadline data afterwards. If the import fails partway through, it is currently unclear whether:

- the empty timetable shell remains saved
- partial data is stored
- the entire import is rolled back

This must be clarified so that the design matches the US-01 requirement that deadlines are saved without losing any dates. Our preferred approach is an atomic import: nothing is saved unless the entire file is processed successfully.

---

### Issue 6 – Error Handling Is Inconsistent Across Stories

We have an unhappy path for login and for import, but UI coverage is uneven:

- The import error has a wireframe
- The login error is shown in a sequence diagram but not clearly in the wireframes
- Progress logging validation errors (US-02) are not yet shown anywhere

Error, loading, and success states should be visible in the UI design for all three core stories, not just import.

---

### Issue 7 – Sequence Diagrams Do Not Fully Respect Architecture Boundaries

In our current diagrams, the "Study Planner System" performs several internal actions but persistence is hidden inside a single lifeline. While this is acceptable at a high level, our final sequence diagrams should reflect the layered boundaries defined in our architecture — for example: UI → Backend → Service → Database — rather than treating the system as a single black box.

---

## New Assumptions Discovered During Iteration

The following assumptions were previously implicit and are now formally documented:

| # | Assumption |
|---|---|
| 1 | **Authentication is required before core actions.** The user must be logged in before importing data, logging progress, or viewing the dashboard. |
| 2 | **The first supported upload format will be CSV only.** This keeps US-01 small enough for an initial sprint. |
| 3 | **The imported file contains sufficient data to create module records and deadlines.** We assume fields include module code, assessment name, and deadline date. |
| 4 | **Each module can have multiple progress logs.** US-02 requires repeated updates over time, not a single completion value. |
| 5 | **Dashboard progress is calculated from logged study data.** US-05 depends directly on data created through US-02. |
| 6 | **A simple status rule will be used first.** The system will compare logged progress against expected progress based on deadline proximity, then label a module as On Track or Behind Schedule. |
| 7 | **User-facing errors will be simple; technical detail is logged internally.** For example, users see "Import failed, please try again" rather than a raw exception trace. |

---

## Proposed Refinements

Based on the review above, the following changes will be made before Sprint 1 implementation begins.

---

**Change 1 – Replace the US-03 sequence with a US-02 sequence**

Remove or postpone the US-03 workload/Gantt sequence diagram and replace it with a proper US-02 Log Progress sequence showing the full interaction flow including validation.

*Reason: US-02 is one of the three agreed core stories. US-03 is not.*

---

**Change 2 – Simplify the dashboard to match minimum viable scope**

The Sprint 1 dashboard will focus on three outputs only: module name, percentage complete, and current status (On Track / Behind Schedule). Advanced workload and Gantt-style behaviour will be deferred to Sprint 2.

*Reason: this matches the agreed must-work scope for US-05.*

---

**Change 3 – Add visible status labels to the dashboard wireframe**

The dashboard screen must be updated to show explicit status labels such as On Track and Behind Schedule alongside each module entry.

*Reason: this is required by US-05 and is currently missing from the wireframe.*

---

**Change 4 – Add progress logging interaction and validation state to US-02 wireframe**

The US-02 wireframe should show the form for entering either time spent or tasks completed, and must also show what happens when the user submits incomplete or invalid data (the validation failure state).

*Reason: the current design shows the form but not the failure or validation behaviour.*

---

**Change 5 – Clarify import failure behaviour**

We need to formally define what happens on an unsuccessful import. The three options are:

- Save nothing (full rollback)
- Save only valid rows (partial save)
- Save an empty timetable shell

Our preferred option is a **full rollback**: no deadline data is saved unless the import completes successfully. This reduces data inconsistency and directly supports the US-01 requirement not to lose dates.

---

## Sprint 1 Backlog

The following tasks make up the Sprint 1 backlog, derived from the three core user stories. All items are scoped to the minimum viable functionality agreed above.

| Backlog Item | Linked Story | Reason for Priority |
|---|---|---|
| Implement login / authentication flow | Supports all core stories | Needed before users can access main features |
| Build a CSV import for the UEA data file | US-01 | The system has no planning data without the import |
| Parse and save modules and deadlines to database | US-01 | This is a core persistence requirement |
| Show the import success and import error states | US-01 | This is needed for basic UX feedback |
| Create the progress logging form | US-02 | This is the main way Michelle updates actual progress |
| Save the progress entries against one of the modules | US-02 | This is required so progress can later be compared |
| Validate the progress input | US-02 | This prevents bad or incomplete data |
| Calculate the module progress percentage | US-05 | This is needed as it is core functionality for our dashboard |
| Display the module name, percentage and status | US-05 | This is the minimum requirement needed for a viable dashboard |
| Mark modules as On Track or Behind Schedule | US-05 | This is needed for visual feedback |
| Update the documentation and diagrams after the sprint | All | This is to keep everything consistent and aligned with our vision |

---

## Sprint Backlog Management

We will use **GitHub Projects** to manage the sprint backlog. This keeps tasks close to the codebase and matches the module guidance that sprint documentation should be archived close to the code.

Our board will use the following columns:

- **Backlog** — all identified tasks not yet scheduled
- **To Do** — tasks committed to the current sprint
- **In Progress** — tasks actively being worked on
- **Done** — completed and reviewed tasks
