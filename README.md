# 🚀 SAM-LMS - Smart Adaptive Learning Management System

A comprehensive Django-based Learning Management System with interactive courses, quizzes, certificates, and community features.

## 📋 Table of Contents
- [Features](#features)
- [System Requirements](#system-requirements)
- [Installation Guide](#installation-guide)
  - [Windows Setup](#windows-setup)
  - [macOS/Linux Setup](#macoslinux-setup)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [Available Commands](#available-commands)
- [Troubleshooting](#troubleshooting)

---

## ✨ Features

- **User Authentication**: Register, login, and role-based access (Student, Instructor, Admin)
- **Course Management**: Create, manage, and enroll in courses
- **Interactive Lessons**: Text and video-based content delivery
- **Quizzes & Assessments**: Create quizzes with multiple-choice questions
- **Certificates**: Generate certificates upon course completion
- **Learning Paths**: Guided learning sequences across multiple courses
- **Community Forum**: Real-time messaging in community channels
- **XP & Leveling System**: Earn experience points and level up
- **Dashboard**: Personalized learner and instructor dashboards
- **Admin Panel**: Comprehensive user and content management
- **Cloud Storage**: Cloudinary integration for image management

---

## 🖥️ System Requirements

**Minimum Requirements:**
- **Python**: 3.10 or higher
- **pip**: 21.0 or higher
- **Virtual Environment Support**: venv (built into Python)

**Recommended:**
- **Operating System**: Windows 10+, macOS 10.14+, or Linux (Ubuntu 20.04+)
- **RAM**: 4GB minimum, 8GB recommended
- **Disk Space**: 2GB for project and dependencies

---

## 📥 Installation Guide

### Windows Setup

#### Step 1: Prerequisites Check
Open PowerShell or Command Prompt and verify Python installation:
```bash
python --version
pip --version
```

If not installed, download from [python.org](https://www.python.org/downloads/)

#### Step 2: Navigate to Project
```bash
cd "path\to\SAM-LMS"
```

#### Step 3: Create Virtual Environment
```bash
python -m venv venv
```

#### Step 4: Activate Virtual Environment
```bash
.\venv\Scripts\activate
```

You should see `(venv)` at the start of your terminal line.

#### Step 5: Install Dependencies
```bash
pip install -r requirements.txt
```

**Expected output:**
```
Successfully installed Django==5.0 gunicorn==21.2.0 psycopg2-binary==2.9.9 ...
```

#### Step 6: Configure Environment Variables
Create a `.env` file in the root project directory:
```bash
copy .env.example .env
```

Edit `.env` with your preferred text editor and update:
```
DEBUG=True
SECRET_KEY=your-secret-key-here
CLOUDINARY_CLOUD_NAME=your-cloud-name
CLOUDINARY_API_KEY=your-api-key
CLOUDINARY_API_SECRET=your-api-secret
```

#### Step 7: Database Setup
Initialize the database:
```bash
python manage.py migrate
```

Populate sample data (optional):
```bash
python manage.py populate_courses
python manage.py populate_channels
```

Create Admin Account:
```bash
python manage.py createsuperuser
```

You'll be prompted for:
- Username
- Email
- Password (input won't be visible)
- Confirm Password

#### Step 8: Run Development Server
```bash
python manage.py runserver
```

**Expected output:**
```
Watching for file changes with StatReloader
Quit the server with CTRL-BREAK.
Starting development server at http://127.0.0.1:8000/
```

Visit **http://127.0.0.1:8000/** in your browser.

---

### macOS/Linux Setup

#### Step 1: Prerequisites Check
```bash
python3 --version
pip3 --version
```

#### Step 2: Navigate to Project
```bash
cd path/to/SAM-LMS
```

#### Step 3: Create Virtual Environment
```bash
python3 -m venv venv
```

#### Step 4: Activate Virtual Environment
```bash
source venv/bin/activate
```

You should see `(venv)` at the start of your terminal prompt.

#### Step 5: Install Dependencies
```bash
pip install -r requirements.txt
```

#### Step 6: Configure Environment Variables
```bash
cp .env.example .env
nano .env  # or use your preferred editor
```

Add your configuration values.

#### Step 7: Database Setup
```bash
python manage.py migrate
python manage.py populate_courses
python manage.py populate_channels
python manage.py createsuperuser
```

#### Step 8: Run Development Server
```bash
python manage.py runserver
```

Visit **http://127.0.0.1:8000/**

---

## 🗄️ Database Setup

### Available Management Commands

#### Populate Initial Data
```bash
python manage.py populate_courses
```
Adds sample courses, modules, and lessons.

#### Create Community Channels
```bash
python manage.py populate_channels
```
Sets up default community discussion channels.

#### Add More Content
```bash
python manage.py add_more_content
```
Adds additional course content for testing.

#### Create Superuser (Admin)
```bash
python manage.py createsuperuser
```

#### View Database
```bash
python manage.py dbshell
```

---

## 🚀 Running the Application

### Development Server
```bash
python manage.py runserver
```

**Access Points:**
- Frontend: http://127.0.0.1:8000/
- Admin Panel: http://127.0.0.1:8000/admin/
- API: http://127.0.0.1:8000/api-auth/

### Production Deployment

Using Gunicorn:
```bash
gunicorn config.wsgi:application
```

Using the build script (Linux/macOS):
```bash
chmod +x build.sh
./build.sh
```

---

## 📁 Project Structure

```
SAM-LMS/
├── config/                 # Django settings and WSGI
│   ├── settings.py        # Main configuration
│   ├── urls.py            # URL routing
│   ├── wsgi.py            # WSGI application
│   └── asgi.py            # ASGI application
│
├── courses/               # Course management app
│   ├── models.py          # Course, Module, Lesson, Quiz models
│   ├── views.py           # Course views and logic
│   ├── urls.py            # Course URL patterns
│   └── templates/         # Course templates
│
├── users/                 # User authentication app
│   ├── models.py          # Custom User model
│   ├── forms.py           # Registration and login forms
│   └── views.py           # Auth views
│
├── dashboard/             # Dashboard app
│   ├── views.py           # Dashboard views
│   └── templates/         # Dashboard templates
│
├── community/             # Community forum app
│   ├── models.py          # Channel and Message models
│   └── views.py           # Community views
│
├── theme/                 # Frontend theme
│   ├── static/            # CSS, JS, images
│   └── templates/         # Base templates
│
├── manage.py              # Django management script
├── requirements.txt       # Python dependencies
├── .env.example           # Environment variables template
└── db.sqlite3             # SQLite database (generated)
```

---

## 🛠️ Available Commands

### Django Management Commands

```bash
# Create migrations
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# Collect static files
python manage.py collectstatic

# Run development server
python manage.py runserver

# Run tests
python manage.py test

# Interactive shell
python manage.py shell

# Check for issues
python manage.py check
```

### Virtual Environment

```bash
# Activate (Windows)
.\venv\Scripts\activate

# Activate (macOS/Linux)
source venv/bin/activate

# Deactivate
deactivate

# List installed packages
pip list

# Update pip
pip install --upgrade pip
```

---

## ⚙️ Environment Variables

Create a `.env` file with the following variables:

```env
# Django Settings
DEBUG=True
SECRET_KEY=your-secret-key-here
ALLOWED_HOSTS=localhost,127.0.0.1

# Database (optional, defaults to SQLite)
DATABASE_URL=postgresql://user:password@localhost:5432/samlms

# Cloudinary (optional, for image uploads)
CLOUDINARY_CLOUD_NAME=your-cloud-name
CLOUDINARY_API_KEY=your-api-key
CLOUDINARY_API_SECRET=your-api-secret
```

---

## 🔧 Troubleshooting

### 1. Virtual Environment Not Activating
**Windows:**
```bash
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**macOS/Linux:**
```bash
chmod +x venv/bin/activate
source venv/bin/activate
```

### 2. Module Not Found Error
```bash
# Ensure virtual environment is activated, then:
pip install -r requirements.txt
```

### 3. Port 8000 Already in Use
```bash
# Run on different port
python manage.py runserver 8001
```

### 4. Database Migration Issues
```bash
# Clear migrations (development only)
python manage.py migrate courses zero
python manage.py migrate
```

### 5. Static Files Not Loading
```bash
python manage.py collectstatic --noinput
```

### 6. Cloudinary Images Not Working
- Ensure `.env` has correct Cloudinary credentials
- Check CLOUDINARY_STORAGE configuration in `config/settings.py`
- Verify Cloudinary account is active

### 7. Permission Denied on build.sh
```bash
chmod +x build.sh
./build.sh
```

---

## 📚 Dependencies

Main packages included:
- **Django 5.0**: Web framework
- **gunicorn**: WSGI HTTP server
- **Pillow**: Image processing
- **requests**: HTTP library
- **python-dotenv**: Environment variables
- **djangorestframework**: REST API framework
- **cloudinary**: Cloud storage integration
- **whitenoise**: Static file serving

See `requirements.txt` for complete list.

---

## 🔐 Security Notes

**Development Only:**
- `DEBUG=True` in `.env`
- Default SQLite database
- Development secret key

**Production:**
- Change `SECRET_KEY` to a random string
- Set `DEBUG=False`
- Use PostgreSQL or MySQL
- Set `ALLOWED_HOSTS` to your domain
- Use HTTPS
- Update CORS settings

---

## 📞 Support

For issues or questions:
1. Check the [Troubleshooting](#troubleshooting) section
2. Review Django documentation: https://docs.djangoproject.com/
3. Check project logs: `python manage.py check`

---

## 📄 License

This project is part of an internship program. All rights reserved.

---

**Last Updated:** December 30, 2025  
**Python Version:** 3.10+  
**Django Version:** 5.0
