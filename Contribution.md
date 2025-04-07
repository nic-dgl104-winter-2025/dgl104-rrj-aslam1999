# CONTRIBUTIONS.md

This document outlines my contributions to the Task Management System project, developed as part of our group effort. The project is a web-based application designed to manage tasks, leaves, and user roles (admin, team lead, and user) with a shared database.

## [Aslam Shaik]

### Role: Project Lead Developer(Team member)
### Contributions:
- **Project Foundation**:
  - Designed and implemented the initial structure of the entire Task Management System from scratch.
  - Set up the core PHP files, including session management, database connection (`includes/connection.php`), and foundational dashboards (`admin_dashboard.php`, `teamlead_dashboard.php`, `user_dashboard.php`).
  - Established the directory structure and integrated Bootstrap for consistent UI/UX across the application.
  - Created the initial database schema for the `admins` , `users` , `tasks` and `leaves` tables, ensuring compatibility across all user roles without requiring subsequent structural changes.

- **Admin Panel Enhancements**:
  - Developed and refined the admin task creation functionality (`create_task.php` in the admin folder), enabling admins to assign tasks to any user (team leads or regular users) with priority levels.
  - Improved the admin interface with dynamic user selection and role-based visibility, ensuring a seamless experience for task management.

- **Database Enhancements**:
  - Optimized the `tasks` table to support shared usage across admin, team lead, and user roles, maintaining columns like `uid`, `created_by`, `description`, `start_date`, `end_date`, `status`, and `priority`.
  - Ensured database consistency by aligning all task-related queries (e.g., in `create_task_teamlead.php`, `task.php`, and `update_status.php`) with the existing schema, avoiding the need for additional tables or columns.
  - Added sorting logic in `task.php` to prioritize urgent tasks, enhancing usability for end users.

- **General Improvements**:
  - Debugged and resolved session persistence issues across dashboards and task management pages, ensuring users remain logged in during navigation (e.g., fixed redirects to `user_login.php` in `update_status.php`).
  - Standardized alert messages with a consistent style (e.g., `....` suffix) across all dashboards and task-related files for a cohesive user experience.
  - Provided ongoing support to align team lead and user functionalities with the admin panel, such as fixing `create_task_teamlead.php` to match the working admin `create_task.php`.

---

## Notes
- This project was developed collaboratively, with each member building on the foundational work established by [Your Name].
- All code was written in PHP with MySQL, using Bootstrap for styling and jQuery for dynamic content loading.
- The database schema was kept unchanged after the initial setup by [Your Name], with subsequent enhancements handled through code adjustments.

---
