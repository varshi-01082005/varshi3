# Expense Tracker Application

A full-stack expense tracking application with user authentication, budgeting, category management, and AI insights. The backend is built with Node.js, Express, and MongoDB; the frontend uses React and Material UI.

---

## Features

- **User Authentication:** Register, login, and manage user sessions with JWT.
- **Expense Management:** Add, update, delete, and view expenses.
- **Budgeting:** Set budgets for categories and manage custom categories.
- **Sample/Test Users:** Easily create admin, test, and default users for demo or testing.
- **AI Insights (Stub):** Endpoint for future AI-powered financial insights.
- **Modern UI:** React frontend with Material UI and charting libraries.

---

## Project Structure

```
.
├── client/         # React frontend
├── server/         # Express backend
├── app.js          # (Legacy/root server entry, see server/server.js)
├── package.json    # Project-level dependencies
└── README.md
```

---

## Prerequisites

- **Node.js** (v18+ recommended)
- **npm** (v9+ recommended)
- **MongoDB** (local or cloud instance)

---

## Environment Variables

Create a `.env` file in the `server/` directory with the following variables:

```
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
PORT=5000
```

> **Note:** The `.env` file is not included in version control. You must create it yourself.

---

## Backend Setup (Express + MongoDB)

1. **Install dependencies:**
   ```bash
   cd server
   npm install
   ```

2. **Run environment checks (optional):**
   ```bash
   npm run setup
   ```

3. **Start the backend server:**
   ```bash
   npm run dev
   ```
   The server will run on `http://localhost:5000` by default.

---

## Frontend Setup (React)

1. **Install dependencies:**
   ```bash
   cd client
   npm install
   ```

2. **Start the frontend:**
   ```bash
   npm start
   ```
   The app will run on `http://localhost:3000` and proxy API requests to the backend.

---

## Running Both (Fullstack Dev)

From the `client` directory, you can run both servers concurrently:
```bash
npm run dev:full
```

---

## API Overview

### Auth Routes (`/api/auth`)
- `POST /register` — Register a new user (`{ username, password }`)
- `POST /login` — Login (`{ username, password }`)
- `GET /me` — Get current user (JWT required)
- `GET /categories` — Get category budgets and custom categories
- `PUT /categories/budget` — Update category budget
- `POST /categories/custom` — Add a custom category

#### Utility/Test Routes
- `POST /create-admin` — Create/reset admin user (`admin`/`admin123`)
- `POST /create-test-user` — Create/reset test user (`test`/`test123`)
- `POST /create-default` — Create/reset default user (`user@example.com`/`password123`)
- `POST /create-verified-user` — Create/reset verified user

### Expense Routes (`/api/expenses`)
- `GET /` — List all expenses (JWT required)
- `POST /` — Add new expense
- `PUT /:id` — Update expense
- `DELETE /:id` — Delete expense

### AI Insights (`/api/ai/insights`)
- `GET /insights` — (Stub) Returns a placeholder message for AI insights

---

## Data Models

### User
- `username` (String, unique, required)
- `password` (String, required, hashed)
- `expenses` (Array of Expense references)
- `categoryBudgets` (Array of `{ category, amount }`)
- `customCategories` (Array of Strings)
- `createdAt` (Date)

### Expense
- `user` (User reference, required)
- `description` (String, required)
- `amount` (Number, required)
- `category` (String, required)
- `date` (Date, required)
- `createdAt` (Date)

---

## Development Scripts

From the `server` directory:
- `npm run create-admin` — Create/reset admin user
- `npm run create-test-user` — Create/reset test user
- `npm run create-default` — Create/reset default user
- `npm run test-env` — Check environment variables
- `npm run test-mongo` — Test MongoDB connection

---

## Frontend

The frontend is a React app using Material UI, Chart.js, and other modern libraries. See [`client/README.md`](client/README.md) for more details on available scripts and React-specific documentation.

---

## License

MIT (or specify your license)

---

## Acknowledgements

- [Create React App](https://create-react-app.dev/)
- [Express](https://expressjs.com/)
- [MongoDB](https://www.mongodb.com/)
- [Material UI](https://mui.com/)
- [Chart.js](https://www.chartjs.org/)

---

**Feel free to customize this README further for your project's needs!**
