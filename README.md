# Student Management System

## Overview
A JavaFX-based application for managing educational resources, supporting Admin, Teacher, and Student roles. Features include user management, course handling, and task viewing, with PostgreSQL as the backend.

## Features
- **Authentication**: Login and registration with role-based access.
- **Admin**: Manage users, data, settings, and reports.
- **Teacher**: Manage courses, assignments, and students.
- **Student**: View courses, videos, and tasks.
- **Database**: PostgreSQL with CRUD operations.
- **GUI**: JavaFX with FXML and CSS styling.
- **OOP Principles**: Encapsulation (`Info`, `Database`), abstraction (`UserOperations`, `AbstractUserManager`), inheritance (`User` → `AdminUser`/`TeacherUser`/`StudentUser`), polymorphism (`UserManager` implements `UserOperations`).

## Setup
### Prerequisites
- Java JDK 17+
- JavaFX SDK
- PostgreSQL 17.4
- IntelliJ IDEA
- PostgreSQL JDBC Driver

### Database Setup
1. Install PostgreSQL and create a database `oop2`.
2. Set username `postgres`, password `z20102006`.
3. Import schema:
   ```bash
   psql -U postgres -d oop2 -f export.sql
   ```

### Project Setup
1. Import project into IntelliJ.
2. Configure JavaFX SDK: Add libraries to module path, set VM options:
   ```
   --module-path /path/to/javafx-sdk/lib --add-modules javafx.controls,javafx.fxml
   ```
3. Add PostgreSQL JDBC driver to dependencies.
4. Place FXML (`login.fxml`, etc.) and CSS (`style.css`, `designSTU.css`) files in `resources`.

## Running
1. Run `Main.java`.
2. Log in with test credentials (e.g., username: `testuser`, password: `password123`) or register a new user.
3. Navigate based on role:
   - **Admin**: Manage users, export data, view reports.
   - **Teacher**: Manage courses, add tasks.
   - **Student**: View courses, videos, tasks.

## Team
- [Team Member 1]
- [Team Member 2]
- [Team Member 3]
- [Team Member 4]
- [Team Member 5]

## License
For academic use only.