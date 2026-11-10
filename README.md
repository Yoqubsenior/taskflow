# TaskFlow

A task and project management API inspired by Jira — built with production-grade practices: role-based access control, JWT authentication, automated testing, and containerized deployment.

> 🚧 **Status:** Active development

## Tech Stack

- **Backend:** Python, Django, Django REST Framework
- **Database:** PostgreSQL
- **Auth:** JWT (djangorestframework-simplejwt)
- **Frontend:** React + Vite *(planned)*
- **DevOps:** Docker, GitHub Actions *(planned)*

## Features

- [x] Custom user model with email-based login
- [x] Environment-based settings (dev / prod)
- [ ] JWT authentication (register, login, refresh)
- [ ] Projects with owner / member roles
- [ ] Tasks, comments, filtering and pagination
- [ ] Object-level permissions (IDOR protection)
- [ ] Test suite (≥ 80% coverage)
- [ ] Docker Compose setup
- [ ] CI pipeline with GitHub Actions
- [ ] React frontend

## Getting Started

**Prerequisites:** Python 3.12+, Docker

```bash
# 1. Start PostgreSQL
docker run --name taskflow-db -e POSTGRES_DB=taskflow -e POSTGRES_USER=taskflow \
  -e POSTGRES_PASSWORD=taskflow -p 5432:5432 -v taskflow_pgdata:/var/lib/postgresql/data -d postgres:16

# 2. Set up the backend
cd backend
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\Activate.ps1
pip install -r requirements.txt

# 3. Configure environment
cp .env.example .env            # then set a real SECRET_KEY

# 4. Run
python manage.py migrate
python manage.py runserver
```

## Project Structure

```
backend/
├── apps/
│   └── users/          # custom user model
├── config/
│   └── settings/       # base / dev / prod
└── manage.py
```