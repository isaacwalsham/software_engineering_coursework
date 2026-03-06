# 2.4 Major System Responsibilities

The primary responsibilities of the Study Planner system, derived from the project specification and user stories, are as follows:

---

### School Data Import

The system must accept and parse a structured data file provided by the UEA Hub, containing module names, assessment titles, weightings, and deadlines. Upon successful validation, the system automatically creates a semester profile and populates module content areas reflecting the structure of the academic semester. This responsibility directly supports **US-01**.

---

### Coursework Breakdown

The system must allow students to decompose coursework assessments into smaller, more manageable study tasks. Each task must belong to a specific assessment event and capture a type (e.g. programming, writing, studying), a required completion criterion, a start date, and a deadline. This structure enables students to focus on individual task dependencies rather than treating a coursework submission as a single undivided unit. This responsibility directly supports **US-04**.

---

### Tie Study Sessions to Tasks to Track Progress

The system must allow students to log study activities and attach them to one or more specific tasks. Each activity records a type, duration, quantity completed, and optional notes. The cumulative quantity logged against a task is used to calculate progress towards that task's requirement criterion using the formula:

**Progress (%) = (Quantity Completed ÷ Requirement) × 100**

This responsibility directly supports **US-02**.

---

### Produce Visual Representations of Tasks, Progress, and Dependencies

The system must provide a Gantt chart visualisation that renders tasks as bars on a semester timeline, showing start dates, deadlines, and a progress fill indicating completion percentage. Task dependency relationships must be displayed as arrows between task bars, clearly indicating which tasks are locked until prerequisites are complete. Milestone markers must be rendered as diamond shapes at their respective deadline positions. This responsibility directly supports **US-03**.

---

### Collate Progress Towards Each Module

The system must feature a Study Dashboard that aggregates progress data across all modules and classifies each deadline into one of three categories:

- **Completed** – all associated tasks meet their requirement criteria
- **Upcoming** – deadline has not yet passed but tasks are not yet complete
- **Missed** – deadline has passed and tasks were not completed

Each deadline entry on the dashboard must display a progress bar indicating how far the student is towards completing the associated work. This responsibility directly supports **US-05**.

---

### Deadline and Overdue Reminders

The system must compare task and assessment deadlines against the current system date and provide visual notifications to the student. Tasks approaching their deadline must be highlighted in amber; tasks that are overdue must be highlighted in red. This gives students immediate visibility of at-risk work without needing to manually check each module. This responsibility supports all user stories.
