# Library Management API

This is a RESTful API for managing books in a library. It allows users to authenticate, add, update, retrieve, and delete books.

## Features

- User authentication (Signup, Login, Logout)
- CRUD operations for books
- Token-based authentication

## Technologies Used

- Django Rest Framework (DRF)
- MySQL
- Python 3.9+

---

## Installation

### 1. Create a Virtual Environment

```bash
python -m venv venv
use `venv\Scripts\activate`
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure Database (MySQL)

1. Create a MySQL database:
   ```sql
   CREATE DATABASE library_db;
   ```
2. Update `settings.py` with your MySQL credentials:
   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.mysql',
           'NAME': 'library_db',
           'USER': 'your_username',
           'PASSWORD': 'your_password',
           'HOST': 'localhost',
           'PORT': '3306',
       }
   }
   ```

### 4. Apply Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Create a Superuser

```bash
python manage.py createsuperuser
```

### 6. Run the Server

```bash
python manage.py runserver
```

---

## API Endpoints

### 1️ Authentication

#### **Signup** (POST `/signup/`)

```json
{
    "username": "shubh_more",
    "email": "shubh@example.com",
    "password": "password123"
}
```

#### **Login** (POST `/login/`)

```json
{
    "email": "shubh@example",
    "password": "password123"
}
```

Response:

```json
{
    "token": "your_auth_token"
}
```

#### **Logout** (POST `/logout/`)

Header: `Authorization: Token your_auth_token`

---

### 2️ Books

#### **Get All Books** (GET `/books/`)

Header: `Authorization: Token your_auth_token`

#### **Add a New Book** (POST `/books/`)

```json
{
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "isbn": "9780743273565",
    "published_year": 1925,
    "genre": "Fiction"
}
```

#### **Update a Book** (PUT `/books/{id}/`)

```json
{
    "title": "The Great Gatsby - Updated",
    "author": "F. Scott Fitzgerald",
    "isbn": "9780743273565",
    "published_year": 1925,
    "genre": "Classic Fiction"
}
```

#### **Delete a Book** (DELETE `/books/{id}/`)

Header: `Authorization: Token your_auth_token`

---

## Testing the API

### Using Postman

1. Open **Postman**.
2. Send a **POST** request to `http://127.0.0.1:8000/api/login/` with JSON body:
   ```json
   {
       "username": "john_doe",
       "password": "password123"
   }
   ```
3. Copy the token and use it in the **Authorization Header** for further requests.

### Using curl

#### Login & Get Token

```bash
curl -X POST http://127.0.0.1:8000/api/login/ \
     -H "Content-Type: application/json" \
     -d '{"username": "john_doe", "password": "password123"}'
```

#### Add a Book

```bash
curl -X POST http://127.0.0.1:8000/api/books/ \
     -H "Authorization: Token your_auth_token" \
     -H "Content-Type: application/json" \
     -d '{"title": "The Great Gatsby", "author": "F. Scott Fitzgerald", "isbn": "9780743273565", "published_year": 1925, "genre": "Fiction"}'
```
**Your Name** - [GitHub](https://github.com/aloksarwade2002)
