# 2.3 User Stories

All user stories follow the Connextra format:
> As a [persona], I want [feature], so that [benefit].

Stories are split by sprint. Each story includes a happy path and at least one unhappy path as acceptance criteria.

---

## 2.3.1 Sprint 1 Features

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


