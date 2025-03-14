# Project ReadMe: JavaScript Login System

## 1. Project Info

**Project Name:** Class Management System

**Project overview** The Class Management System is a web-based platform designed to assist schools and educational institutions in managing their classes and students more efficiently. It provides user authentication with role-based access (e.g., teacher, other users) and includes functionalities for managing student information such as reading, adding, editing, deleting, and updating records.

User cannot access system wihtou passport and the user password was encrypted to ensure the security requirements.

---

## 2. Project File Introduction

### Key Components:
- **Frontend**: 
  - Templates: `ejs` (Embedded JavaScript)
  - Styling: CSS
  - Scripting: JavaScript
- **Backend**: 
  - Framework: server.js with Express for server-side logic
- **Database**: 
  - MongoDB for data storage and management

### **Main Files and Functionalities**

#### **`server.js`**
- The core backend server file that handles the following functionalities:
  - Initializes the Express server.
  - Configures middleware like `body-parser`, `cookie-parser`, and `express-session`.
  - Sets up routes for user authentication (e.g., login, registration, password reset).
  - Implements CRUD operations for managing student information in the database.
  - Connects to the MongoDB database using Mongoose.
  - Serves static files and dynamic views.

#### **`package.json`**
- This file manages the project's dependencies and scripts.  
- **Dependencies List:**

- `bcryptjs`: ^2.4.3 - A library to help you hash passwords.
- `body-parser`: ^1.20.3 - Node.js body parsing middleware.
- `cookie-parser`: ^1.4.7 - Parse HTTP request cookies.
- `ejs`: (version not specified) - Embedded JavaScript templating.
- `passport`: ^0.7.0 - Simple, unobtrusive authentication for Node.js.
- `passport`-local: ^1.x.x - Local username and password authentication strategy for Passport.
- `bcrypt`: ^5.x.x - A library to help you hash passwords.
- `express`: (version not specified) - Fast, unopinionated, minimalist web framework for Node.js.
- `express-session`: ^1.18.1 - Simple session middleware for Express.
- `jsonwebtoken`: ^9.0.2 - JSON Web Token implementation (JWT).
- `method-override`: ^3.0.0 - Lets you use HTTP verbs such as PUT or DELETE in places where the client doesn't support it.
- `mongodb`: ^6.10.0 - The official MongoDB driver for Node.js.
- `mongoose`: ^8.8.0 - Elegant MongoDB object modeling for Node.js.
---

### **Folders**

#### **`public/`**
- Contains static files for the project, including:
  - **CSS:** Styling for the application.

#### **`views/`**
- Contains EJS (Embedded JavaScript) templates for the user interface:
  - **`index.ejs`**: The home page of the application.
  - **`login.ejs`**: Login page.
  - **`signup.ejs`**: Registration page.
  - **`reset.ejs`**: Password reset page.
  - **`home.ejs`**: Home page displayed upon successful login.
  - **`editor.ejs`**: A page for managing (create, updata, read and delete) student information.

#### **`models/`**
- Contains Mongoose model files for interacting with the database:
  - **User model:** Handles user authentication and data storage (e.g., username, email, hashed password).
  - **Student model:** Manages student information such as SID, name, gender, age, class ID, and other details.

---

## 3. Cloud-Based Server URL

**Testing URL:**  
[https://project3810-group19.onrender.com](https://project3810-group19.onrender.com)

---

## 4. Operation Guides
---
### **Operation Guides of Login / signup / Reset password Pages**

1. **Login:**
   - Navigate to the `/login` page.
   - Enter valid credentials to log in:
     - Example:
       - **Email:** `testuser@example.com`
       - **Password:** `password123`
   - Click the "Submit" button to log in.
   - Redirected to the home page, if the credentials are valid
   - If the account is logged in and the window is closed without clicking the logout button. Users do not need to log in again after clicking the login button

2. **Logout:**
   - Click the "Log out" button in the navigation bar or home page to end the session.
   - After user click logout button, user cannot access to the editor directly. User have to login the account again.

3. **Sign Up:**
   - Navigate to the `/signup` page.
   - Fill in the registration form (username, email, password, confirm password).
   - Click "Sign up" to register a new account.
   - The user password will be encrypted

4. **Password Reset:**
   - Navigate to the `/reset` page.
   - Enter username and email, then set a new password.
   - Submit the form to update password.

---

### **CRUD Operations for Student Management**
1. **Access the CRUD Interface:**
   - After logging in, navigate to the home page (`/home`),then click "start edit"
   - navigate to the student management page (`/edit`)

2. **Create new student**
   - Click the "Add Student" button to open the "Add New Student" form.
   - Fill in the required fields, such as SID, first name, last name, gender, etc.
   - Click "Add Student" to save the new student to the database.

3. **Noramal read**
    - The list of students is displayed on the student management page.
    - Each student's information is shown in a table format.

4. **Search Student**
    - Chick the search bar
    - Input student SID
    - Click "ENTER"

5. **Update:**
    ***Edit student information***
   - Click the "Edit" button next to a student's record.
   - Modify the fields as needed.
   - Click "Save All" to apply the changes.

6. **Delete:**
    ***Delete student***
   - Click the "Delete" button next to a student's record to remove it from the database.

---

### **RESTful CRUD Services**

1. **API Endpoints:**
   **GET** 
   - **/edit**: Fetch all students in the database.
   **POST** 
   - **/logining**: User authentication
   - **/signuping**: Create new account
   - **/reset**: Reset password
   - **/edit/add**: Add a new student to the database.
   - **/edit/saveAll**: Save all edit to the database.  
   **PUT**
   - **/edit/update/:id**: Add a student information
   **DELETE**
   - **/edit/delete/:id**: Delete a student by ID.

2. **Testing APIs with CURL:**
   **Authentication**
   - **Login:**
     ```bash
     curl -X POST https://project3810-group19.onrender.com/login \
     -H "Content-Type: application/json" \
     -d '{"email": "test@live.hkmu.edu.hk", "password": "testing"}'
     ```
   - **Creata accound:**
     ```bash
     curl -X POST https://project3810-group19.onrender.com/signup \
     -H "Content-Type: application/json" \
     --d'{"username": "tester", "email": "tester@example.com", "password": "tester","password_comfirm":"tester"}'
     ```
   - **Reset password:**
     ```bash
     curl -X POST https://project3810-group19.onrender.com/reset \
     -H "Content-Type: application/json" \
     -d '{"username": "testing123", "email": "testuser@example.com", "newPassword": "newtesting123"}'
     ```
   **Studnet Information Edit**
   - **Fetch all students:**
     ```bash
     curl -X GET https://project3810-group19.onrender.com/edit
     ```
   - **Add a new student:**
     ```bash
     curl -X POST https://project3810-group19.onrender.com/edit/add \
     -H "Content-Type: application/json" \
     -d '{"SID": "123456", "firstName": "John", "lastName": "Doe", "gender": "M", "age": 20, "classID": "CSE101"}'
     ```
   - **Save edit:**
     ```bash
     curl -X POST https://project3810-group19.onrender.com/edit/saveAll \
     -H "Content-Type: application/json" \
     -d '{"students": {"63f4e8d1c4a0f5f1d4a8c123": {"First name": "John","Last name": "Doe","age": "21"}}}'
     ```
    - **Update a Student information**
     ``` bash
     curl -X PUT https://project3810-group19.onrender.com/edit/update/:id \
     -H "Content-Type: application/json" \
     -d '{ "First name": "John", "Last name": "Smith", "Gender": "Male", "age": "21" }'
     ```

   - **Delete a student:**
     ```bash
     curl -X DELETE https://project3810-group19.onrender.com/edit/delete/123
     ```

3. **Response Format:**
   **Authentication**
   - **Login:**
    ```json
    User authenticated successfully: {
      _id: new ObjectId('674997431f8c8d11531098e2'),
      userID: 3,
      name: 'testing',
      email: 'test@live.hkmu.edu.hk',
      password: '$2b$10$fqcXfMUCkbRMdAhneucykOhOMHAQEWAniYSTlyeoX5RI614F5nGYu'
    }
     ```

   - **Signup (POST /signup)**
    ```text
    Redirects to /login.
    ```

   - **Reset password:**
    ```text
    Redirects to /login.
    ```

   **Studnet Information Edit**
   - **Fetch All Students (GET /edit)**
     ```json
        [
        {
            "_id": "63f4e8d1c4a0f5f1d4a8c123",
            "ClassID": "101",
            "SID": "123",
            "First name": "John",
            "Last name": "Doe",
            "Gender": "Male",
            "age": "20",
            "Home address": "123 Main St",
            "phone address": "1234567890",
            "Credit": "10"
        },
        {
            "_id": "63f4e8d1c4a0f5f1d4a8c124",
            "ClassID": "102",
            "SID": "124",
            "First name": "Jane",
            "Last name": "Smith",
            "Gender": "Female",
            "age": "22",
            "Home address": "456 Elm St",
            "phone address": "9876543210",
            "Credit": "15"
        }
    ]
     ```

   - **Save All Student Updates (POST /edit/saveAll)**
    ***Success (200)***
    ```text
    Redirects to /edit.
    ```
    ***Failure (500)***
    ```json
    {
    "success": false,
    "message": "Error updating students"
    }
     ```

   - **Add a New Student (POST /edit/add)**
    ***Success (200)***
    ```text
    Redirects to /edit.
    ```
    ***Failure (500)***
    ```json
    {
    "success": false,
    "message": "Error adding student"
    }
    ```

   - **Update a Student (PUT /edit/update/:id)**
    ***Success (200)***
    ```text
    Redirects to /edit.
    ```
    ***Failure (500)***
    ```json
    {
    "error": "Error deleting student"
    }
    ```

   - **Delete a Student (DELETE /edit/delete/:id)**
    ***Success (200)***
    ```json
    {
        "success": true,
        "message": "Student updated successfully",
        "student": {
            "_id": "63f4e8d1c4a0f5f1d4a8c123",
            "First name": "John",
            "Last name": "Doe",
            "age": "21"
        }
    }
    ```
    ***Failure (404)***
    ```json
    {
        "error": "Student not found"
    }
    ```

