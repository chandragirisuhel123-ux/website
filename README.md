# Loyola CS Digital Assistant

Professional Flask web application built around the original Streamlit chatbot logic.

## Project Structure

```text
G:/chatbot
|-- app.py
|-- main.py
|-- requirements.txt
|-- README.md
|-- app/
|   |-- __init__.py
|   |-- config.py
|   |-- extensions.py
|   |-- auth/
|   |   |-- __init__.py
|   |   `-- decorators.py
|   |-- models/
|   |   |-- __init__.py
|   |   `-- user.py
|   |-- routes/
|   |   |-- __init__.py
|   |   |-- admin.py
|   |   |-- auth.py
|   |   |-- chat.py
|   |   `-- main.py
|   |-- services/
|   |   |-- __init__.py
|   |   `-- chatbot_loader.py
|   |-- static/
|   |   `-- css/
|   |       `-- styles.css
|   `-- templates/
|       |-- admin.html
|       |-- base.html
|       |-- chat.html
|       |-- dashboard.html
|       |-- auth/
|       |   |-- login.html
|       |   `-- register.html
|       |-- errors/
|       |   `-- 403.html
|       `-- partials/
|           `-- sidebar.html
`-- instance/
    `-- app.db
```

## Key Notes

- The original chatbot logic is not rewritten in Flask.
- `app/services/chatbot_loader.py` loads `study_notes` and `get_answer()` directly from the original `app.py`.
- The new Flask app adds authentication, SQLite persistence, admin access control, and a Tailwind-based UI around that preserved logic.

## Setup

1. Create and activate a virtual environment.
2. Install dependencies:

```powershell
pip install -r requirements.txt
```

3. Set environment variables for production-safe secrets and optional admin bootstrap:

```powershell
$env:SECRET_KEY="replace-with-a-secure-random-secret"
$env:ADMIN_USERNAME="admin"
$env:ADMIN_PASSWORD="replace-with-a-strong-password"
```

## Run

```powershell
python main.py
```

Open [http://127.0.0.1:5000/login](http://127.0.0.1:5000/login)

## Routes

- `/login`
- `/register`
- `/dashboard`
- `/chat`
- `/logout`
- `/admin`

## Admin Access

- `/admin` requires a user with `role = "admin"`.
- If `ADMIN_USERNAME` and `ADMIN_PASSWORD` are set before startup, the app will create or update that admin user automatically.
