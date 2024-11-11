# Grocery Checklist Full Stack Application

## Overview

The **Grocery Checklist Application** is a full-stack web app that allows users to create, update, and delete grocery checklists. Users can authenticate themselves and manage their checklists using a user-specific backend and frontend built with React. This project is designed to help users track grocery items and mark them as completed.

The frontend is hosted on **GitHub Pages**, and can be accessed at the following link:

[https://ijlal321.github.io/basic-full-stack-app](https://ijlal321.github.io/basic-full-stack-app)


## Features

- **User Authentication**: Users can sign up, log in, and maintain their own grocery checklists.
- **CRUD Operations for Grocery Items**: Users can create, read, update, and delete grocery items in their checklist.
- **Completion Toggle**: Users can mark items as completed or incomplete, and it will be reflected in the UI.
- **Persistent Data**: The app persists data using a SQLite database on the backend.

## Tech Stack

- **Frontend**: 
  - React
  - Axios (for API calls)
  - React Router (for routing)

- **Backend**:
  - Node.js
  - Express
  - SQLite (for data storage)
  - CORS (for handling cross-origin requests)

## Folder Structure

```
/frontend             # React frontend application
    /src
    /components
    /App.js            # Main component
    /Login.js          # Login page
    /Signup.js         # Signup page
    /Grocries.js       # Grocery checklist component
/backend              # Backend application
    /server.js         # Express server
    /db.js             # Database setup
    /models.js         # Database models
    /controllers       # API routes and controllers
    /config            # Configuration files
```

## Backend Setup

### 1. Install Dependencies

In the backend folder, run the following command to install the required dependencies:

```bash
npm install express sqlite3 cors
```

### 2. Set Up Database

The SQLite database stores user and checklist data. Here’s the schema:

- **Users Table**: Stores information about users.
  - `id`: Integer, primary key
  - `name`: String
  - `password`: String (hashed)

- **Checklist Table**: Stores grocery checklist items.
  - `id`: Integer, primary key
  - `user_id`: Integer, foreign key referencing Users table
  - `name`: String (grocery item name)
  - `completed`: Boolean (true if the item is completed, false otherwise)

### 3. API Endpoints

#### User Authentication
- **POST `/users/signup`**: Registers a new user with a name and password.
- **POST `/users/login`**: Authenticates the user with their credentials and returns a session token.

#### Checklist Operations
- **GET `/users/:userId/checklist`**: Fetches all grocery items for the user with `userId`.
- **POST `/users/:userId/checklist`**: Creates a new grocery item for the user.
- **DELETE `/users/:userId/checklist/:id`**: Deletes the grocery item with the specified `id` for the user.
- **PATCH `/users/:userId/checklist/:id/complete`**: Marks a grocery item as completed.
- **PATCH `/users/:userId/checklist/:id/incomplete`**: Marks a grocery item as incomplete.

### 4. Run the Backend

After setting up the backend, run the following command to start the server:

```bash
node server.js
```

The backend will run on `http://localhost:5000`.

---

## How the Application Works

### User Authentication

- The frontend provides **login** and **signup** pages.
- When the user logs in, a session token is generated on the backend and returned to the frontend.
- The token is stored locally (e.g., in `localStorage` or `sessionStorage`) and is sent with subsequent API requests to authenticate the user.

### Grocery Checklist Operations

- The frontend uses **Axios** to make API calls to the backend:
  - **GET `/users/:userId/checklist`**: Fetches the grocery list for the logged-in user.
  - **POST `/users/:userId/checklist`**: Adds a new item to the grocery list.
  - **PATCH `/users/:userId/checklist/:id/complete`**: Marks an item as completed.
  - **DELETE `/users/:userId/checklist/:id`**: Deletes an item from the list.

### Data Persistence

- All data is stored in a **SQLite** database on the backend, including user information and the grocery checklist items.
- The data is persisted between app sessions, so the user's list remains intact after they log out and log back in.

---

## Conclusion

This project demonstrates how to build a full-stack grocery checklist application with user authentication and CRUD operations for managing a checklist. It uses React for the frontend, Node.js with Express for the backend, and SQLite for data storage. The frontend is deployed on GitHub Pages, while the backend can be hosted on any platform of your choice.
