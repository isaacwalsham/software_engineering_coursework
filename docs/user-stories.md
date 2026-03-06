# 2.3 User Stories

All user stories follow the Connextra format:
> As a [persona], I want [feature], so that [benefit].

Stories are split by sprint. Each story includes a happy path and at least one unhappy path as acceptance criteria.

---

## 2.3.1 Sprint 1 Features (Weeks 6–8)

---

### US-01 – Module and Deadline Import
> As Steve,
> I want to import my modules and deadlines from the provided UEA data file,
> so that I can see all my coursework deadlines in one place and begin planning my semester effectively.

**Priority:** High – Core system requirement. All other features depend on this.

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
> As Michelle,
> I want to log my study sessions against specific tasks,
> so that I can track my actual progress towards each assessment deadline.

**Priority:** High – Core progress tracking capability.

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
> As Ben,
> I want to view my semester workload on a Gantt chart,
> so that I can identify busy periods, task dependencies, and track progress across all my modules.

**Priority:** High – Key differentiating feature specified in the project brief.

**Happy Path:**
- Given modules and tasks have been imported and defined
- When the student selects the Gantt chart view
- Then tasks are displayed on a timeline showing start dates, deadlines, dependency arrows, and progress fills indicating completion percentage

**Unhappy Path – No modules imported:**
- Given no modules have been imported
- When the user navigates to the Gantt chart view
- Then the system displays a blank chart with a prompt: *"Import your module data to view the Gantt chart."*

---

### US-04 – Task Breakdown and Dependencies
> As Steve,
> I want the system to help me break coursework into smaller tasks with dependencies,
> so that I can create a realistic semester plan instead of cramming close to deadlines.

**Priority:** High – Core task management requirement from the project specification.

**Happy Path:**
- Given a module and assessment exist
- When the user creates a task and selects one or more prerequisite tasks from the dependency selector
- Then the system stores the dependency, displays the task as locked in the Gantt chart until prerequisites are complete, and prevents it from being started prematurely

**Unhappy Path – Circular dependency:**
- Given the user attempts to create a dependency that would result in a cycle (e.g. Task A depends on Task B which already depends on Task A)
- When the system detects the cycle
- Then an error message is displayed: *"Circular dependency detected. Please review task dependencies."*, and the dependency is not created

---

### US-05 – Module-Level Progress Dashboard
> As Michelle,
> I want to see a dashboard showing my progress percentage per module,
> so that I can prioritise the assignments where I am falling behind schedule.

**Priority:** High – Specified dashboard requirement in the project brief.

**Happy Path:**
- Given tasks and activities have been logged across one or more modules
- When the user opens the Study Dashboard
- Then the system displays completed deadlines, upcoming deadlines with progress bars, and missed deadlines — each section colour-coded with percentage completion figures

**Unhappy Path – No activities logged:**
- Given a module has been imported but no activities have been logged
- When the user opens the dashboard
- Then a progress bar at 0% is displayed with a message encouraging the user to begin logging study activities

---

## 2.3.2 Test Cases for Sprint 1

See [TestCase.md](../TestCase.md) for full test cases TC-01 through TC-12 covering all Sprint 1 stories.

---

## 2.3.3 Sprint 2 Features (Weeks 9–11)

---

### US-06 – Milestone Management
> As Michelle,
> I want to define intermediate milestones with their own deadlines,
> so that I can track progress towards major coursework submissions in stages.

**Priority:** Medium – Specified in the project brief; builds on Sprint 1 task framework.

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
> As Steve,
> I want to attach a single study activity to multiple tasks,
> so that cross-cutting study sessions contribute to the completion of more than one task simultaneously.

**Priority:** Medium – Specified in the project brief for study progress capture.

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
> As Michelle,
> I want to update task and assessment deadlines within the system,
> so that I can reflect extensions granted by module organisers without losing my existing progress data.

**Priority:** Medium – Explicitly specified in the project brief.

**Happy Path:**
- Given a task or assessment exists
- When the user selects "Edit Deadline" and enters a new valid future date
- Then the system updates the stored deadline, recalculates the dashboard status for the affected item, and re-renders the Gantt chart to reflect the change

**Unhappy Path – Past date entered:**
- Given the user enters a new deadline date that is in the past
- When the system validates the input
- Then a warning is displayed: *"The deadline you entered is in the past. Are you sure?"*

---

## 2.3.4 Test Cases for Sprint 2

See [TestCase.md](../TestCase.md) for full test cases TC-13 through TC-18 covering all Sprint 2 stories.

---

## Assumptions and Constraints

| # | Assumption |
|---|---|
| 1 | The UEA data file follows an agreed, valid structure with fields including module code, assessment name, and deadline date |
| 2 | Progress percentages are calculated from measurable task requirements (e.g. hours required vs. hours completed) |
| 3 | Deadline comparisons use system time |
| 4 | Visual indicators such as colour changes must be clearly distinguishable and meet WCAG 2.1 AA accessibility standards |
| 5 | The first supported upload format will be CSV; JSON support may be added in Sprint 2 |
