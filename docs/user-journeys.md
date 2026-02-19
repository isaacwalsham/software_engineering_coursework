# Study Planner – User Journeys

This section outlines end-to-end user journeys derived from the primary personas:  
Steve Beaton, Michelle Lush, and Ben Williams.  

Each journey describes:
- The user’s goal
- Key interaction steps
- System touchpoints
- Pain points and risks

These journeys directly inform functional requirements, dashboard design, and system architecture.

---

## Persona 1: Steve Beaton  
**Goal:** Break coursework into manageable tasks and avoid last-minute deadlines.

### Journey: Managing Overlapping Coursework

#### Stage 1 – Semester Setup
1. Steve creates a new semester profile.
2. He uploads the module data file provided by the University Hub.
3. The system validates the file and generates module pages with deadlines.

**System Touchpoints:**
- Semester Profile Creation
- File Upload & Validation
- Module Overview Dashboard

---

#### Stage 2 – Task Planning
4. Steve selects a coursework assignment.
5. He breaks it into smaller tasks (research, implementation, testing).
6. He assigns estimated effort to each task.
7. He defines dependencies between tasks.
8. He creates intermediate milestones.

**System Touchpoints:**
- Task Creation Interface
- Dependency Selector
- Milestone Creation
- Gantt Chart View

---

#### Stage 3 – Progress Monitoring
9. Steve opens the Study Dashboard weekly.
10. The system evaluates upcoming deadlines.
11. Progress bars display completion status.
12. The Gantt chart highlights workload overlaps.

**System Touchpoints:**
- Study Dashboard
- Progress Calculation Engine
- Deadline Evaluation Service
- Gantt Visualisation

**Pain Points / Risks:**
- Underestimating time requirements
- Incorrect dependency configuration
- Overlapping deadlines causing workload spikes

---

## Persona 2: Michelle Lush  
**Goal:** Balance study with work commitments and monitor whether she is on track.

### Journey: Time-Constrained Study Planning

#### Stage 1 – Reviewing Deadlines
1. Michelle opens the Study Dashboard.
2. Deadlines are categorised as upcoming, completed, or missed.
3. She checks milestone progress.

**System Touchpoints:**
- Dashboard Overview
- Deadline Status Classification
- Progress Bars

---

#### Stage 2 – Planning Around Work
4. Michelle views the Gantt chart.
5. She identifies free time between work shifts.
6. She schedules study tasks accordingly.
7. She updates deadlines if extensions are granted.

**System Touchpoints:**
- Gantt Chart Interface
- Task Scheduling
- Deadline Update Functionality

---

#### Stage 3 – Logging Study Activity
8. After studying, Michelle logs an activity (e.g., 2 hours writing).
9. She links the activity to relevant tasks.
10. The system recalculates progress automatically.

**System Touchpoints:**
- Activity Logging Interface
- Activity-to-Task Linking
- Progress Calculation Service

**Pain Points / Risks:**
- Falling behind due to limited time
- Difficulty determining if she is "on track"
- Overlooking smaller milestones

---

## Persona 3: Ben Williams  
**Goal:** Gain structure and confidence in managing coursework independently.

### Journey: Building Structured Study Habits

#### Stage 1 – Initial Setup
1. Ben creates a semester profile.
2. He uploads the hub-provided file.
3. Coursework deadlines populate automatically.

**System Touchpoints:**
- Profile Setup
- File Loader
- Module Overview Page

---

#### Stage 2 – Creating Structured Tasks
4. Ben views coursework deadlines.
5. He creates simple tasks for each assessment.
6. Tasks appear in a visual timeline.

**System Touchpoints:**
- Task Creation Interface
- Gantt Chart View
- Milestone Overview

---

#### Stage 3 – Tracking Progress
7. Ben logs small study activities regularly.
8. Task completion percentages update automatically.
9. The dashboard shows visual progress toward deadlines.

**System Touchpoints:**
- Activity Logger
- Progress Indicators
- Deadline Dashboard

**Pain Points / Risks:**
- Feeling overwhelmed by workload
- Uncertainty about sufficient progress
- Reduced motivation if progress is unclear

---

# UX Principles Supporting All Journeys

Across all personas, the following design elements support effective use:

- Clear categorisation of deadlines (upcoming, completed, missed)
- Visual progress bars for tasks and milestones
- Interactive Gantt chart for dependency awareness
- Simple activity logging
- Automatic progress recalculation

These features directly address user frustrations identified in the personas and support the core functional requirements of the Study Planner.
