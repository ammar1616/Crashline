﻿# Crashline

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Prerequisites](#prerequisites)
4. [Getting Started](#getting-started)
5. [Project Structure](#project-structure)
6. [Usage](#usage)
    - [User Authentication](#user-authentication)
    - [Creating Posts](#creating-posts)
    - [Managing Profile](#managing-profile)
7. [Testing](#testing)
8. [Contributing](#contributing)


## Overview

Creashline is a social media platform that allows users to connect, share content, and engage with each other. Whether you're sharing photos, videos, or thoughts, Creashline provides a seamless experience for users to express themselves and connect with others in a meaningful way.


## Features

1. **User Authentication:**
   - Allow users to register accounts and log in securely.
   - Implement JWT token-based authentication for secure access to user-specific features.

2. **Post Creation and Interaction:**
   - Enable users to create, view, update, and delete posts.
   - Support features like liking posts and commenting on them.

3. **Profile Management:**
   - Allow users to view and update their profiles, including changing profile pictures and updating personal information.
   - Implement features like following other users and viewing followers/followings.


## Prerequisites

Ensure you have the following installed:

- Node.js
- npm (Node Package Manager)
- MongoDB database


## Getting Started

Follow these steps to set up and run the Creashline app locally:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/ammar1616/Crashline.git
   ```

2. **Install Dependencies:**
   ```bash
   npm install
   ```

3. **Set Up Environment Variables:**
   - Create a `.env` file based on the `.env.example` template.
   - Update the `.env` file with your configuration details.

4. **Start the Server:**
   ```bash
   npm start
   ```

5. **Access the App:**
   - Open your web browser and go to `https://crashline.vercel.app/` to access the Creashline app.


## Project Structure

The project follows a modular structure:

- **controllers:** Handle business logic for different routes.
- **middlewares:** Custom middleware functions, including authentication and error handling.
- **validations:** Data validation using libraries like Joi.
- **routes:** Define API routes for managing authentication, posts, and profiles.
- **startup:** Initialization scripts for setting up the server and database connections.


## Usage

### User Authentication

- **Description:** Register new users and authenticate existing ones.
- **Endpoints:**
  - `POST /api/auth/register`: Register a new user.
  - `POST /api/auth/login`: Log in an existing user.
- **Authorization:** Not required.
- **Request (`req`) Object:**
  - For registration:
    ```json
    {
      "name": "John Doe",
      "email": "john@example.com",
      "password": "password"
    }
    ```
  - For login:
    ```json
    {
      "email": "john@example.com",
      "password": "password"
    }
    ```
- **Response (`res`) Object:**  
  - **Status Code:** 200 OK
  - **Body (on successful login):**
    ```json
    {
      "token": "your_jwt_token_here"
    }
    ```

### Creating Posts

- **Description:** Allow users to create, view, update, and delete posts.
- **Endpoints:**
  - `POST /api/posts`: Create a new post.
  - `GET /api/posts`: View all posts.
  - `GET /api/posts/:postId`: View a specific post.
  - `PUT /api/posts/:postId`: Update a post.
  - `DELETE /api/posts/:postId`: Delete a post.
- **Authorization:** Required (JWT token).
- **Request (`req`) Object:**
  - For creating a post:
    ```json
    {
      "text": "This is a new post",
      "imageUrl": "https://example.com/image.jpg"
    }
    ```
  - For updating a post:
    ```json
    {
      "text": "Updated post content"
    }
    ```
- **Response (`res`) Object:**  
  - **Status Code:** 200 OK
  - **Body (on successful operation):**
    ```json
    {
      "message": "Post created/updated/deleted successfully!"
    }
    ```

### Managing Profile

- **Description:** Enable users to manage their profiles, including updating information and interacting with other users.
- **Endpoints:**
  - `GET /api/profiles/:userId`: View user profile.
  - `PUT /api/profiles/:userId/picture`: Update profile picture.
  - `PUT /api/profiles/:userId/password`: Change password.
  - `PUT /api/profiles/:userId/name`: Change name.
  - `PUT /api/profiles/:followerId/follow`: Follow/unfollow a user.
  - `GET /api/profiles/:userId/followers`: View followers.
  - `GET /api/profiles/:userId/followings`: View followings.
- **Authorization:** Required (JWT token).
- **Request (`req`) Object:**  
  - For updating profile picture or password:
    ```json
    {
      "newProfilePictureUrl": "https://example.com/new_image.jpg"
    }
    ```
  - For changing name:
    ```json
    {
      "newName": "New Name"
    }
    ```
- **Response (`res`) Object:**  
  - **Status Code:** 200 OK
  - **Body (on successful operation):**
    ```json
    {
      "message": "Profile updated successfully!"
    }
    ```


## Testing

To run tests, execute the following command:

```bash
npm test
```

The testing suite includes unit tests for individual components and integration tests for API endpoints, ensuring reliability and functionality.


## Contributing

We welcome contributions from the community! Follow these guidelines to contribute to the Creashline project:

1. Fork the repository.
2. Create a new branch.
3. Make your changes and commit.
4. Submit a pull request.

Thank you for contributing to make Crashline better!
