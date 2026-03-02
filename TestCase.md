Test Case US-01: Import UEA Modules
Preconditions: Valid UEA CSV file with modules, codes, deadlines in database.
Steps:
•	Navigate to import screen.
•	Upload valid file.
•	Submit import.
Expected:
•	Modules parse correctly.
•	Redirect to preview within 3 seconds.

Test Case US-02: Log Study Session
Preconditions: Valid credentials logged in; modules imported.
Steps:
•	Select module/task.
•	Enter duration and date.
•	Submit session.
Expected:
•	Session saves to database.
•	Total time updates instantly.

Test Case US-05: View Progress Dashboard
Preconditions: Study sessions logged; estimates set per module.
Steps:
•	Access dashboard.
•	View module progress.
Expected:
•	Percentage displays (e.g., 60%).
•	Behind tasks highlighted.
