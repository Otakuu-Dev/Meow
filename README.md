# Express & MongoDB (Mongoose) ES6 Backend

A modular Node.js backend using Express, MongoDB with Mongoose ODM, bcrypt for password hashing, and dotenv for environment configuration, built natively with modern ES6 modules (`"type": "module"`).

---

## 📁 Directory Structure

```text
express-mongo-backend/
├── .env.example
├── .env
├── .gitignore
├── package.json
├── README.md
└── src/
    ├── app.js                 # Express app initialization, middleware & routes
    ├── index.js               # Entry point, database connection & server start
    ├── config/
    │   └── database.js        # Mongoose connection logic
    ├── controllers/
    │   ├── authController.js  # User authentication (register, login, users)
    │   └── postController.js  # Post CRUD operations
    ├── models/
    │   ├── Post.js            # Post Mongoose schema & model
    │   └── User.js            # User Mongoose schema & bcrypt hashing hooks
    └── routes/
        ├── authRoutes.js      # Routes for authentication
        ├── index.js           # API route aggregator (/api)
        └── postRoutes.js      # Routes for Post CRUD
```

---

## 🚀 Getting Started

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Environment Variables

The project includes `.env.example` and a default `.env` file:

```env
PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb://127.0.0.1:27017/express_mongo_db
```

Ensure your MongoDB instance is running locally or provide a remote MongoDB Atlas connection URI.

### 3. Run the Server

- **Development Mode** (with Nodemon hot-reloading):
  ```bash
  npm run dev
  ```

- **Production Mode**:
  ```bash
  npm start
  ```

---

## 📡 API Endpoints

### Health Check
- `GET /` - Check server operational status

### Authentication (`/api/auth`)
- `POST /api/auth/register` - Register a new user (`name`, `email`, `password`)
- `POST /api/auth/login` - Authenticate user credentials (`email`, `password`)
- `GET /api/auth/users` - Retrieve all users (passwords omitted)

### Posts (`/api/posts`)
- `POST /api/posts` - Create a new post (`title`, `content`, `author?`, `tags?`)
- `GET /api/posts` - Retrieve all posts (sorted newest first, populated author)
- `GET /api/posts/:id` - Retrieve a single post by ID
- `PUT /api/posts/:id` - Update a post by ID
- `DELETE /api/posts/:id` - Delete a post by ID
