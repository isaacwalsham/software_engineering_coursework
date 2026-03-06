# 3.6 Design Rationale and Anticipated Evolution

This document captures the key architectural reasoning behind the Study Planner system. It summarises how requirements influenced the system structure, why responsibilities are separated as they are, the assumptions made during design, and which parts of the architecture are most likely to evolve.

---

## How Requirements Influenced the System Structure

### Loading Module and Deadline Data

The requirement to load module, coursework, and deadline information from a defined file format directly influenced the decision to introduce a dedicated `FileParser` service class. This separates external input handling from core domain logic, meaning the file format can change — for example, from a `.csv` file to a live Hub API — without affecting task management, progress calculation, or dashboard functionality. Validation logic is also isolated here, keeping domain classes free of input-handling concerns.

### Task Dependencies

Since tasks can depend on other tasks, `Task` was structured as a core domain entity with its own dependency collection, and dependency validation was centralised within a dedicated `DependencyChecker` service. This ensures that business rules — such as cycle detection — are enforced consistently and are not duplicated or embedded in the user interface or controller layer.

### Activity-Based Progress Tracking

Activities contribute toward task completion, so `StudyActivity` was modelled as a separate entity from `Task`. Task progress is calculated dynamically by the `ProgressCalculator` service from linked activities, rather than being stored as a fixed value. This avoids data duplication, maintains consistency across the system, and supports flexible progress metrics (e.g. hours studied, pages written, requirements completed).

### Dashboard and Deadline Classification

The requirement to categorise deadlines as completed, upcoming, or missed influenced the introduction of a dedicated `Dashboard` service that handles time-based evaluation separately from presentation logic. This separation means the classification rules can be extended — for example, to support email reminders or push notifications — without modifying the frontend rendering code.

---

## Why Responsibilities Are Separated This Way

Responsibilities are separated according to established software engineering principles:

- **Separation of Concerns** — Data handling, business logic, and presentation logic are isolated into distinct layers. Each layer can be modified or tested independently without affecting the others.
- **Single Responsibility Principle** — Each class and service has one clearly defined purpose: `FileParser` handles input, `ProgressCalculator` handles progress, `DependencyChecker` handles graph validation, `Dashboard` handles deadline classification.
- **Low Coupling, High Cohesion** — Components interact through defined interfaces rather than sharing internal state. This reduces the risk of unintended side effects when one component changes.
- **Testability** — Stateless service classes (`FileParser`, `ProgressCalculator`, `DependencyChecker`) can be unit tested in complete isolation, which directly supports the testing requirements in Sprint 1 and Sprint 2.

This structure also supports parallel development across the team. Frontend and backend work can proceed simultaneously against an agreed API contract, and individual services can be developed and tested independently before integration.

---

## Architectural Assumptions

The design is based on the following assumptions. If any of these change, the affected parts of the architecture are noted.

| # | Assumption | Impact if Changed |
|---|---|---|
| 1 | The hub-provided file follows a consistent and valid structure | `FileParser` validation rules would need updating; potentially significant if format changes completely |
| 2 | The system is intended for single-user use per session | Multi-user support would require authentication, session management, and data isolation |
| 3 | Deadline changes are applied manually by the student | Automatic synchronisation would require a live API integration with the Hub |
| 4 | Study activity contributions are measurable quantities (e.g. hours, pages) | Abstract or qualitative progress criteria would require changes to `ProgressCalculator` |
| 5 | Performance requirements are moderate and suitable for an academic-scale single-user system | High concurrency or institutional-scale deployment would require infrastructure changes |

---

## Parts of the Architecture Likely to Evolve

### Data Integration
File-based input is the initial approach for v1. If the Study Planner experiment is successful, the brief explicitly anticipates future integration with the Hub via a live API. The `FileParser` service is designed to be replaceable — swapping it for an API client would not require changes to domain classes or the dashboard.

### Visualisation Layer
The Gantt chart and dashboard are rendered in the presentation layer and consume data from the application layer via REST API calls. Because no business logic resides in the frontend, the visualisation library can be replaced or upgraded without affecting domain logic. For example, moving from a custom SVG renderer to a full charting library such as Chart.js would require only frontend changes.

### Notification Features
The current implementation highlights overdue and approaching tasks visually within the dashboard. Future extensions could include automated push notifications, email reminders, or calendar integration with Google, Apple, or Microsoft services. The `Dashboard` classification logic is already separated from presentation, making this extension straightforward.

### Data Storage Strategy
Sprint 1 uses a file-based JSON store for simplicity and rapid development. Sprint 2 may migrate to SQLite if relational querying of tasks, activities, and dependencies becomes necessary. The data layer is accessed only through the application layer, so storage changes do not propagate to the frontend.

### Multi-School Support
The data model uses generalised module and assessment structures that are not tied to Computing Sciences-specific formats. Extending the system to support other UEA schools would primarily require updates to the `FileParser` to handle different hub file structures, with no changes needed to core domain logic.
