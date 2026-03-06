# 2.2 User Journeys

User journeys describe the end-to-end interaction flows for each persona, from initial motivation through system interaction to successful outcome. They were derived from the three primary personas — Steve Beaton, Michelle Lush, and Ben Williams — and directly inform the functional requirements, dashboard design, and system architecture.

Across all three journeys, three recurring behavioural themes emerge:

1. Structured import of academic data
2. Decomposition of coursework into manageable tasks
3. Measurable progress tracking with visual feedback

---

## Journey 1: Steve Beaton – Semester Setup and Task Planning

**Goal:** Break coursework into manageable tasks and avoid last-minute deadline pressure.

### Stage 1 – Semester Setup

| Step | Steve's Action | System Response |
|---|---|---|
| 1 | Logs in and selects "New Semester" | System prompts for a semester identifier and data file upload |
| 2 | Enters "Spring 2026" and uploads his hub data file | System validates the file, extracts module and assessment data, and creates content areas for each module |
| 3 | Navigates to CMP-5012B and views the imported assessments | System displays coursework titles, weightings, and deadlines |

**System Touchpoints:** Semester Profile Creation, File Upload and Validation, Module Overview Dashboard

---

### Stage 2 – Task Planning

| Step | Steve's Action | System Response |
|---|---|---|
| 4 | Selects a coursework item and clicks "Add Task" | System presents the task creation form: type, required hours, start date, deadline |
| 5 | Creates tasks for research, implementation, and testing | System stores tasks linked to the assessment |
| 6 | Assigns estimated effort to each task | System updates the task requirement criterion |
| 7 | Defines dependencies between tasks | System stores dependency links; dependent tasks display as locked until prerequisites are complete |
| 8 | Creates intermediate milestones | System renders milestone diamond markers on the Gantt chart |

**System Touchpoints:** Task Creation Interface, Dependency Selector, Milestone Creation, Gantt Chart View

---

### Stage 3 – Progress Monitoring

| Step | Steve's Action | System Response |
|---|---|---|
| 9 | Opens the Study Dashboard weekly | System evaluates all upcoming deadlines and recalculates progress |
| 10 | Reviews progress bars per assessment | System displays completion percentages based on logged activity data |
| 11 | Opens the Gantt chart | System highlights workload overlaps and at-risk tasks |

**System Touchpoints:** Study Dashboard, Progress Calculation Engine, Deadline Evaluation Service, Gantt Visualisation

**Pain Points / Risks:**
- Underestimating time requirements for individual tasks
- Incorrect dependency configuration causing tasks to be blocked unexpectedly
- Overlapping deadlines across modules causing workload spikes

---

## Journey 2: Michelle Lush – Time-Constrained Study Planning

**Goal:** Balance study with work commitments and monitor whether she is on track.

### Stage 1 – Reviewing Deadlines

| Step | Michelle's Action | System Response |
|---|---|---|
| 1 | Opens the Study Dashboard | System displays the dashboard with deadlines classified as upcoming, completed, or missed |
| 2 | Reviews deadline categories | System shows colour-coded status indicators and progress bars per assessment |
| 3 | Checks milestone progress | System displays milestone completion status linked to prerequisite tasks |

**System Touchpoints:** Dashboard Overview, Deadline Status Classification, Progress Bars

---

### Stage 2 – Planning Around Work

| Step | Michelle's Action | System Response |
|---|---|---|
| 4 | Opens the Gantt chart | System renders the full semester timeline with task bars and dependency arrows |
| 5 | Identifies free time between work shifts | System displays task start dates and deadlines alongside the timeline |
| 6 | Schedules study tasks around her availability | System stores updated task planning data |
| 7 | Updates a deadline following a granted extension | System recalculates dashboard status and re-renders the Gantt chart |

**System Touchpoints:** Gantt Chart Interface, Task Scheduling, Deadline Update Functionality

---

### Stage 3 – Logging Study Activity

| Step | Michelle's Action | System Response |
|---|---|---|
| 8 | Selects "Log Activity" after a study session | System presents the activity logging form: type, duration, quantity, notes |
| 9 | Enters 2 hours of writing and links it to the Literature Review task | System records the activity and updates cumulative hours on the task |
| 10 | Returns to the dashboard | System recalculates progress automatically; task moves from Upcoming to In Progress |

**System Touchpoints:** Activity Logging Interface, Activity-to-Task Linking, Progress Calculation Service

**Pain Points / Risks:**
- Falling behind due to limited available study time
- Difficulty determining whether she is genuinely on track for a deadline
- Overlooking smaller milestones that contribute to major submissions

---

## Journey 3: Ben Williams – Building Structured Study Habits

**Goal:** Gain structure and confidence in managing coursework independently.

### Stage 1 – Initial Setup

| Step | Ben's Action | System Response |
|---|---|---|
| 1 | Creates a new semester profile | System prompts for a semester name and data file upload |
| 2 | Uploads the hub-provided file | System validates the file and populates module pages with coursework deadlines |
| 3 | Reviews the imported module overview | System displays all modules with their assessments and deadlines |

**System Touchpoints:** Profile Setup, File Loader, Module Overview Page

---

### Stage 2 – Creating Structured Tasks

| Step | Ben's Action | System Response |
|---|---|---|
| 4 | Browses coursework deadlines for each module | System displays assessment titles, weightings, and deadlines per module |
| 5 | Creates simple tasks for each assessment | System stores tasks and links them to their parent assessments |
| 6 | Views the Gantt chart | System renders tasks as bars on the semester timeline |

**System Touchpoints:** Task Creation Interface, Gantt Chart View, Milestone Overview

---

### Stage 3 – Tracking Progress

| Step | Ben's Action | System Response |
|---|---|---|
| 7 | Logs a small study activity after each session | System records the activity and links it to the selected task |
| 8 | Checks task completion percentages | System updates progress bars automatically based on logged data |
| 9 | Reviews the dashboard | System highlights at-risk deadlines in amber or red; on-track items in green |

**System Touchpoints:** Activity Logger, Progress Indicators, Deadline Dashboard

**Pain Points / Risks:**
- Feeling overwhelmed by the total volume of coursework across modules
- Uncertainty about whether progress logged so far is sufficient
- Reduced motivation if visual progress indicators do not update clearly

---

## UX Principles Supporting All Journeys

Across all three personas, the following design elements directly address the identified pain points and frustrations:

| Design Element | Pain Point Addressed |
|---|---|
| Clear deadline categorisation (upcoming, completed, missed) | Difficulty knowing what needs immediate attention |
| Visual progress bars per task and assessment | Uncertainty about how much work remains |
| Interactive Gantt chart with dependency arrows | No visibility of task dependencies in generic tools |
| Simple activity logging form | Friction in recording study progress regularly |
| Automatic progress recalculation on activity save | Manual tracking burden leading to stale data |
| Colour-coded deadline status (green / amber / red) | Lack of early warning for at-risk deadlines |
