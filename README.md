# Comm-Sync-AI

Comm-Sync-AI is a collaborative platform that integrates AI-powered assistance for project management and communication. It allows users to create projects, manage file structures, and interact with AI for development-related queries.

## Features
- User authentication (register, login, logout, profile management).
- Project management (create projects, add users, update file trees).
- AI-powered assistance for development queries.
- Real-time communication using Socket.IO.

---

## Installation Guide

### Prerequisites
- Node.js (v16 or higher)
- MongoDB
- Redis

### Steps
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd Comm-Sync-AI
   ```

2. Navigate to the backend directory:
   ```bash
   cd backend
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

4. Create a `.env` file in the `backend` directory and configure the following variables:
   ```properties
   MONGODB_URI=mongodb://localhost:27017/Comm-Sync-AI
   REDIS_HOST=localhost
   REDIS_PORT=6379
   REDIS_PASSWORD=your_redis_password
   PORT=5000
   GOOGLE_AI_KEY=your_google_ai_key
   JWT_SECRET=your_jwt_secret
   ```

5. Start the backend server:
   ```bash
   npm start
   ```

6. Access the application at `http://localhost:5000`.

---

## Routes Table

### User Routes
| Method | Endpoint         | Description                     | Middleware                  |
|--------|------------------|---------------------------------|-----------------------------|
| POST   | `/users/register` | Register a new user             | `express-validator`         |
| POST   | `/users/login`    | Login a user                    | `express-validator`         |
| GET    | `/users/profile`  | Get logged-in user's profile    | `authMiddleware.authUser`   |
| GET    | `/users/logout`   | Logout the user                 | `authMiddleware.authUser`   |
| GET    | `/users/all`      | Get all users except logged-in  | `authMiddleware.authUser`   |

### Project Routes
| Method | Endpoint                 | Description                     | Middleware                  |
|--------|--------------------------|---------------------------------|-----------------------------|
| POST   | `/projects/create`       | Create a new project            | `authMiddleware.authUser`   |
| GET    | `/projects/all`          | Get all projects for a user     | `authMiddleware.authUser`   |
| PUT    | `/projects/add-user`     | Add users to a project          | `authMiddleware.authUser`   |
| GET    | `/projects/get-project/:projectId` | Get project details by ID | `authMiddleware.authUser`   |
| PUT    | `/projects/update-file-tree` | Update the file tree of a project | `authMiddleware.authUser` |

### AI Routes
| Method | Endpoint         | Description                     | Middleware                  |
|--------|------------------|---------------------------------|-----------------------------|
| GET    | `/ai/get-result` | Get AI-generated result for a prompt | None                    |

---

## Technologies Used
- **Backend**: Node.js, Express.js
- **Database**: MongoDB, Mongoose
- **Caching**: Redis
- **Authentication**: JWT
- **Real-time Communication**: Socket.IO
- **AI Integration**: Google Generative AI

---

## Contributing
1. Fork the repository.
2. Create a new branch for your feature/bug fix.
3. Commit your changes and push to your branch.
4. Submit a pull request.

---

## License
This project is licensed under the MIT License.