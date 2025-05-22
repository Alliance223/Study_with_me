# Study With Me - Backend API Documentation

## Introduction

This document outlines the API endpoints for the backend service of the "Study With Me" application.

## Base URL

All endpoints are relative to the base URL: `/api/v1`

## Endpoints

### 1. User Authentication

#### 1.1. Register a new user

- **Endpoint:** `POST /users/register`
- **Description:** Registers a new user account.
- **Request Body:**
    ```json
    {
        "username": "string",
        "email": "string",
        "password": "string"
    }
    ```
- **Response:**
    ```json
    {
        "message": "User registered successfully",
        "user": {
            "id": "integer",
            "username": "string",
            "email": "string"
        }
    }
    ```

#### 1.2. Login

- **Endpoint:** `POST /users/login`
- **Description:** Logs in an existing user.
- **Request Body:**
    ```json
    {
        "email": "string",
        "password": "string"
    }
    ```
- **Response:**
    ```json
    {
        "message": "Login successful",
        "token": "string"
    }
    ```

### 2. Study Sessions

#### 2.1. Create a new study session

- **Endpoint:** `POST /sessions`
- **Description:** Creates a new study session. Requires authentication.
- **Request Headers:**
    ```
    Authorization: Bearer <token>
    ```
- **Request Body:**
    ```json
    {
        "title": "string",
        "description": "string",
        "start_time": "datetime",
        "end_time": "datetime"
    }
    ```
- **Response:**
    ```json
    {
        "message": "Study session created successfully",
        "session": {
            "id": "integer",
            "title": "string",
            "description": "string",
            "start_time": "datetime",
            "end_time": "datetime",
            "user_id": "integer"
        }
    }
    ```

#### 2.2. Get all study sessions

- **Endpoint:** `GET /sessions`
- **Description:** Retrieves all study sessions.
- **Response:**
    ```json
    [
        {
            "id": "integer",
            "title": "string",
            "description": "string",
            "start_time": "datetime",
            "end_time": "datetime",
            "user_id": "integer"
        }
    ]
    ```

#### 2.3. Get a specific study session

- **Endpoint:** `GET /sessions/{id}`
- **Description:** Retrieves a specific study session by its ID.
- **Response:**
    ```json
    {
        "id": "integer",
        "title": "string",
        "description": "string",
        "start_time": "datetime",
        "end_time": "datetime",
        "user_id": "integer"
    }
    ```

#### 2.4. Update a study session

- **Endpoint:** `PUT /sessions/{id}`
- **Description:** Updates a specific study session. Requires authentication.
- **Request Headers:**
    ```
    Authorization: Bearer <token>
    ```
- **Request Body:**
    ```json
    {
        "title": "string",
        "description": "string",
        "start_time": "datetime",
        "end_time": "datetime"
    }
    ```
- **Response:**
    ```json
    {
        "message": "Study session updated successfully",
        "session": {
            "id": "integer",
            "title": "string",
            "description": "string",
            "start_time": "datetime",
            "end_time": "datetime",
            "user_id": "integer"
        }
    }
    ```

#### 2.5. Delete a study session

- **Endpoint:** `DELETE /sessions/{id}`
- **Description:** Deletes a specific study session. Requires authentication.
- **Request Headers:**
    ```
    Authorization: Bearer <token>
    ```
- **Response:**
    ```json
    {
        "message": "Study session deleted successfully"
    }
    ```

### 3. Pomodoro Timers

#### 3.1. Create a new pomodoro timer

- **Endpoint:** `POST /pomodoros`
- **Description:** Creates a new pomodoro timer. Requires authentication.
- **Request Headers:**
    ```
    Authorization: Bearer <token>
    ```
- **Request Body:**
    ```json
    {
        "study_duration": "integer",
        "break_duration": "integer",
        "session_id": "integer"
    }
    ```
- **Response:**
    ```json
    {
        "message": "Pomodoro timer created successfully",
        "pomodoro": {
            "id": "integer",
            "study_duration": "integer",
            "break_duration": "integer",
            "session_id": "integer"
        }
    }
    ```

#### 3.2. Get all pomodoro timers for a session

- **Endpoint:** `GET /pomodoros?session_id={session_id}`
- **Description:** Retrieves all pomodoro timers for a specific study session.
- **Response:**
    ```json
    [
        {
            "id": "integer",
            "study_duration": "integer",
            "break_duration": "integer",
            "session_id": "integer"
        }
    ]
    ```

#### 3.3. Get a specific pomodoro timer

- **Endpoint:** `GET /pomodoros/{id}`
- **Description:** Retrieves a specific pomodoro timer by its ID.
- **Response:**
    ```json
    {
        "id": "integer",
        "study_duration": "integer",
        "break_duration": "integer",
        "session_id": "integer"
    }
    ```

#### 3.4. Update a pomodoro timer

- **Endpoint:** `PUT /pomodoros/{id}`
- **Description:** Updates a specific pomodoro timer. Requires authentication.
- **Request Headers:**
    ```
    Authorization: Bearer <token>
    ```
- **Request Body:**
    ```json
    {
        "study_duration": "integer",
        "break_duration": "integer"
    }
    ```
- **Response:**
    ```json
    {
        "message": "Pomodoro timer updated successfully",
        "pomodoro": {
            "id": "integer",
            "study_duration": "integer",
            "break_duration": "integer",
            "session_id": "integer"
        }
    }
    ```

#### 3.5. Delete a pomodoro timer

- **Endpoint:** `DELETE /pomodoros/{id}`
- **Description:** Deletes a specific pomodoro timer. Requires authentication.
- **Request Headers:**
    ```
    Authorization: Bearer <token>
    ```
- **Response:**
    ```json
    {
        "message": "Pomodoro timer deleted successfully"
    }
    ```

## Authentication

Most endpoints require authentication using a Bearer token.  You can obtain a token by registering a new user or logging in.  Include the token in the `Authorization` header of your requests.

## Error Handling

The API returns standard HTTP status codes to indicate the success or failure of a request.  Error responses typically include a JSON body with a `message` field providing more details about the error.

## Conclusion
This API documentation provides an overview of the endpoints available in the "Study With Me" backend service.  For further details or specific use cases, please refer to the codebase or contact the development team.