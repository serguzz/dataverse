# DataVerse

A full-stack data platform combining a modern Next.js frontend and FastAPI backend designed for dataset marketplace and data-driven applications.
Built for data scientists, data engineers, and data analysts on one side and data providers on the other side.

---

## Project Structure

- **frontend/**  
  Next.js 14+ app using the App Router  
  Contains isolated `node_modules/` and `package.json`

- **backend/**  
  FastAPI app with Pydantic settings, SQLAlchemy models, Alembic migrations  
  Uses isolated Python virtual environment `.venv/` and `requirements.txt`

- **docs/**  
  Markdown documentation: project specs, API design, architecture diagrams

- **docker-compose.yml**  
  Orchestrates backend, frontend, and PostgreSQL database with migrations on startup

- **.gitignore**  
  Configured to ignore `frontend/node_modules/`, `backend/.venv/`, build artifacts, and IDE configs

---

## Development Setup

### Prerequisites

- Docker & Docker Compose installed
- Python 3.12+ (for local backend dev)
- Node.js 20+ (for local frontend dev)

### Running the project with Docker

```bash
docker-compose up --build
```
- Runs Postgres, applies Alembic migrations automatically
- Starts FastAPI backend at http://localhost:8000
- Starts Next.js frontend at http://localhost:3000

### Local development (without Docker)
#### Backend

```bash
cd backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

#### Frontend
```bash
cd frontend
npm install
npm run dev
```

### Environment variables

- Backend uses .env file parsed with Pydantic Settings
- Example .env keys:

```bash
ENV=development
DATABASE_URL=postgresql://user:pass@localhost:5432/SECRET_KEY=your_secret_key_here
```

### Database Migrations
- Alembic config located in backend/alembic/
- Run migrations manually with:

```bash
cd backend
.venv/bin/alembic upgrade head
```

### Git Repository
- Single Git repo tracking the entire project
- .gitignore excludes environment folders and dependencies to keep repo clean

### Further Documentation
See docs/project-overview.md for detailed architecture, roadmap, and development guidelines.

### Contributions
Contributions welcome! Please follow coding standards and add tests where applicable.

DataVerse © 2025