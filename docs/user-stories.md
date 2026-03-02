# User Stories

All user stories follow the format:

> As a <user>, I want <goal>, so that <reason>.


## Story List

### US-01 – Module and Deadline Import  
> As Steve,  
> I want to import my modules and deadlines from the provided UEA data file,  
> so that I can see all my coursework deadlines in one place and begin planning my semester effectively.


### US-02 – Study Session Logging  
> As Michelle,  
> I want to log my study sessions against specific tasks,  
> so that I can track my actual progress towards each assessment deadline.


### US-03 – Workload Visualisation  
> As Ben,  
> I want to view my semester workload on a Gantt chart and dashboard,  
> so that I can identify busy periods, task dependencies, and track progress across all my modules.


### US-04 – Task Breakdown  
> As Steve,  
> I want the system to help me break coursework into smaller tasks,  
> so that I can create a realistic semester plan instead of cramming close to deadlines.


### US-05 – Module-Level Progress Overview  
> As Michelle,  
> I want to see a dashboard showing my progress percentage per module,  
> so that I can prioritise the assignments where I am falling behind schedule.


# Acceptance Notes (Initial Behaviour Scenarios)

The following scenarios outline example validation conditions for selected stories.


## US-01 – Data Import

**Given** Steve is on the module import page  
**When** he uploads a valid UEA data file  
**Then** all module names, coursework, and deadlines appear in the system without requiring manual entry  


## US-02 – Study Session Logging

**Given** Michelle has an active assessment task  
**When** she enters a study session duration and saves it  
**Then** the progress percentage for that specific task (and relevant module) updates accordingly  


## US-03 – Gantt Chart Visualisation

**Given** Ben is viewing the Gantt chart  
**When** a task passes its deadline without being completed  
**Then** that task is highlighted in a different colour to indicate it is overdue  


# Assumptions and Constraints

- The UEA data file follows an agreed, valid structure.
- Progress percentages are calculated based on measurable task requirements (e.g., hours required vs. hours completed).
- Deadline comparisons use system time.
- Visual indicators (e.g., colour changes) must be clearly distinguishable and accessible.
