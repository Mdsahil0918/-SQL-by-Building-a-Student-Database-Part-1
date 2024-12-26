# Student Database Insert Script

This Bash script is designed to read data from `courses.csv` and `students.csv` files and insert it into a PostgreSQL database called `students`. It inserts information into the `students`, `majors`, `courses`, and `majors_courses` tables.

## Features:
- Clears existing data in the `students`, `majors`, `courses`, and `majors_courses` tables.
- Inserts new majors and courses if they don't already exist in the database.
- Inserts student information, linking each student to their major and GPA.

## How It Works:
1. **Courses and Majors**: 
   - Reads data from `courses.csv` file.
   - For each major, it checks if the major already exists in the `majors` table. If not, it inserts the major.
   - Then, it checks if the course already exists in the `courses` table. If not, it inserts the course.
   - Links each major with its respective courses in the `majors_courses` table.

2. **Students**: 
   - Reads data from `students.csv` file.
   - For each student, it checks if the major exists in the `majors` table. If not, it assigns `null` for the major.
   - Inserts the student data, including their first name, last name, GPA, and associated major ID.

## Prerequisites:
- PostgreSQL should be installed and running.
- A database named `students` should exist with the following tables:
  - `students`: Contains `first_name`, `last_name`, `major_id`, and `gpa`.
  - `majors`: Contains `major_id` and `major`.
  - `courses`: Contains `course_id` and `course`.
  - `majors_courses`: A join table linking majors and courses (`major_id`, `course_id`).
- Ensure the `freecodecamp` user has appropriate permissions to interact with the database.

## How to Use:
1. Place the `courses.csv` and `students.csv` files in the same directory as this script.
2. Run the script using the following command:
   ```bash
   ./insert_data.sh
