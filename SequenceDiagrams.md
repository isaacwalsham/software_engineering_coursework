# Sequence Diagrams

## User Story 01 (Happy Path)

```mermaid
    sequenceDiagram %% User Story 01 (Happy Path)
    participant UEA as UEA Academic Data Source
    participant User as Student (User Story 1)
    participant Login as Planner Login
    participant Auth as Authenticor 
    participant Planner as Study Planner System

    User->>Login: Input login credentials
    Login->>Auth: Validate credentials
    Auth-->>Login: Authorise Entry
    User->>Planner: Create New Timetable(Empty)
    Planner->>Planner: Save Timetable
    User->>UEA: Extract module and deadline information
    User-->>Planner: Insert Module and assessment data
    Planner->>Planner: Organise modules and deadlines within Timetable
    Planner-->>User: Display imported modules and deadlines
```

## User Story 01 (Unhappy Path 1, Login Error)

```mermaid
    sequenceDiagram %% User Story 01 (Unhappy Path 1, Login Error)
    participant User as Student
    participant Login as Planner Login
    participant Auth as Authenticor 
    participant Planner as Study Planner System

    User->>Login: Input incorrect login credentials
    Login->>Auth: Validate credentials (Throw Exception)
    Auth-->>Login: Unauthorise Entry
    %%User->>Planner: Create New Timetable(Empty)
    %%Planner->>Planner: Save Timetable
    %%User->>UEA: Extract module and deadline information
    %%User-->>Planner: Insert Module and assessment data
    %%Planner->>Planner: Organise modules and deadlines within Timetable
    %%Planner-->>User: Display imported modules and deadlines
```

## User Story 01 (Unhappy Path 2, Import Error)

```mermaid
    sequenceDiagram %% User Story 01 (Unhappy Path 2, Import Error)
    participant UEA as UEA Academic Data Source
    participant User as Student (User Story 1)
    participant Login as Planner Login
    participant Auth as Authenticor 
    participant Planner as Study Planner System

    User->>Login: Input login credentials
    Login->>Auth: Validate credentials
    Auth-->>Login: Authorise Entry
    User->>Planner: Create New Timetable(Empty)
    Planner->>Planner: Save Timetable
    User->>UEA: Extract module and deadline information
    User-->>Planner: Insert Module and assessment data
    Planner->>Planner: Throw Exception (Error Importing Data)
    Planner-->>User: Show Error code 
```

## User Story (03) (Happy Path)

```mermaid
    sequenceDiagram %% User Story 03 (Happy Path)
    participant UEA as UEA Academic Data Source
    participant User as Student (User Story 3)
    participant Login as Planner Login
    participant Auth as Authenticor 
    participant Planner as Study Planner System

    User->>Login: Input login credentials
    Login->>Auth: Validate credentials
    Auth-->>Login: Authorise Entry
    User->>Planner: Open existing Timetable
    Planner->>Planner: Load Timetable
    User->>Planner: Select Workload Dashboard / Gantt View
    Planner->>UEA: Retrieve module and assessment data
    UEA-->>Planner: Return module and deadline information
    Planner->>Planner: Retrieve saved tasks and dependencies
    Planner->>Planner: Calculate workload per week
    Planner->>Planner: Compute task dependency links
    Planner->>Planner: Calculate progress per module
    Planner-->>User: Display workload dashboard (busy periods)
    Planner-->>User: Render Gantt chart with tasks and dependencies
```

## User Story (05) (Happy Path)

```mermaid
    sequenceDiagram %% User Story 05 (Happy Path)
    participant UEA as UEA Academic Data Source
    participant User as Student (User Story 5)
    participant Login as Planner Login
    participant Auth as Authenticor 
    participant Planner as Study Planner System

    User->>Login: Input login credentials
    Login->>Auth: Validate credentials
    Auth-->>Login: Authorise Entry
    User->>Planner: Open existing Timetable
    Planner->>Planner: Load Timetable
    User->>Planner: Select Module Progress Dashboard
    Planner->>UEA: Retrieve module and assessment data
    UEA-->>Planner: Return module and deadline information
    Planner->>Planner: Retrieve saved task completion data
    Planner->>Planner: Calculate progress percentage per module
    Planner->>Planner: Compare progress against planned schedule
    Planner-->>User: Display progress percentage per module
    Planner-->>User: Highlight modules falling behind schedule
```
