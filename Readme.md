# Authentication API with Actix Web and MongoDB

Welcome to the Authentication API project! This API is built using **Actix Web** and **MongoDB**, providing a seamless way to handle user authentication, profile management, and password resets.

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Prerequisites](#prerequisites)
4. [Project Structure](#project-structure)
5. [Environment Setup](#environment-setup)
6. [Running the Application](#running-the-application)
7. [API Endpoints](#api-endpoints)
8. [Testing the API](#testing-the-api)
9. [Troubleshooting](#troubleshooting)
10. [License](#license)

## Overview

This project implements a RESTful authentication API that allows users to register, log in, manage their profiles, and reset their passwords securely. JWT (JSON Web Token) is used for authentication to ensure secure access.

## Features

- User Registration
- User Login
- Get User Profile
- Edit User Profile
- Delete User Account
- Forgot Password functionality
- Password Reset functionality

## Prerequisites

Before you start, make sure you have the following installed:

- [Rust](https://www.rust-lang.org/tools/install)
- [MongoDB](https://www.mongodb.com/try/download/community)
- [Cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html)

## Project Structure

Here's an overview of the project's structure:

api_with_mongo/
├── src/
│   ├── handlers/
│   │   ├── mod.rs  
│   │   ├── auth.rs               # Authentication logic
│   │   ├── profile.rs            # Profile management logic
│   │   └── reset_password.rs      # Password reset logic
│   ├── models/
│   │   ├── mod.rs               # User data model
│   │   └── users.rs         # Other data model (if needed)
│   ├── routes/
│   │   ├── auth_routes.rs        # Authentication route definitions
│   │   ├── profile_routes.rs      # Profile route definitions
│   │   └── mod.rs                # General route definitions
│   ├── db.rs                      # Database connection and setup
│   ├── main.rs                    # Entry point of the application
├── .env                           # Environment variables
├── Cargo.toml                     # Project dependencies
└── README.md                      # Project documentation



### Description of Files

- **main.rs**: This is the entry point of the application where routes are set up, and the Actix Web server is initialized.
- **handlers/**: Contains all the logic for various API endpoints.
- **models/**: Defines data structures such as the User model.
- **routes/**: Includes route definitions to manage endpoint registration.
- **.env**: Contains sensitive information such as database URLs and JWT secrets.
- **Cargo.toml**: Lists the dependencies needed for the project.

## Environment Setup

### Step 1: Clone the Repository

Start by cloning the project repository to your local machine:

```bash
git clone https://github.com/your-username/api_with_mongo.git
cd api_with_mongo


Step 2: Configure the Environment

Create a .env file in the root of your project directory with the following content:

dotenv

JWT_SECRET=your_jwt_secret_here
DATABASE_URL=mongodb://localhost:27017/your_database_name
EMAIL_USERNAME=your-email@gmail.com
EMAIL_PASSWORD=your-16-character-app-password


Step 3: Install Dependencies

Run the following command to build and install the project dependencies:

bash

cargo build

Running the Application

To start the Actix Web server, run:

bash

cargo run

The server will be accessible at http://localhost:8000.
API Endpoints

Here’s a quick overview of the available API endpoints:
1. User Registration

    Endpoint: POST /signup
    Request Body:

json

{
    "username": "exampleUser",
    "email": "example@example.com",
    "password": "yourPassword"
}

    Response: "User registered successfully"

2. User Login

    Endpoint: POST /login
    Request Body:

json

{
    "email": "example@example.com",
    "password": "yourPassword"
}

    Response:

json

{
    "token": "your_jwt_token"
}

3. Get User Profile

    Endpoint: GET /profile/{user_id}
    Headers:

plaintext

Authorization: Bearer your_jwt_token

    Response:

json

{
    "id": "user_id",
    "username": "exampleUser",
    "email": "example@example.com"
}

4. Edit User Profile

    Endpoint: PUT /profile/{user_id}
    Headers:

plaintext

Authorization: Bearer your_jwt_token

    Request Body:

json

{
    "username": "newUsername",
    "email": "new@example.com"
}

    Response: "Profile updated successfully"

5. Delete User Account

    Endpoint: DELETE /profile/{user_id}
    Headers:

plaintext

Authorization: Bearer your_jwt_token

    Response: "Account deleted successfully"

6. Forgot Password

    Endpoint: POST /forgot_password
    Request Body:

json

{
    "email": "example@example.com"
}

    Response: "Password reset link sent to your email"

7. Reset Password

    Endpoint: POST /reset_password
    Request Body:

json

{
    "token": "your_jwt_token",
    "new_password": "yourNewPassword"
}

    Response: "Password reset successfully"

Testing the API

You can test the API endpoints using tools like Postman or cURL. Make sure to send the correct headers and request bodies as specified above.
Example cURL Command

To test the signup endpoint, you can use the following command:

bash

curl -X POST http://localhost:8000/signup \
-H "Content-Type: application/json" \
-d '{"username": "exampleUser", "email": "example@example.com", "password": "yourPassword"}'

Troubleshooting

If you encounter any issues, consider the following:

    Make sure your MongoDB server is running and accessible.
    Double-check the contents of your .env file for accuracy.
    Look at the terminal for any error messages that might indicate the problem.

License

This project is licensed under the MIT License - see the LICENSE file for details.
