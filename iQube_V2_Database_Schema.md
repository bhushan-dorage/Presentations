# iQube V2 Database Schema Design

## Overview
This document outlines the database schema design for the iQube V2 workflow system. The schema includes all necessary tables, relationships, indexes, constraints, and security considerations to ensure an efficient and secure database environment.

## Tables
### 1. Users
- **user_id** (PK): Unique identifier for each user.
- **username**: Unique username for user login.
- **password_hash**: Securely hashed password.
- **email**: User's email address.
- **created_at**: Timestamp of user creation.

### 2. Workflows
- **workflow_id** (PK): Unique identifier for each workflow.
- **name**: The name of the workflow.
- **description**: A brief description of the workflow.
- **created_by** (FK): References Users(user_id).
- **created_at**: Timestamp of workflow creation.

### 3. Tasks
- **task_id** (PK): Unique identifier for each task.
- **workflow_id** (FK): References Workflows(workflow_id).
- **title**: Title of the task.
- **status**: Current status of the task (e.g., Pending, In Progress, Completed).
- **assigned_to** (FK): References Users(user_id).
- **due_date**: Due date for the task.

### 4. Comments
- **comment_id** (PK): Unique identifier for each comment.
- **task_id** (FK): References Tasks(task_id).
- **user_id** (FK): References Users(user_id).
- **content**: Comment text.
- **created_at**: Timestamp of comment creation.

## Relationships
- One-to-Many between Users and Workflows (One user can create many workflows).
- One-to-Many between Workflows and Tasks (One workflow can contain many tasks).
- One-to-Many between Users and Comments (One user can make many comments).
- One-to-Many between Tasks and Comments (One task can have many comments).

## Indexes
- **Users**: An index on `username` to optimize login queries.
- **Workflows**: An index on `created_by` to quickly fetch workflows by user.
- **Tasks**: An index on `workflow_id` to speed up task retrieval for specific workflows.

## Constraints
- **Unique Constraints**: Ensure unique usernames and emails in the Users table.
- **Foreign Key Constraints**: Properly enforced relations between tables using foreign keys.
- **Not Null Constraints**: Essential fields such as `username`, `email`, and `name` cannot be null, ensuring data integrity.

## Security Considerations
1. **Data Encryption**: Sensitive information like passwords should be hashed and possibly encrypted.
2. **Access Control**: Implement role-based access controls (RBAC) to restrict access to the database based on user roles.
3. **SQL Injection Prevention**: Use parameterized queries to prevent SQL injection attacks.
4. **Regular Audits**: Conduct regular audits of the database security and user access logs to identify potential threats.

## Conclusion
The database schema outlined above is designed to support the needs of the iQube V2 workflow system, ensuring both functionality and security in the management of user and workflow data.