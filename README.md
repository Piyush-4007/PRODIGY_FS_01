# PRODIGY_FS_01 — Secure User Authentication System

A Flask web application implementing secure user authentication with registration,
login/logout, hashed passwords, role-based access (user/admin), and a protected
dashboard. Built as **Task 01** of the Prodigy InfoTech Full Stack Web Development
internship.

## Features

- User registration with role selection (user / admin)
- Secure password storage using Werkzeug password hashing (PBKDF2-SHA256)
- Session-based login and logout (Flask-Login)
- A dashboard that is only accessible when logged in (`@login_required`)
- Admin-only content shown conditionally based on the user's role
- Responsive Bootstrap 5 UI

## Tech Stack

| Layer     | Technology                              |
| --------- | --------------------------------------- |
| Backend   | Python, Flask                           |
| Auth      | Flask-Login, Werkzeug password hashing  |
| Database  | SQLite via Flask-SQLAlchemy             |
| Frontend  | HTML, Jinja2 templates, Bootstrap 5     |

## Project Structure

```
PRODIGY_FS_01/
├── app.py                 # Flask application, routes, and User model
├── requirements.txt       # Python dependencies
├── templates/
│   ├── login.html
│   ├── register.html
│   └── dashboard.html
└── README.md
```

The SQLite database (`users.db`) is created automatically on first run and is
git-ignored.

## Getting Started

### Prerequisites

- Python 3.9+

### Setup

```bash
# 1. Clone the repository
git clone https://github.com/Piyush-4007/PRODIGY_FS_01.git
cd PRODIGY_FS_01

# 2. Create and activate a virtual environment
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS / Linux
source .venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the app
python app.py
```

Then open <http://127.0.0.1:5000/> in your browser.

## Usage

1. Go to **Register** and create an account (choose the `user` or `admin` role).
2. **Log in** with those credentials.
3. You are redirected to the protected **dashboard**. Accounts with the `admin`
   role see an additional admin-only panel.
4. Use **Logout** to end the session.

## Routes

| Route        | Method    | Description                              |
| ------------ | --------- | ---------------------------------------- |
| `/`          | GET       | Redirects to the login page              |
| `/register`  | GET, POST | Create a new account                     |
| `/login`     | GET, POST | Authenticate and start a session         |
| `/dashboard` | GET       | Protected page (login required)          |
| `/logout`    | GET       | End the session                          |

## Security Notes

Passwords are never stored in plain text — they are hashed with Werkzeug's
`generate_password_hash`. For a real deployment you should also set a strong,
secret `app.secret_key` (e.g. from an environment variable) and serve the app
over HTTPS behind a production WSGI server such as Gunicorn.

## License

Created for educational purposes as part of the Prodigy InfoTech internship.
