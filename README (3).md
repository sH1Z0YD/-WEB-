# University Management System Database

## Domain Description

This database is a University Management System.

It manages:

- Students
- Professors
- Departments
- Courses
- Classrooms
- Schedules
- Enrollments
- Student clubs

The system also stores relationships between students and courses, and students and clubs.

---

# Database & Schema Names

| Type | Name |
|---|---|
| Database | `university_db` |
| Schema | `university` |

---

# Design Decisions

## Generated Columns

`full_name` is generated automatically from:

```sql
first_name || ' ' || last_name
```

Why:
- avoids duplicate data
- easier to read

---

## Many-to-Many Relationship

Students can join many clubs.

Clubs can have many students.

This is implemented using:

```sql
student_club_members
```

---

## CHECK Constraints

Used to prevent invalid data.

Examples:

```sql
CHECK (gpa >= 0)
CHECK (course_fee >= 0)
CHECK (gender IN ('M','F','Other'))
```

---

## ALTER TABLE Usage

Used to modify existing tables.

Examples:
- added `phone_number`
- renamed `lesson_day` → `weekday`
- added default value to `course_fee`

---

## Roles & Permissions

Two roles were created:

| Role | Access |
|---|---|
| `university_readonly` | SELECT only |
| `university_editor` | INSERT/UPDATE |

---

# Run Instructions

## 1. Create database

```sql
CREATE DATABASE university_db;
```

---

## 2. Connect to database

```sql
\c university_db
```

---

## 3. Run SQL script

Execute the whole script in PostgreSQL.

The script will:
- create schema
- create tables
- add constraints
- insert sample data
- create roles

---

## 4. Check data

```sql
SELECT * FROM university.students;
SELECT * FROM university.courses;
SELECT * FROM university.enrollments;
```

---

# Main Features

- CREATE TABLE
- ALTER TABLE
- FOREIGN KEYS
- CHECK constraints
- GENERATED columns
- MANY-TO-MANY relationships
- TRANSACTIONS
- ROLES & GRANTS

---

# Conclusion

This project is a PostgreSQL university database system that demonstrates:

- relational database design
- normalization
- constraints
- relationships
- transactions
- access control
