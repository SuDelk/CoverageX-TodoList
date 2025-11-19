# CoverageX TodoList

A modern, full-stack todo application built with React and NestJS, featuring a clean UI and containerized deployment.

## 🚀 Tech Stack

### Frontend
- **Vite** - Fast build tool and development server
- **React 19** - Modern UI library
- **TailwindCSS 4** - Utility-first CSS framework
- **Nginx** - Production web server
- **SweetAlert2** - Beautiful alerts and notifications

### Backend
- **Node.js** - JavaScript runtime
- **NestJS** - Progressive Node.js framework
- **Prisma** - Type-safe ORM
- **PostgreSQL** - Database (hosted on Supabase)
- **TypeScript** - Type-safe JavaScript

## ✨ Features

- ✅ Add new tasks with title and description
- ✅ Mark tasks as completed
- ✅ View recent tasks (up to 5 most recent)
- ✅ Dark mode support
- ✅ Responsive design
- ✅ Real-time task updates
- ✅ Beautiful loading states and animations

## 📁 Folder Structure

```
CoverageX-TodoList/
├── frontend/                # Frontend application
│   ├── src/
│   │   ├── components/     # React components
│   │   │   ├── AddTaskForm.jsx
│   │   │   ├── TaskCard.jsx
│   │   │   └── TaskList.jsx
│   │   ├── service/        # API service layer
│   │   ├── App.jsx         # Main app component
│   │   └── main.jsx        # Entry point
│   ├── public/             # Static assets
│   ├── Dockerfile          # Frontend Docker configuration
│   ├── package.json        # Frontend dependencies
│   └── vite.config.js      # Vite configuration
│
├── backend/                # Backend application
│   ├── src/
│   │   ├── tasks/          # Tasks module
│   │   ├── app.module.ts   # Root module
│   │   └── main.ts         # Entry point
│   ├── prisma/
│   │   └── schema.prisma   # Database schema
│   ├── test/               # E2E tests
│   ├── Dockerfile          # Backend Docker configuration
│   └── package.json        # Backend dependencies
│
└── docker-compose.yml      # Docker Compose configuration
```

## 🐳 Running with Docker

This application uses Docker Compose to run both the frontend and backend services. No `.env` files are required as all configuration is handled in `docker-compose.yml`.

### Prerequisites
- Docker
- Docker Compose

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/SuDelk/CoverageX-TodoList.git
   cd CoverageX-TodoList
   ```

2. **Build and run the containers**
   ```bash
   docker-compose up --build
   ```

3. **Access the application**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:3000

### Services Overview

- **Frontend Service**
  - Built with Vite and served by Nginx
  - Runs on port 5173
  - Automatically connects to backend API

- **Backend Service**
  - NestJS application with Prisma ORM
  - Runs on port 3000
  - Connected to Supabase PostgreSQL database
  - Prisma client is generated on startup

### Stop the Application

```bash
docker-compose down
```

## 📝 Commands

### Using Docker Compose

```bash
# Build and start all services
docker-compose up --build

# Start services in detached mode (background)
docker-compose up -d

# Stop all services
docker-compose down

# View logs
docker-compose logs

# View logs for a specific service
docker-compose logs frontend
docker-compose logs backend

# Rebuild a specific service
docker-compose up --build frontend
```

### Local Development (without Docker)

#### Frontend

```bash
cd frontend

# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build

# Run tests
npm test

# Run linter
npm run lint
```

#### Backend

```bash
cd backend

# Install dependencies
npm install

# Generate Prisma client
npx prisma generate

# Run database migrations
npx prisma migrate dev

# Start development server
npm run start:dev

# Build for production
npm run build

# Run tests
npm test

# Run E2E tests
npm run test:e2e

# Run linter
npm run lint
```

## 🔧 Developer Notes

### Database (Prisma)

The application uses **PostgreSQL** hosted on **Supabase**. Database configuration is managed through Prisma.

#### Prisma Client Generation
The Prisma client is automatically generated when the backend container starts. For local development:

```bash
cd backend
npx prisma generate
```

#### Database Migrations
To create and apply database migrations:

```bash
cd backend

# Create a new migration
npx prisma migrate dev --name your_migration_name

# Apply migrations in production
npx prisma migrate deploy

# View database in Prisma Studio
npx prisma studio
```

#### Database Schema
The application uses a simple Task model:
- `id` - Auto-incrementing primary key
- `title` - Task title (required)
- `description` - Task description (optional)
- `completed` - Completion status (default: false)
- `created_at` - Creation timestamp

### Testing

#### Frontend Tests
- Uses **Vitest** and **React Testing Library**
- Run tests: `npm test`
- Watch mode: `npm run test:watch`

#### Backend Tests
- Uses **Jest** and **Supertest**
- Unit tests: `npm test`
- E2E tests: `npm run test:e2e`
- Coverage: `npm run test:cov`

### Environment Variables

For Docker deployment, environment variables are defined in `docker-compose.yml`:

- `VITE_API_URL` - Backend API URL (frontend)
- `DATABASE_URL` - PostgreSQL connection string with pgBouncer (backend)
- `DIRECT_URL` - Direct PostgreSQL connection string (backend)
- `PORT` - Backend server port (backend)

### Code Quality

Both frontend and backend include ESLint configurations:

```bash
# Frontend
cd frontend && npm run lint

# Backend
cd backend && npm run lint
```

### Production Deployment

The application is containerized and ready for production deployment:

1. Frontend uses a multi-stage build:
   - Build stage: Compiles Vite/React app
   - Production stage: Serves with Nginx

2. Backend uses a multi-stage build:
   - Build stage: Installs dependencies and generates Prisma client
   - Production stage: Runs the compiled NestJS application

## 📄 License

UNLICENSED

## 👤 Author

SuDelk

---

**Happy coding! 🎉**
