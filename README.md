# Random Post - Full-Stack Application

Welcome to Random Post, a complete MERN stack (MongoDB, Express.js, React, Node.js) application. This platform allows users to register, log in (using local credentials or Google), and manage their own blog posts. It's a demonstration of modern web development practices, including RESTful API design, token-based authentication, and a responsive user interface built with React and Tailwind CSS.

## Key Features

-   **Authentication**: Secure user registration and login system with both local (email/password) and Google OAuth 2.0 options.
-   **Session Management**: Uses JSON Web Tokens (JWT) stored in secure, HTTP-only cookies to manage user sessions.
-   **CRUD Operations**: Full Create, Read, Update, and Delete functionality for posts and comments.
-   **Authorization**: Users can only edit or delete their own posts and comments. Protected routes prevent unauthorized access.
-   **Responsive UI**: A clean, modern, and responsive user interface built with React and styled with Tailwind CSS.
-   **Theming**: Includes a dark and light mode toggle for user comfort.
-   **Pagination**: Both posts on the main page and comments on the detail page are paginated for better performance and user experience.

## Tech Stack

**Backend:**
-   **Node.js**: JavaScript runtime environment.
-   **Express.js**: Web application framework for Node.js.
-   **MongoDB**: NoSQL database for storing user, post, and comment data.
-   **Mongoose**: Object Data Modeling (ODM) library for MongoDB and Node.js.
-   **Passport.js**: Authentication middleware for Node.js, configured with JWT, local, and Google OAuth2 strategies.
-   **JSON Web Token (JWT)**: For creating secure access tokens.
-   **Bcrypt**: For hashing user passwords.
-   **CORS**: To enable Cross-Origin Resource Sharing.
-   **Dotenv**: For managing environment variables.

**Frontend:**
-   **React**: A JavaScript library for building user interfaces.
-   **Vite**: A fast build tool and development server.
-   **React Router**: For client-side routing and navigation.
-   **Tailwind CSS**: A utility-first CSS framework for rapid UI development.

---

## Getting Started

Follow these instructions to get a local copy of the project up and running on your machine for development and testing purposes.

### Prerequisites

-   Node.js (v18 or newer)
-   npm (or yarn/pnpm)
-   A running instance of MongoDB

### Backend Installation

1.  **Navigate to the backend directory:**
    ```bash
    cd express-test-Copy
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Create a `.env` file** in the `express-test-Copy` directory and populate it with your configuration details.

    ```env
    # A strong, secret key for signing JWTs
    JWT_SECRET_KEY=your_super_secret_key

    # Your Google OAuth 2.0 credentials from Google Cloud Console
    GOOGLE_CLIENT_ID=your_google_client_id.apps.googleusercontent.com
    GOOGLE_CLIENT_SECRET=your_google_client_secret

    # The URL of your frontend application
    FRONTEND_URL=http://localhost:5173
    ```

4.  **Start the server:**
    ```bash
    npm start
    ```
    The backend server will be running on `http://localhost:3000`.

### Frontend Installation

1.  **Navigate to the project root directory** (if you are in the backend directory, go back one level).

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Start the development server:**
    ```bash
    npm run dev
    ```
    The React application will be available at `http://localhost:5173`.

---

## API Endpoints Overview

The backend provides a RESTful API for managing users, posts, and comments.

-   **Authentication (`/auth`)**:
    -   `POST /register`: Register a new user.
    -   `POST /login`: Log in a user and receive a JWT cookie.
    -   `POST /logout`: Log out a user by clearing the JWT cookie.
    -   `GET /me`: Get the currently authenticated user's profile.
    -   `GET /google`: Initiate Google OAuth login.
    -   `GET /google/callback`: Callback URL for Google OAuth.

-   **Posts (`/posts`)**:
    -   `GET /`: Get a paginated list of all posts.
    -   `GET /:id`: Get a single post by its ID.
    -   `POST /`: Create a new post (requires authentication).
    -   `PUT /:id`: Update a post (requires authentication, user must be the owner).
    -   `DELETE /:id`: Delete a post (requires authentication, user must be the owner).

-   **Comments (`/posts/:postId/comments`)**:
    -   `GET /`: Get all comments for a specific post.
    -   `POST /`: Add a new comment to a post (requires authentication).
