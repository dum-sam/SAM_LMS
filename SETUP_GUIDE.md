# 🚀 SAM-LMS Setup Guide

Follow these steps to run the project on a new laptop (Windows/Mac/Linux).

## 1. Prerequisites
Make sure you have **Python 3.10+** installed.
Check by running:
```bash
python --version
```

## 2. Setup (One Time Only)

### A. Extract/Clone the Folder
Open the project folder in VS Code.

### B. Create Virtual Environment
Open the Terminal in VS Code (`Ctrl + ~`) and run:

**Windows:**
```bash
python -m venv venv
.\venv\Scripts\activate
```

**Mac/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```
*(You should see `(venv)` appear at the start of your terminal line)*

### C. Install Dependencies
```bash
pip install -r requirements.txt
```

### D. Set Environment Variables
1.  Create a new file named `.env` in the root folder.
2.  Copy the contents from `.env.example` into `.env`.
3.  (Optional) Add your Cloudinary keys if you want image uploads to work.

## 3. Database Setup
Initialize the database:
```bash
python manage.py migrate
python manage.py populate_courses  # Adds sample courses
python manage.py createsuperuser   # Create admin account
```

## 4. Run the Server
```bash
python manage.py runserver
```

Go to **http://127.0.0.1:8000/** to see the site!
Login with the superuser account you created.

---
**Note:** To stop the server, press `Ctrl + C`.
