**Iteration**

***Review of selected user stories***


We selected three user stories as the core of the system:

US-01 Import Data: Without this, there is no planning data.

Must work: Read UEA data file correctly; deadlines saved without losing dates.

Can wait: drag/drop UI, multiple file types, automated error correction.

US-02 Log Progress: Main action Michelle uses to track work.

Must work: Log time or tasks completed against a module; save “actual progress” to compare against deadlines.

Can wait: stopwatch timer, photos/notes, edit/delete logs.

US-05 Dashboard: Essential feedback loop.

Must work: Calculate % complete from logs; show module status (Behind/On Track).

Can wait: interactive Gantt, theming/colour, sharing.

This fits the fact that interaction artefacts should stay consistent across user stories, UX, architecture, and interactions, and that we should watch for design drift as artefacts evolve.

After reviewing our diagrams and wireframes, we found the following issues:

- One of our sequence diagrams is not one of our chosen core stories

We selected US-01, US-02, and US-05 as our core stories, but one of the sequence diagrams currently models US-03 instead. This creates a mismatch between our prioritised requirements and our interaction modelling.

Why this matters: each sequence diagram should be linked to a user story and we should model 2 to 3 core behaviours.

- US-02 is underrepresented in the current interaction models

We have a wireframe for logging a study session, but we do not currently have a clearly shown sequence diagram for US-02 Log Progress. Since this is one of the three core stories, it maybe should have its own interaction model.

-US-05 scope is drifting toward advanced features

Our dashboard-related materials include ideas like a Gantt/workload view, but our agreed “must work” scope for US-05 is more basic:

- calculate percentage of work done from US-02 logs

- show module name

- show module status such as On Track or Behind Schedule

The more advanced Gantt-style behaviour is closer to a future enhancement than our minimum viable version.

- Dashboard wireframe does not fully show the required status output

The dashboard wireframe shows module bars and dates, but it does not clearly show a textual status such as On Track or Behind Schedule, even though this is part of the must-work definition of US-05.

- Import sequence needs clearer persistence logic

In the import happy path, the system appears to create and save an empty timetable early, then later inserts module and deadline data. If the import fails part way through, it is unclear whether:

- the empty timetable remains saved

- partial data is stored

- the import is rolled back

This needs to be clarified so the design matches the user story requirement that deadlines must be saved without losing any dates.

- Error handling is inconsistent across stories

We have an unhappy path for login and import, but the UI coverage is uneven:

- import error has a wireframe

- login error is shown in a sequence but not clearly in the wireframes

- progress logging validation errors are not yet shown

UX should make loading, error, and success states visible, and that error cases should be reflected in the UI

- Sequence diagrams should respect architecture boundaries, for example UI → Backend → Service → Database, not UI directly to data storage. 

In our diagrams, the “Study Planner System” performs several internal actions, but persistence is hidden inside one lifeline. That is acceptable at a high level, but we should make sure our final version still reflects the boundaries from our C4 model.

***New assumptions discovered***:

During iteration, we realised that several assumptions had been implicit and now need to be documented:

- Authentication is required before core actions
- The user must be logged in before importing data, logging progress, or viewing the dashboard.

- The first supported upload format will be CSV only
- This keeps US-01 small enough for an initial sprint.

- The imported file contains enough information to create module records and assessment deadlines
- We are assuming the UEA data file includes fields such as module code, assessment name, and deadline date.

- Each module can have multiple progress logs
- US-02 requires repeated updates over time, not just a single completion value.

- Dashboard progress is calculated from logged study/progress data
- US-05 depends directly on data created through US-02.

- A simple status rule will be used first
- For example, the system will compare logged progress against expected progress based on deadline proximity, then label a module as On Track or Behind Schedule.

- User-facing errors will be simple, while technical detail is logged internally
- For example, users may see “Import failed, please try again” rather than a raw exception trace.

***Based on the review, we would make the following refinements***:

Change 1: Replace the current US-03 sequence with a US-02 sequence

- We will remove or postpone the US-03 workload/Gantt sequence and create a proper US-02 Log Progress sequence instead.

- Reason: US-02 is one of the three agreed core stories, while US-03 is not.

Change 2: Simplify the dashboard to match minimum scope

- The dashboard in Sprint 1 will focus on: module name, percentage complete and current status

- We will postpone advanced workload/Gantt behaviour until later.

- Reason: this matches our chosen must-work scope for US-05.

Change 3: Add visible status labels to the dashboard wireframe

- The dashboard screen should show labels such as: On Track and Behind Schedule

- Reason: this is required by US-05 and is currently missing from the wireframe.

- Change 4: Add a clear progress logging interaction and validation state

- The US-02 wireframe should support entering either: time spent, or tasks completed

- It should also show what happens if the user submits incomplete or invalid data.

- Reason: the current design shows the form, but not the failure/validation behaviour.

Change 5: Clarify import failure behaviour

- We need to define whether an unsuccessful import: saves nothing, or saves only valid rows, or saves an empty timetable shell

- Our preferred option is to avoid saving partial deadline data unless the import succeeds cleanly.

- Reason: this reduces data inconsistency and better supports the requirement not to lose dates.

|   Backlog item        |           |           |<img width="483" height="644" alt="Screenshot 2026-03-04 at 13 06 07" src="https://github.com/user-attachments/assets/b07b7e92-a5fe-45da-81f3-b99cba6c64cf" />

|---------------|-----------|-----------|
|               |           |           |
|               |           |           |
|               |           |           |
|               |           |           |
|               |           |           |
|               |           |           |
|               |           |           |
|               |           |           |
|               |           |           |
|               |           |           |
