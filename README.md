# 🚀 My Portfolio

A full-stack personal portfolio website built with **Next.js 15** on the frontend and **Node.js + Express** on the backend, powered by **MongoDB** for data persistence. Designed to showcase projects, experience, Medium articles, and client reviews — with a unique roll-number-based access system for private content.

---

## 📸 Live Demo

🌐 **Portfolio:** [Frontend on Vercel and Backend on Render](https://www.sadikaslam.in/) 

---

## 📁 Project Structure

```
portfolio/
├── client/                         # Next.js 15 Frontend
│   ├── src/
│   │   ├── app/                    # Next.js App Router pages
│   │   ├── components/             # Reusable UI components
│   │   └── pages/                  # (if using Pages Router)
│   ├── public/                     # Static assets
│   ├── .env.local                  # Environment variables (client)
│   ├── next.config.mjs             # Next.js configuration + API rewrites
│   ├── tailwind.config.js          # Tailwind CSS theme config
│   ├── postcss.config.js           # PostCSS config
│   └── package.json
│
└── server/                         # Node.js + Express Backend
    ├── models/
    │   └── approvedRoll.model.js   # Mongoose model for approved roll numbers
    ├── routes/
    │   ├── ProjectRoutes.js        # /api/projects
    │   ├── ExperienceRoutes.js     # /api/experience
    │   ├── MediumRoutes.js         # /api/medium
    │   └── ReviewRoutes.js         # /api/reviews
    ├── import_rolls.js             # Utility: bulk import roll numbers from Excel
    ├── myList.xlsx                 # Source Excel file for roll numbers (gitignored)
    ├── index.js                    # Express app entry point
    └── package.json
```

---

## ✨ Features

### Frontend (Next.js 15)
- ⚡ **Next.js 15 App Router** with React 19
- 🎨 **Tailwind CSS v3** for utility-first styling with a custom color palette
- 🎞️ **Framer Motion** for smooth page & component animations
- 🌀 **GSAP** for advanced scroll-triggered animations
- 🧊 **Three.js / React Three Fiber** for 3D visuals and interactive scenes
- 🖼️ **React Parallax Tilt** for hover-tilt card effects
- 🔄 **SWR** for data fetching with built-in caching and revalidation
- 🎠 **Embla Carousel** for responsive project/review carousels
- ✍️ **React Type Animation** for typewriter-style hero text effects
- 🖍️ **React Syntax Highlighter** for code block display
- 📅 **date-fns** for readable date formatting across blog/experience sections
- 🔗 **Next.js API rewrites** to proxy backend calls, hiding the backend URL from the client

### Backend (Node.js + Express)
- 🚀 **Express 5** REST API
- 🛡️ **CORS** with configurable allowed origins via environment variables
- 🗄️ **MongoDB + Mongoose** for structured data models
- 🔐 **JWT (jsonwebtoken)** for authentication & protected routes
- 🔑 **bcrypt / bcryptjs** for password hashing
- ☁️ **Cloudinary** for image uploads and CDN delivery
- 📤 **Multer** for handling multipart/form-data (image uploads)
- 🍪 **cookie-parser** for cookie-based session handling
- 📰 **rss-parser** for fetching and parsing Medium RSS feeds dynamically
- 📊 **XLSX** for reading Excel files (used in roll number import utility)
- 🔁 **Nodemon** for hot-reloading in development

### Special Feature: Roll Number Access System
- Maintains an `ApprovedRoll` collection in MongoDB
- Admin can import a `.xlsx` list of approved roll numbers via `import_rolls.js`
- Bulk upsert logic ensures no duplicates and supports incremental updates

---

## 🛠️ Tech Stack

| Layer        | Technology                                      |
|--------------|-------------------------------------------------|
| Frontend     | Next.js 15, React 19, Tailwind CSS              |
| Animations   | Framer Motion, GSAP                             |
| 3D Graphics  | Three.js, @react-three/fiber, @react-three/drei |
| Data Fetching| SWR                                             |
| Backend      | Node.js, Express 5                              |
| Database     | MongoDB, Mongoose                               |
| Auth         | JWT, bcryptjs                                   |
| File Storage | Cloudinary, Multer                              |
| Deployment   | Vercel (client), Render (server)                |

---

## 🎨 Design System (Tailwind Theme)

Custom colors defined in `tailwind.config.js`:

| Token        | Hex       | Usage                          |
|--------------|-----------|--------------------------------|
| `primary`    | `#222222` | Headings, main text            |
| `secondary`  | `#7B7B7B` | Subtext, labels, captions      |
| `background` | `#F8F8F8` | Page background                |
| `white`      | `#FFFFFF` | Cards, containers              |
| `muted`      | `#EAEAEA` | Borders, dividers, skeletons   |

---

## 🔌 API Endpoints

| Method | Endpoint           | Description                          |
|--------|--------------------|--------------------------------------|
| GET    | `/`                | Health check — confirms API is live  |
| GET    | `/api/projects`    | Fetch all portfolio projects         |
| GET    | `/api/experience`  | Fetch work/education experience      |
| GET    | `/api/medium`      | Fetch parsed Medium blog articles    |
| GET    | `/api/reviews`     | Fetch client/peer reviews            |

> All routes are proxied through Next.js rewrites — client calls `/api/*` and Next.js forwards them to the Render backend.

---

## ⚙️ Environment Variables

### Client — `client/.env.local`

```env
NEXT_PUBLIC_API_URL=https://sadik-portfolio.onrender.com
```

### Server — `server/.env`

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
CLIENT_ORIGIN=http://localhost:3000
JWT_SECRET=your_jwt_secret
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

> ⚠️ Never commit `.env` files. They are already included in `.gitignore`.

---

## 🚀 Getting Started

### Prerequisites

- Node.js **v18+**
- npm **v9+**
- A running **MongoDB** instance (local or MongoDB Atlas)
- A **Cloudinary** account (for image handling)

---

```env
PORT=5000
MONGO_URI=mongodb+srv://<user>:<password>@cluster.mongodb.net/portfolio
CLIENT_ORIGIN=http://localhost:3000
JWT_SECRET=your_super_secret_key
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

Start the server:

```bash
# Development (with hot reload)
npm run dev

# Production
npm start
```
---

### 3. Setup the Frontend (Client)

```bash
cd client
npm install
```

Create a `.env.local` file inside the `client/` directory:

```env
NEXT_PUBLIC_API_URL=http://localhost:5000
```

Start the dev server:

```bash
npm run dev
```


---

### 4. Import Roll Numbers (Optional)

If you use the roll number access control feature:

1. Place your Excel file named `myList.xlsx` in the `server/` directory.
2. The file should have a column named `rollNumber` or `Roll` (or data in the first column).
3. Run the import script:

```bash
cd server
node import_rolls.js
```

This performs a **bulk upsert** — it inserts new roll numbers and skips duplicates safely.

---

## 📦 Build for Production

### Client

```bash
cd client
npm run build
npm start
```

### Server

```bash
cd server
npm start
```

---

## 🌐 Deployment

### Frontend → Vercel

1. Push the `client/` folder (or the whole repo) to GitHub.
2. Import the project on [vercel.com](https://vercel.com).
3. Set the root directory to `client/`.
4. Add the environment variable: `NEXT_PUBLIC_API_URL=https://sadik-portfolio.onrender.com`
5. Deploy.

### Backend → Render

1. Push the `server/` folder to GitHub.
2. Create a new **Web Service** on [render.com](https://render.com).
3. Set the root directory to `server/`.
4. Set the build command: `npm install`
5. Set the start command: `npm start`
6. Add all environment variables from `server/.env`.
7. Deploy.

---

## 🔒 Security Notes

- JWT tokens are used for any protected admin routes.
- Passwords are hashed using `bcryptjs` before being stored in MongoDB.
- CORS is restricted to the `CLIENT_ORIGIN` environment variable in production — set this to your Vercel domain.
- All `.env` files are gitignored.

---

## 📜 Scripts Reference

### Client (`client/package.json`)

| Script       | Command          | Description                   |
|--------------|------------------|-------------------------------|
| `dev`        | `next dev`       | Start development server      |
| `build`      | `next build`     | Build for production          |
| `start`      | `next start`     | Start production server       |
| `lint`       | `next lint`      | Run ESLint checks             |

### Server (`server/package.json`)

| Script       | Command            | Description                      |
|--------------|--------------------|----------------------------------|
| `start`      | `node index.js`    | Start production server          |
| `dev`        | `nodemon index.js` | Start dev server with hot reload |

---

## 🤝 Contributing

This is a personal portfolio project, but suggestions and feedback are always welcome!

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👨‍💻 Author

**Sadik**  
🌐 [sadik-portfolio.onrender.com](https://www.sadikaslam.in/)  
💼 [LinkedIn](https://www.linkedin.com/in/sadikaslam/) *(update with your link)*  
🐙 [GitHub](https://github.com/syedsadikaslam) *(update with your link)*

---

> Built with ❤️ using Next.js, Express, and MongoDB.
