# iQube V2 API Specifications

## Overview
This document outlines the comprehensive REST API specifications for all microservices in the iQube project, detailing endpoints for authentication, ingestion, workflows, tasks, data view, and user action services.

### 1. Authentication Service API
#### 1.1 Login
- **Endpoint:** `POST /api/auth/login`
- **Description:** Authenticates a user and receives a JWT token.
- **Request Body:** 
  - `username`: string
  - `password`: string
- **Response:** 
  - `token`: string
  - `expiresIn`: number (seconds)

#### 1.2 Logout
- **Endpoint:** `POST /api/auth/logout`
- **Description:** Logs out the user by invalidating the token.

### 2. Ingestion Service API
#### 2.1 Upload Data
- **Endpoint:** `POST /api/ingest/data`
- **Description:** Uploads data for processing.
- **Request Body:** 
  - `file`: binary (multipart/form-data)
- **Response:** 
  - `status`: string
  - `message`: string

### 3. Workflow Service API
#### 3.1 Create Workflow
- **Endpoint:** `POST /api/workflows`
- **Description:** Creates a new workflow.
- **Request Body:** 
  - `name`: string
  - `description`: string
- **Response:** 
  - `workflowId`: string
  - `status`: string

### 4. Task Service API
#### 4.1 Create Task
- **Endpoint:** `POST /api/tasks`
- **Description:** Creates a new task within a workflow.
- **Request Body:** 
  - `workflowId`: string
  - `taskDetails`: object
- **Response:** 
  - `taskId`: string
  - `status`: string

#### 4.2 Get Task Status
- **Endpoint:** `GET /api/tasks/{taskId}`
- **Description:** Retrieves the status of a specific task.

### 5. Data View Service API
#### 5.1 Get Data
- **Endpoint:** `GET /api/data/view`
- **Description:** Fetches processed data.
- **Response:** 
  - `data`: array of objects

### 6. User Action Service API
#### 6.1 Record Action
- **Endpoint:** `POST /api/actions`
- **Description:** Records a user action in the system.
- **Request Body:** 
  - `userId`: string
  - `action`: string
- **Response:** 
  - `status`: string

## Conclusion
This document serves as a reference for developers working with the iQube microservices architecture. For further details, please refer to the corresponding service documentation.