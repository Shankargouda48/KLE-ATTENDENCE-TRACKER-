# KLE-ATTENDENCE-TRACKER-
<img width="1362" height="644" alt="Screenshot 2026-05-18 110707" src="https://github.com/user-attachments/assets/835483ee-b647-4f4d-b762-b427bb62d108" /># KLE-ATTENDENCE-TRACKER.

<img width="1363" height="641" alt="Screenshot 2026-05-18 111303" src="https://github.com/user-attachments/assets/97155af9-bab5-42f7-ba4c-9fdc17d52e2a" />
<img width="1307" height="647" alt="Screenshot 2026-05-18 111221" src="https://github.com/user-attachments/assets/975144c2-fed3-4505-be7d-4b6ef7c7fb3d" />
<img width="1354" height="639" alt="Screenshot 2026-05-18 110935" src="https://github.com/user-attachments/assets/ca48da89-b203-4a40-beb6-4c4ca8111d91" />
<img width="1364" height="651" alt="Screenshot 2026-05-18 110822" src="https://github.com/user-attachments/assets/64906d7c-70d1-41eb-b81b-455d2d87bf1b" />
<img width="1360" height="654" alt="Screenshot 2026-05-18 110800" src="https://github.com/user-attachments/assets/36fd9ba0-c7d9-44e7-9d85-2a180ed041e5" />
<img width="1353" height="547" alt="Screenshot 2026-05-18 110744" src="https://github.com/user-attachments/assets/46c4740d-23f1-4475-8d29-b47ae26cade4" />
<img width="1334" height="524" alt="Screenshot 2026-05-18 110730" src="https://github.com/user-attachments/assets/ab0deb37-d99e-448d-b5d1-5ca48a29f86d" />
<img width="1362" height="644" alt="Screenshot 2026-05-18 110707" src="https://github.com/user-attachments/assets/5e919da9-baca-4452-aee1-ed92cee02427" />
<img width="1365" height="766" alt="Screenshot 2026-05-17 122024" src="https://github.com/user-attachments/assets/a433bc69-bb70-405c-b6bf-09b79e393143" />



A professional Django attendance management system with a clean frontend, REST API, and JWT authentication.

## Overview

This project includes:
- Student registration and user authentication
- Attendance recording and analytics
- Subject management with student enrollment
- Teacher/admin dashboard and frontend pages
- REST API powered by Django REST Framework
- JWT authentication using `djangorestframework-simplejwt`
- Responsive HTML templates with CSS and JavaScript

## Project Structure

- `ds/` - Python virtual environment
- `kle_attendance/` - Django project directory
- `attendance/` - Django app with models, views, serializers, and URLs
- `templates/` - HTML template files for the frontend
- `static/` - CSS and JavaScript assets
- `db.sqlite3` - SQLite database file

## Prerequisites

- Python 3.10+ installed
- Git (optional)
- Recommended: use the existing virtual environment inside `ds/`

## Activate the Virtual Environment

Open PowerShell in the repository root and run:

```powershell
# Activate the existing virtual environment
.\ds\Scripts\Activate.ps1
```

Or in CMD:

```cmd
.\ds\Scripts\activate.bat
```

If the `ds/` environment does not exist, create it with:

```powershell
python -m venv ds
.\ds\Scripts\Activate.ps1
```

## Install Dependencies

If you do not already have the required packages installed, run:

```powershell
python -m pip install django djangorestframework djangorestframework-simplejwt django-cors-headers
```

## Run the Project

Change into the Django project directory and start the development server:

```powershell
cd kle_attendance
python manage.py migrate
python manage.py runserver
```

Open the app in a browser at:

- `http://127.0.0.1:8000/`

## Frontend Pages

- `/` — Home page
- `/register/` — Student registration page
- `/dashboard/` — Admin dashboard
- `/attendance/` — Attendance marking page
- `/students/` — Student list page
- `/analytics/` — Attendance analytics page
- `/api-docs/` — API documentation page

## API Endpoints

### Authentication

- `POST /api/auth/register/`
  - Request body: `username`, `password`, `first_name`, `last_name`, `email`
  - Response returns access token and refresh token

- `POST /api/auth/login/`
  - Request body: `username`, `password`
  - Response returns access token and refresh token

- `POST /api/auth/refresh/`
  - Request body: `refresh`
  - Response returns a new access token

### User API

- `GET /api/users/`
- `GET /api/users/{id}/`
- `POST /api/users/`
- `PUT /api/users/{id}/`
- `PATCH /api/users/{id}/`
- `DELETE /api/users/{id}/`
- `GET /api/users/profile/` — Current user profile
- `POST /api/users/{id}/make_teacher/` — Assign teacher role

### Subject API

- `GET /api/subjects/`
- `GET /api/subjects/{id}/`
- `POST /api/subjects/`
- `PUT /api/subjects/{id}/`
- `PATCH /api/subjects/{id}/`
- `DELETE /api/subjects/{id}/`
- `POST /api/subjects/{id}/add_student/`
- `POST /api/subjects/{id}/remove_student/`
- `GET /api/subjects/{id}/students/`

### Attendance API

- `GET /api/attendance/`
- `GET /api/attendance/{id}/`
- `POST /api/attendance/`
- `PUT /api/attendance/{id}/`
- `PATCH /api/attendance/{id}/`
- `DELETE /api/attendance/{id}/`
- `POST /api/attendance/bulk_mark/`
- `GET /api/attendance/by_date/?date=YYYY-MM-DD`

### Statistics

- `GET /api/stats/` — Attendance statistics for students
- `GET /api/dashboard/` — Dashboard stats for admins

## API Authorization

Protected endpoints require a JWT access token in the request header:

```http
Authorization: Bearer <access_token>
```

## Notes

- The project uses SQLite by default (`db.sqlite3`).
- `DEBUG` is currently enabled in `kle_attendance/settings.py` for development.
- The default static files path is `static/`, with `staticfiles/` as the collection target.

## Recommended Workflow

1. Activate `ds` virtual environment
2. Install dependencies
3. Apply migrations: `python manage.py migrate`
4. Create a superuser if needed: `python manage.py createsuperuser`
5. Run the server: `python manage.py runserver`
6. Visit `http://127.0.0.1:8000/`

## Optional Improvements

- Add `requirements.txt` for easier dependency install
- Add more frontend form validation and charts
- Harden production settings before deployment

