# Product Back Log

This product backlog is designed to give a team member a clear understanding of the tasks required to be completed when developing the Student Study planner, the priority of each task as well as which tasks are dependent on the completion of prior tasks are also listed giving the developer an idea of what to prioritise.

| Development task | Task Description | Priority/Value | Dependencies | User Story it relates to |
|------------------|------------------|---------------|--------------|--------------------------|
| 1 – Implement UI for user login | Create username & password input fields, add ‘submit’ button, connect fields to authentication controller | High | None | None (System Requirement) |
| 2 – Credential Validation | Compare the inputted credentials with stored login data, compare password hashes, return true or false | High | None | None (System Requirement) |
| 3 – False input handling | Implement an exception where an error message will be returned if the authentication fails, prevent login | High | None | None (System Requirement) |
| 4 – Create classes for domains | Create domain classes such as; Modules/Deadlines, Tasks, Study Sessions, Timetable. Assign getters/setters | High | None | None (System Requirement) |
| 5 – Include file upload arguments | Restrict file type when uploading files to system, return upload status. Accept files such as .csv | Medium | Development Task 4 | None (System Requirement) |
| 6 – Integrate File Parser | Implementing a file parser ensure the system can validate the file structure and extract important information for system functionality (deadlines, assessment titles etc.) | Medium | Development Task 5 | None (System Requirement) |
| 7 – Assign objects to Timetable | Create Module & Task Domain Objects and assign them to the Timetable | Medium | Development Task 4 | None (System Requirement) |
| 8 – Render imported data | Render the data imported by user in UI to represent a successful import | High | Development Task 4,5,6,7 | None (System Requirement) |
| 9 - Validate the file type | Display an error message should the user upload an empty file/unsupported file | High | Development Task 5 | User Story 01 |
| 10 – Create Study session duration field | Allow the user to select a task, enter a duration and save as a study session for said task | Medium | Development Task 4 | User Story 02 |
| 11 – Study session duration validation | Should the user input a negative value or invalid value, throw an exception error, prevent user from submitting invalid duration | Medium | Development Task 4, 10 | User Story 02 |
| 12 – Associate Study session with task | Store cumulative hours of study sessions | Low | Development Task 4,10,11 | User Story 02 |
| 13 – Introduce task progress calculator | To represent task progress (Hours Completed / Required Hours) × 100 Store within Task UI | Low | Development Task 10 | User Story 02 |
| 14 – Approaching/Overdue Task Reminder | Implement a method to compare deadlines to system date/time and change colour of Task UI based on imminence | Medium | Development Task 6 | All Users |
| 15 – Implement Gantt chart | Using plotting libraries produce a Gantt chart which displays a date axis, semester timeline and task bars | High | Development Task 6, 10 | User Story 03 |
| 16 – Highlight task progress within Gantt chart | Represent start date, deadline and status of completion | Low | Development Task 6, 10, 12, 15 | User Story 03 |
| 17 – Link Subtasks to Parent tasks | Ensure progress towards parent task is updated when subtasks are completed and update progress of Parent task | Medium | Development Task 11 | User Story 04 |
