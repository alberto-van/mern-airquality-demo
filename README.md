# MERN Demo — Items + Air Quality

Technical test built with a **simplified MERN stack** under a tight deadline.  
The goal was to build a backend with Express + MongoDB, a React frontend, and consume data from an external API (OpenAQ).

Beyond just meeting the requirements, my intention was to demonstrate that I could set up an **end-to-end project**, connect all the moving parts, and have it running in just a few hours.

---

## Running the project

You can set up and run the project locally. Follow the [local setup instructions](#local-setup) below.

---

## 🚀 Backend

### Technologies

- **Node.js + Express** → simple, fast to set up, perfect for this kind of project.  
- **MongoDB Atlas + Mongoose** → first time using NoSQL. Atlas let me externalize the database without managing servers, and Mongoose made it easy to handle validations in one place instead of repeating them in every endpoint.  
- **Dotenv** for managing credentials.  
- **OpenAQ API** as the external API.

### Structure

```
server/
 ├── .env
 ├── package.json
 └── src/
     ├── db.js           # connection to MongoDB Atlas
     ├── index.js        # server entry point
     ├── models/
     │    └── Items.js   # schema and model for Items
     └── routes/
          └── airquality.js # OpenAQ integration
```

### Environment variables

```env
PORT=4000
MONGODB_URI=<MongoDB Atlas connection string>
OPENAQ_API_KEY=<your OpenAQ API key>
```

### Scripts

```bash
cd server
npm install
npm run dev
```

### Endpoints

- `GET /health` → checks if the server is responding.  
- `GET /api/items` → lists all items.  
- `POST /api/items` → creates a new item.  
- `GET /api/airquality?lat=<lat>&lon=<lon>` → returns nearby monitoring stations with measured parameters.

### Unit tests

Includes **basic tests** with **Jest** and **Supertest** in `server/tests/`:

- Healthcheck (`/health`).  
- Item reading (`GET /api/items`).  
- Item creation (`POST /api/items`).  

```bash
cd server
npm test
```

---

## 💻 Frontend

### Technologies

- **React + Vite** → already familiar with React, and Vite gave me fast dev server, HMR, and easy `.env` handling.

### Features

- Displays items from the backend.  
- Form to add new items.  
- Air quality widget (OpenAQ).  

### Scripts

```bash
cd client
npm install
npm run dev
```

---

## ⚙️ Technical decisions

- **Express + Node.js**: simple, proven, and quick to set up.  
- **React + Vite**: I already knew React, and Vite makes setup and environment variables easier.  
- **MongoDB Atlas (NoSQL)**: I came from SQL, but the test required NoSQL. I chose MongoDB over Firestore because it offers more flexibility in validations and because I wanted to try the full MERN stack.  
- **Mongoose**: centralizes validation in the model instead of repeating it in every endpoint.  

---

<a id="local-setup"></a>

## ▶️ How to run the project locally

1. Clone the repository.  
2. Create two `.env` files:

   - In `server/.env` → `PORT`, `MONGODB_URI`, and `OPENAQ_API_KEY`.  
   - In `client/.env` → `VITE_API_URL=http://localhost:4000`.  

3. Install dependencies and start the backend:

   ```bash
   cd server
   npm install
   npm run dev
   ```

4. In another terminal, start the frontend:

   ```bash
   cd client
   npm install
   npm run dev
   ```

5. Open `http://localhost:5173` in the browser.

---

## 📌 Learnings and improvements

- **External API**: I wanted to show more detailed data, but OpenAQ docs and deprecations limited me. With more time I would’ve implemented the measurements properly.  
- **Frontend**: I met the requirements, but I could’ve reused components and worked on styles to better demonstrate React and UX/UI skills.  
- **Process**: I proved to myself that I can build a full stack app from scratch to production under pressure. Next time I want to dive deeper into testing best practices and add global error handling middleware.