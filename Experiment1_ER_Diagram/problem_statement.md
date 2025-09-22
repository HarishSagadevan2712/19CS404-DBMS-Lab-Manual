# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

*Business Context:*  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

*Requirements:*  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
![Harish S (212224110022) (3)_page-0001](https://github.com/user-attachments/assets/a5a0b84f-0624-48a8-a199-f8e355ba28d7)


### Entities and Attributes

| Entity   | Attributes (PK, FK)                      | Notes |
|----------|------------------------------------------|-------|
| Member   | MemberID (PK), Name, MembershipType, StartDate | Registers in gym |
| Program  | ProgramID (PK), ProgramName, Duration     | e.g., Yoga, Zumba |
| Trainer  | TrainerID (PK), Name, Specialization      | Assigned to programs |
| Session  | SessionID (PK), Date, Time, MemberID (FK), TrainerID (FK) | Personal training |
| Attendance | AttendanceID (PK), SessionID (FK), Status | Tracks presence |
| Payment  | PaymentID (PK), MemberID (FK), Amount, Date, Type | Membership or session |

### Relationships and Constraints

| Relationship               | Cardinality | Participation | Notes |
|----------------------------|-------------|---------------|-------|
| Member – Program           | M:N         | Total (Member) | A member can join many programs |
| Program – Trainer          | M:N         | Partial        | A program can have multiple trainers |
| Member – Session           | 1:M         | Partial        | A member books many sessions |
| Trainer – Session          | 1:M         | Partial        | One trainer handles many sessions |
| Session – Attendance       | 1:1         | Total          | Attendance recorded for each session |
| Member – Payment           | 1:M         | Total          | Payments linked to members |

### Assumptions
- A member must belong to at least one program.  
- A trainer may be associated with multiple programs.  
- Payments can be for memberships or personal sessions.  

---
