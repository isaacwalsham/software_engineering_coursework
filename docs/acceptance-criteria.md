# Acceptance Criteria

## Story: [US-01/Steve Beaton]

Main Aim: Steve wants the ability to import his modules and deadlines from UEA's database, so that he can plan his semester.

Happy Path:

  Given the user is logged into the system,
  When the user uploads a UEA data file,
  Then data syncs with planner, displaying modules and assessment deadlines

Unhappy Path:
  
  Given the user uploads an empty file/invalid file type,
  When the user attempts to import the data from file,
  Then system throws and exception causing error message to be displayed (no data is added)
  

## Story: [US-02/ Michelle Lush]

Main Aim: Michelle aims to log her study sessions against coursework tasks, allowing her to track her progress towards task completion. 

Happy Path:

  Given a task exists,
  When the user logs a study session with a duration for a task,
  Then the total time spent on said task is updated

Unhappy Path:

  Given an invalid duration is entered e.g. a negative value,
  When the user attempts to submit invalid time,
  Then an error message is displayed and the time is not recorded

## Story: [US-03 Ben]

Main Aim: Ben wishes to display his work throughout the semester on a gannt chart, granting him the ability to see where he may be falling behind in his studies.

Happy Path:

  Given the user has uploaded a data file contianing UEA's modules and tasks associated
  When the student selects Gantt chart view option
  Then 

Unhappy Path:

  Given ...
  When ...
  Then ...
  
## Story: [US-04]

Main Aim: 

Happy Path:

  Given ...
  When ...
  Then ...

Unhappy Path:

  Given ...
  When ...
  Then ...
  
