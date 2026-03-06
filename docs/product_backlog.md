# 2.7 Product Backlog

This product backlog is designed to give a team member a clear understanding of the tasks required to be completed when developing the Student Study Planner. The priority of each task and any dependencies on prior tasks are also listed, giving the developer a clear picture of what to prioritise.

| # | Development Task | Task Description | Priority | Dependencies | User Story |
|---|---|---|---|---|---|
| 1 | Implement UI for user login | Create username and password input fields, add a submit button, connect fields to authentication controller | High | None | System Requirement |
| 2 | Credential validation | Compare the inputted credentials with stored login data, compare password hashes, return true or false | High | None | System Requirement |
| 3 | False input handling | Implement an exception where an error message is returned if authentication fails; prevent login | High | None | System Requirement |
| 4 | Create classes for domains | Create domain classes: Module, Assessment, Task, StudyActivity, SemesterProfile. Assign getters/setters | High | None | System Requirement |
| 5 | Include file upload arguments | Restrict file type when uploading files to the system; return upload status. Accept `.csv` and `.json` | Medium | Task 4 | System Requirement |
| 6 | Integrate file parser | Implement a file parser to validate the file structure and extract important information such as deadlines and assessment titles | Medium | Task 5 | System Requirement |
| 7 | Assign objects to timetable | Create Module and Task domain objects and assign them to the SemesterProfile | Medium | Task 4 | System Requirement |
| 8 | Render imported data | Render the data imported by the user in the UI to confirm a successful import | High | Tasks 4, 5, 6, 7 | System Requirement |
| 9 | Validate the file type | Display an error message if the user uploads an empty or unsupported file | High | Task 5 | US-01 |
| 10 | Create study session duration field | Allow the user to select a task, enter a duration, and save it as a study session for that task | Medium | Task 4 | US-02 |
| 11 | Study session duration validation | If the user inputs a negative or invalid value, throw a validation error and prevent submission | Medium | Tasks 4, 10 | US-02 |
| 12 | Associate study session with task | Store cumulative hours of study sessions linked to a task | Low | Tasks 4, 10, 11 | US-02 |
| 13 | Introduce task progress calculator | Calculate task progress using `(Hours Completed / Required Hours) × 100` and display within the task UI | Low | Task 10 | US-02 |
| 14 | Approaching/overdue task reminder | Compare deadlines to system date and time; change the colour of the task UI based on imminence | Medium | Task 6 | All Users |
| 15 | Implement Gantt chart | Using a plotting library, produce a Gantt chart displaying a date axis, semester timeline, and task bars | High | Tasks 6, 10 | US-03 |
| 16 | Highlight task progress within Gantt chart | Represent start date, deadline, and status of completion within task bars | Low | Tasks 6, 10, 12, 15 | US-03 |
| 17 | Link subtasks to parent tasks | Ensure progress towards a parent task is updated when subtasks are completed | Medium | Task 11 | US-04 |
| 18 | Milestone creation | Allow the user to create milestones with a name, deadline, and linked tasks | Medium | Task 4 | US-06 |
| 19 | Milestone rendering on Gantt chart | Display milestones as diamond markers at their deadline position on the Gantt chart | Medium | Tasks 15, 18 | US-06 |
| 20 | Multi-task activity linking | Allow a single study activity to be linked to multiple tasks; update progress for all linked tasks | Medium | Tasks 4, 10, 11 | US-07 |
| 21 | Deadline update feature | Allow the user to edit task and assessment deadlines; recalculate dashboard status and re-render Gantt chart | Medium | Task 6 | US-08 |
| 22 | Dashboard deadline classification | Classify deadlines as completed, upcoming, or missed; display progress bars with colour-coded status | High | Tasks 6, 13 | US-05 |
| 23 | Circular dependency detection | Detect and reject circular task dependency chains | Medium | Task 4 | US-04 |
| 24 | Unit and integration tests | Implement test cases for core flows: import → task creation → activity logging → progress update | High | All | All |
