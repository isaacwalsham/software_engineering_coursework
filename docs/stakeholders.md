# 2.6 Stakeholder Analysis

The Study Planner system involves five stakeholder groups whose needs, constraints, and objectives directly inform system requirements. Identifying these stakeholders ensures alignment between user needs, institutional objectives, and technical constraints.

---

## 1. Students (Primary Users)

Students are the primary stakeholders and the intended users of all system features. The system is designed to support students in organising, planning, and tracking their academic workload throughout a semester.

**Needs:**
- Load module, coursework, and deadline information from a defined file format
- Define and manage study tasks, milestones, and dependencies
- Log study activities and track measurable progress towards task completion
- View progress on a dashboard and Gantt chart visualisation

**Influence on requirements:**
- Drive usability design, system responsiveness, and clarity of visual feedback
- Require intuitive, human-readable error messages that explain corrective actions
- Need persistent data that survives across sessions without data loss

---

## 2. School of Computing Sciences (Client)

The School of Computing Sciences acts as the commissioning body. The Study Planner is initially intended for use within the School, with potential expansion to other schools considered in its design.

**Objectives:**
- Support structured academic planning across all year groups
- Encourage proactive study behaviour and reduce last-minute submissions
- Improve student deadline awareness and academic performance
- Explore potential future integration with institutional systems (UEA Hub)

**Influence on requirements:**
- Defines the expected structure of the data file exported by the Hub
- Requires the system to be maintainable and scalable beyond a single school
- Sets expectations around data validation, reliability, and long-term architectural consistency

---

## 3. Academic Staff and Module Organisers (Indirect)

Module organisers and academic staff are indirect stakeholders. While they do not directly use the system, their actions directly influence its operation. They define coursework assignments and assessment deadlines, and may change deadlines or grant extensions throughout the semester.

**Influence on requirements:**
- The system must support deadline updates without loss of existing student data
- Assessment information must be accurately represented in the system at all times
- The data model must be flexible enough to accommodate diverse assessment types including coursework, exams, and demonstrations

---

## 4. University IT Services / Hub System (External Technical)

University IT Services are external technical stakeholders. The Study Planner relies on module and deadline data provided through institutional systems on a per-student basis.

**Constraints introduced:**
- A defined and validated file format (`.csv` or `.json`) must be supported
- Uploaded data must be verified before it is persisted to the data store
- The architecture must remain open to future API-based integration with the Hub
- The system must not assume responsibility for the accuracy of data provided by the institution

---

## 5. Future Schools within UEA (Long-term)

Although initially developed for the School of Computing Sciences, the system may later be adopted by other schools within UEA. This future use case was considered during architectural design.

**Influence on design:**
- The data model must support flexible module structures not tied to Computing Sciences conventions
- Assessment modelling should be generalised to accommodate different assessment types across faculties
- The system architecture must support multi-school scalability without requiring core redesign

---

## Stakeholder Summary

| Stakeholder | Type | Primary Concern | Influence on System |
|---|---|---|---|
| Students | Primary User | Usability, progress visibility | Core feature set, UI design, error handling |
| School of Computing Sciences | Client | Academic planning, scalability | Data format, institutional requirements, maintainability |
| Academic Staff | Indirect | Accurate assessment representation | Deadline updates, flexible data modelling |
| University IT / Hub | External Technical | Data format, future API integration | File format specification, validation, architecture |
| Other UEA Schools | Future | Scalability and generalisation | Flexible data model, generalised assessment structures |
