# 1.1 Project Vision

## Background

University students are required to manage increasingly complex academic workloads. Coursework-heavy modules, overlapping deadlines, staged submissions, and independent study expectations demand a high level of planning and self-regulation. While institutional systems provide access to module information and submission portals, they do not provide structured support for personal workload management or progress monitoring.

Generic tools such as calendars, spreadsheets, and to-do lists do not capture academic dependencies, milestones, or the relationship between time spent studying and real progress. As a result, students often rely on fragmented systems that require manual updates and provide limited insight into whether they are genuinely on track.

The **Study Planner** is a web-based academic planning application designed to bridge this gap. Its purpose is to provide students with a structured environment in which module and assessment data can be imported, coursework can be decomposed into manageable tasks, dependencies can be defined, and study activities can be recorded and evaluated against measurable completion criteria.

---

## Project Goals

1. Enable UEA students to create a semester study plan by importing module, coursework, and deadline data from a structured institutional data file.
2. Support structured study planning through the creation of tasks, milestones, and task dependency relationships.
3. Allow students to record study activities and automatically track progress toward task completion using measurable criteria.
4. Provide clear visualisations — including a Gantt chart and progress dashboard — to improve student awareness of deadlines, workload distribution, and overall progress.
5. Classify deadlines dynamically as completed, upcoming, or missed, giving students immediate feedback on where attention is needed.

---

## Primary Users and Stakeholders

| Role | Description |
|---|---|
| **Students** (Primary Users) | UEA undergraduate and postgraduate students using the web application to manage their semester study planning |
| **School of Computing Sciences** | Commissioning body and initial system owner; potential future adopter across other UEA schools |
| **Module Organisers** | Indirect stakeholders who define assessment structures and deadlines that populate the system |
| **University IT / UEA Hub** | External technical stakeholder that generates the structured data file consumed by the system |

The system is initially intended for students within the School of Computing Sciences, with scalability to other schools considered in its design.

---

## Success Criteria

The Study Planner will be considered successful when the following conditions are met:

| # | Success Criterion |
|---|---|
| 1 | Students can log in and successfully create a semester profile by importing a valid UEA module data file |
| 2 | Tasks, milestones, and dependencies are correctly created, stored, and displayed in the Gantt chart |
| 3 | Recorded study activities update task progress accurately using the formula: `(Quantity Completed / Requirement) × 100` |
| 4 | The dashboard correctly classifies and displays completed, upcoming, and missed deadlines with progress bars |
| 5 | Students can identify at-risk deadlines immediately from the dashboard without navigating to individual module pages |

---

## 1.2 Problem Context and Motivation

Higher education increasingly emphasises independent learning and self-directed study. Students are expected to interpret assessment briefs, manage concurrent module demands, and allocate sufficient preparation time without continuous external structure. This shift places significant responsibility on students' organisational and planning skills.

This problem manifests in several ways:

- Overlapping deadlines are not easily visualised across modules
- Large coursework assignments are not systematically decomposed into structured subtasks
- Students struggle to determine whether recorded effort is sufficient to meet requirements
- Early warning signs of delayed progress are not clearly highlighted

These challenges are particularly evident among:

- **Second-year students** managing multiple programming-intensive modules
- **Final-year students** balancing dissertations, employment, and taught assessments
- **First-year students** adjusting to independent academic planning for the first time

If the Study Planner succeeds, it will support more informed academic decision-making, reduce cognitive overload, and provide measurable insight into progress toward deadlines. In doing so, the system contributes not only to task organisation but also to improved academic resilience and confidence.
