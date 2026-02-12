# Study Planner – Design Rationale

This document captures the key architectural reasoning behind the Study Planner system.  
It summarises how requirements influenced the system structure, why responsibilities are separated as they are, the assumptions made during design, and which parts of the architecture may evolve.

---

## 1. Requirements That Influenced the System Structure

### 1.1 Loading Module and Deadline Data
The requirement to load module, coursework, and deadline information from a defined file format directly influenced our decision to introduce a dedicated data-loading component (`ModuleLoader`).  
This separates external input handling from core domain logic, allowing the file format to change (e.g., JSON to API integration) without affecting task or dashboard functionality.

### 1.2 Task Dependencies
Since tasks can depend on other tasks, we structured `Task` as a core domain entity and centralised dependency validation within a service layer.  
This ensures business rules are enforced consistently and not embedded in the user interface.

### 1.3 Activity-Based Progress Tracking
Activities contribute toward task completion, so we modelled `Activity` separately from `Task`.  
Task progress is calculated dynamically from linked activities rather than stored as a fixed value.  
This avoids duplication, maintains consistency, and supports flexible progress metrics.

### 1.4 Dashboard and Deadline Evaluation
The requirement to categorise deadlines (completed, upcoming, missed) influenced the introduction of a dedicated dashboard evaluation component.  
Time-based logic is handled separately from presentation logic, enabling easier extension (e.g., reminders or notifications).

---

## 2. Why Responsibilities Are Separated This Way

We separated responsibilities according to key software engineering principles:

- **Separation of Concerns:** Data handling, business logic, and presentation logic are isolated to improve maintainability and testability.
- **Single Responsibility Principle:** Each component has one clear purpose (e.g., file loading, task validation, activity tracking, dashboard evaluation).
- **Low Coupling and High Cohesion:** Components interact through defined interfaces rather than sharing internal logic.

This structure supports parallel development within the team and aligns with our agile sprint-based implementation plan.

---

## 3. Architectural Assumptions

The design is based on the following assumptions:

1. The hub-provided file will follow a consistent and valid structure.
2. The system is intended for single-user use.
3. Deadline changes are manually updated rather than automatically synchronised.
4. Study activity contributions are measurable (e.g., time or quantity).
5. Performance requirements are moderate and suitable for an academic-scale system.

If these assumptions change, parts of the architecture may require revision.

---

## 4. Parts of the Structure Likely to Change Later

### Data Integration
File-based input may later be replaced by direct Hub API integration.

### Visualisation Layer
The Gantt chart and dashboard could migrate to different libraries or frameworks without affecting business logic due to layered separation.

### Notification Features
Future extensions may include automated reminders, email notifications, or calendar integration.

### Data Storage Strategy
Local storage may later evolve into cloud-based or synchronised database solutions.

---

This architectural structure prioritises modularity, clarity, and extensibility, ensuring the system can evolve while maintaining consistency with the original requirements.
