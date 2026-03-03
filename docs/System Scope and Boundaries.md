Defining Our System Scope and Boundaries 

System definition
System: A Study Planner that helps students import assessment deadlines, break coursework into manageable tasks, schedule/track study sessions, visualise progress/dependencies, and receive reminders.

System boundary: Everything the app stores, calculates, displays and notifies about study planning and progress is inside. Anything to do with teaching, grading, official timetabling, or institutional data ownership/accuracy is outside.

IN SCOPE (System)

Components, features, and functionalities that are part of the system being developed:
School data import & organisation 

Import module/assessment info and deadlines from a school source.
Automatically organise imported items into semester/module structures like sections and timelines.

Coursework breakdown into milestones

Let users deconstruct coursework into smaller tasks/subtasks.
Support task dependencies (e.g., “research” before “write draft”).

Study session logging tied to tasks

Users can log study sessions and label/link them to specific tasks.
Use this linkage to support progress tracking toward completion.

Progress + dependency visualisation

Provide visual representations (e.g., Gantt-style timeline) showing:
task timing across semester, completion indicators (e.g., % progress bars),dependency relationships.

Module-level progress dashboard

Aggregate task progress per module and across modules.
Surface where attention is needed (e.g., “Module A behind schedule”).

Deadline and overdue reminders

Send notifications for:
tasks due in X days and overdue tasks requiring attention.


OUT OF SCOPE (Environment)

These are explicitly not the system’s responsibility:
Official institutional data correctness

The system is not responsible for guaranteeing school-provided data is correct/complete.
Resolving discrepancies with school records is outside scope.

Teaching/learning content delivery

No tutoring, revision notes, lecture content, solutions, or marking/feedback.

Grading, submissions, and academic administration

Not responsible for submitting coursework, interfacing with plagiarism checks, marking, or grade calculation as an official record.
Not an official student record system.

Creating a full timetable / attendance enforcement

Not responsible for generating the university timetable, managing classes, or enforcing attendance.

Mental health / wellbeing intervention

Not responsible for clinical wellbeing monitoring, diagnosis, or crisis support it can be a “signpost” later, but not accountable.

Device/OS notification delivery guarantees

The app can request notifications, but OS/platform delivery failures are outside the system’s responsibility.

Third-party service availability

If an external calendar/LMS is down or changes their API, that’s outside your system boundary.

- 
Actors & External Systems
Key users and external systems that interact with the system:

External actors (outside, but interacting with the system):

Primary user: Student - creates tasks, logs sessions, views progress, receives reminders.

Optional supporting actors: Tutor / mentor / study buddy.

Institution staff/systems: University/school admin systems that provide module/deadline data.

External systems / services (outside the boundary):

School systems / LMS (e.g.Blackboard) — source of deadlines and module info.

Institution data sources (module catalogue, assessment calendars).

Notification platform (iOS/Android/Web push notification services).

Calendar services (Google/Apple/Microsoft calendars) if you plan optional sync.
Authentication provider (e.g., SSO) if used.
