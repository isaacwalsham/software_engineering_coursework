# Acceptance Criteria

Acceptance criteria are expressed using Given/When/Then format. Each user story includes a happy path and at least one unhappy path. Stories are organised by sprint.

---

## Sprint 1

---

### US-01 – Semester Profile and Module Import
**Persona:** Steve Beaton
**Main Aim:** Steve wants to import his modules and deadlines from the UEA data file so that he can plan his semester.

**Happy Path:**
- Given the user is logged into the system
- When the user creates a new semester profile, provides a semester name, and uploads a valid UEA data file
- Then the system validates the file, creates a semester profile, and displays module content areas with their associated coursework titles, weightings, and deadlines

**Unhappy Path 1 – Invalid file type:**
- Given the user uploads a file with an unsupported format (e.g. `.txt`)
- When the system attempts to parse the file
- Then an error message is displayed stating the required file format, and no data is imported

**Unhappy Path 2 – Empty file:**
- Given the user uploads an empty file
- When the system attempts to parse it
- Then an error message is displayed stating the file contains no module data, and the semester profile is not created

---

### US-02 – Study Session Logging
**Persona:** Michelle Lush
**Main Aim:** Michelle aims to log her study sessions against coursework tasks, allowing her to track her progress towards task completion.

**Happy Path:**
- Given a task exists and the user is on the task page
- When the user logs a study session with a valid duration and selects a task to attach it to
- Then the activity is recorded, the cumulative time spent on the task is updated, and the task progress percentage is recalculated

**Unhappy Path – Invalid duration:**
- Given the user attempts to log a study session
- When an invalid duration is entered (e.g. a negative value, zero, or non-numeric input)
- Then an error message is displayed and the session is not recorded

---

### US-03 – Gantt Chart Visualisation
**Persona:** Ben Williams
**Main Aim:** Ben wishes to view his work throughout the semester on a Gantt chart, so he can see where he may be falling behind in his studies.

**Happy Path:**
- Given the user has uploaded a data file containing UEA modules and their associated tasks
- When the student selects the Gantt chart view
- Then tasks are displayed on a timeline showing start dates, deadlines, dependency arrows, and progress fills

**Unhappy Path – No modules imported:**
- Given no modules have been imported
- When the user tries to load the Gantt chart
- Then the user sees a blank chart with a message prompting them to import their modules and deadlines

---

### US-04 – Task Breakdown and Dependencies
**Persona:** Steve Beaton
**Main Aim:** Steve wants to break coursework into smaller tasks with dependencies so he can build a realistic semester plan.

**Happy Path:**
- Given a module and assessment exist
- When the user creates a task and selects one or more prerequisite tasks from the dependency selector
- Then the system stores the dependency, displays the task as locked in the Gantt chart until prerequisites are complete, and prevents it from being started prematurely

**Unhappy Path – Circular dependency:**
- Given the user attempts to create a dependency that would result in a cycle (e.g. Task A depends on Task B which already depends on Task A)
- When the system detects the cycle
- Then an error message is displayed and the dependency is not created

---

### US-05 – Module-Level Progress Dashboard
**Persona:** Michelle Lush
**Main Aim:** Michelle wants to see a dashboard showing her progress per module so she can prioritise where she is falling behind.

**Happy Path:**
- Given tasks and activities have been logged across one or more modules
- When the user opens the Study Dashboard
- Then the system displays completed deadlines, upcoming deadlines with progress bars, and missed deadlines — each section colour-coded with percentage completion figures

**Unhappy Path – No activities logged:**
- Given a module has been imported but no activities have been logged
- When the user opens the dashboard
- Then a progress bar at 0% is displayed with a message encouraging the user to begin logging study activities

---

## Sprint 2

---

### US-06 – Milestone Management
**Persona:** Michelle Lush
**Main Aim:** Michelle wants to define intermediate milestones with their own deadlines so she can track progress towards major submissions in stages.

**Happy Path:**
- Given tasks exist within an assessment
- When the user creates a milestone with a name, deadline, and links it to one or more prerequisite tasks
- Then the system stores the milestone, displays it as a diamond marker on the Gantt chart, and marks it as achieved once all linked tasks are completed

**Unhappy Path – Milestone deadline before task deadline:**
- Given the user sets a milestone deadline that falls before the deadline of one of its linked tasks
- When the system validates the milestone
- Then a warning is displayed: *"Milestone deadline precedes one or more prerequisite task deadlines."*

---

### US-07 – Activity Attached to Multiple Tasks
**Persona:** Steve Beaton
**Main Aim:** Steve wants to attach a single study activity to multiple tasks so that cross-cutting sessions contribute to more than one task at once.

**Happy Path:**
- Given multiple tasks exist within an assessment
- When the user logs an activity and selects two or more tasks from the task selector
- Then the system records the activity and updates the progress percentage of all linked tasks accordingly

**Unhappy Path – No task selected:**
- Given the user fills in the activity log form
- When they attempt to submit without selecting any task
- Then an error message is displayed: *"Please select at least one task for this activity."*

---

### US-08 – Deadline Update
**Persona:** Michelle Lush
**Main Aim:** Michelle wants to update task and assessment deadlines to reflect extensions granted by module organisers, without losing her existing progress data.

**Happy Path:**
- Given a task or assessment exists
- When the user selects "Edit Deadline" and enters a new valid future date
- Then the system updates the stored deadline, recalculates the dashboard status for the affected item, and re-renders the Gantt chart to reflect the change

**Unhappy Path – Past date entered:**
- Given the user enters a new deadline date that is in the past
- When the system validates the input
- Then a warning is displayed: *"The deadline you entered is in the past. Are you sure?"*
