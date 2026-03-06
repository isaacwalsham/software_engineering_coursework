# 3.1 System Scope and Boundaries

## System Definition

Our system is a Study Planner, which is a web-based academic planning application that helps students import assessment deadlines, break down coursework into manageable tasks, log and track study sessions, see progress and task dependencies, and receive reminders for upcoming and overdue work.

**System Scope and boundary:** Everything the application stores, calculates, displays, and notifies about study planning and progress is inside the boundary. Anything related to teaching, grading or timetabling is outside the boundary.



## In Scope

The following components, features, and functionalities are part of our system being developed.

### School Data Import and Organisation
- Import module and assessment information and deadlines from a data file provided by UEA.
- Automatically organise imported data into semester and module structures, mirroring the academic semester timeline.
- Validate file format and structure before persisting any data.

### Coursework Breakdown into Tasks and Milestones
- Allowing students to break down coursework assessments into smaller chunks, like more feasible study tasks.
- Support task dependencies (e.g. a "Write Draft" task cannot begin until "Research" is complete).
- Allow students to define their own milestones with their own deadlines, linked to one or more tasks.

### Study Session Logging Tied to Tasks
- Allow students to log study activities and link them to one or more specific tasks.
- Capture what the students are studying, the duration, quantity completed, date, and optional notes.
- Use logged activity data to calculate and update progress towards task completion.

### Progress and Dependency Visualisation
- Provide a Gantt chart timeline showing task bars across the semester, with start dates and deadlines.
- Display progress fills within task bars indicating percentage completion.
- Use dependency arrows between tasks to show which tasks are locked until the previous tasks are complete.
- Display milestone markers at their respective deadline positions.

### Module-Level Progress Dashboard
- Aggregate task progress across all modules and assessments.
- Classify each deadline as completed, upcoming, or missed based on progress and current date.
- Display a progress bar for each deadline so students can prioritise and identify visually where their attention is needed.

### Deadline and Overdue Reminders
- Compare task and assessment deadlines against the current system date.
- Highlight tasks especially ones that are approaching their deadline in amber and overdue tasks in red.
- Surface these alerts on the dashboard so students have immediate visibility of work due imminently.



## Out of Scope

The following are explicitly outside the system's responsibility.

| Area | Reason |
|---|---|
|  Data correctness | The system is not responsible for guaranteeing that school-provided data is accurate or complete. Issues with school records must be resolved externally. |
| Teaching and learning content delivery | No tutoring, revision notes, lecture content, solutions, or marking feedback. |
| Grading, submissions, and academic administration | Not responsible for submitting coursework, interfacing with plagiarism checks, marking, or grade calculation as an official record. Not an official student record system. |
| University timetable generation | Not responsible for generating the university timetable, managing classes, or enforcing attendance. |
| Mental health and wellbeing intervention | Not responsible for clinical wellbeing monitoring, diagnosis, or crisis support. |
| Device and OS notification delivery | The system can request notifications, but OS and platform delivery failures are outside the system's responsibility. |
| Third-party service availability | If an external calendar service or LMS changes their API or becomes unavailable, that is outside the system boundary. |



## Actors and External Systems

### Primary Actor
- **Student** — creates tasks, logs study sessions, views progress, and receives reminders

### Optional Supporting Actors
- **Tutor / Mentor / Study Buddy** — may view shared progress in future iterations 

### External Systems Interacting with the Boundary

| External System | Role |
|---|---|
| UEA Hub / School LMS (e.g. Blackboard) | Source of module, assessment, and deadline data — provided as a structured file |
| Institution data sources | Module catalogue and assessment calendars that generate the hub data file |
| Notification platform | iOS / Android / Web push notification services used to deliver reminders |
| Calendar services | Google / Apple / Microsoft calendars — optional sync considered for future iterations |
| Authentication provider | SSO or institutional login provider if used for student authentication |
