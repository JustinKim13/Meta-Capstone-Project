# Meta Backend Capstone

This capstone project is for the Meta Back-End Development course.

## Commands

### Setup Environment

```bash
# Create a virtual environment
python -m venv capstone

# Activate the virtual environment
capstone\Scripts\activate

# Install Django
pip install django
```

### Create and Run Django Project

```bash
# Create a Django project
django-admin startproject littlelemon

# Navigate to the project directory
cd littlelemon

# Run the development server
python manage.py runserver

# Create a Django app
python manage.py startapp restaurant

# Install MySQL client
pip install mysqlclient
```

### MySQL Setup

```sql
CREATE DATABASE littlelemon;
USE littlelemon;
CREATE USER 'django'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON littlelemon.* TO 'django'@'localhost';
```

### Django Migrations and Superuser

```bash
# Apply migrations
python manage.py migrate

# Create migrations for any changes
python manage.py makemigrations

# Create a superuser
python manage.py createsuperuser
# Use the following details:
# Username: super
# Email: super@gmail.com
# Password: 123
```

### Install Django REST Framework

```bash
pip install djangorestframework
```

## API Endpoints

### Menu API

#### GET Menu Item by ID

```http
GET http://localhost:8000/api/menu/1
```

**Response:**

```json
{
    "id": 1,
    "title": "Menu 1",
    "price": "123.00",
    "inventory": 4
}
```

#### GET All Menu Items

```http
GET http://localhost:8000/api/menu
```

- Get all menus

#### POST Create a Menu Item

```http
POST http://localhost:8000/api/menu/
```

**Body:**

```json
{
    "title": "Menu 2",
    "price": "123.00",
    "inventory": 3
}
```

**Response:**

```json
{
    "id": 2,
    "title": "Menu 2",
    "price": "123.00",
    "inventory": 3
}
```

### Booking API

#### GET All Table Bookings

```http
GET http://localhost:8000/api/booking/tables
```

**Response:**

```json
[
    {
        "id": 1,
        "name": "Booking 1",
        "number_of_guests": 6,
        "booking_date": "2023-06-06T17:41:53Z"
    }
]
```

### Authentication

#### Obtain Token

```http
POST http://localhost:8000/api/api-token-auth/
```

**Response:**

```json
{
    "token": "a9d223579062329a541eb8eb8206c52c8b15c974"
}
```

### Add Authorization

Add authorization to the endpoints, so you have to send a header in the request with the Authorization title: Token [VALUE]

### Install Djoser

```bash
pip install djoser
```

Navigate to http://127.0.0.1:8000/auth/token/login/ to get the token.

- **User:** super
- **Password:** 123

Use http://127.0.0.1:8000/auth/token/logout/ to logout with the token in the header.

## Testing

```bash
python manage.py test
```

```sql
GRANT ALL PRIVILEGES ON `test_littlelemon`.* TO 'django'@'localhost';
FLUSH PRIVILEGES;
```

To execute the available unit tests, please open the Visual Studio terminal and enter the following command:

```bash
python manage.py test tests/
```

Ensure that you have activated the virtual environment and navigated into the 'littlelemon' directory prior to running the unit tests command.

Utilize this path to verify that the web application is serving static HTML content, inclusive of images and styling:

```http
/restaurant
```

For testing, you can make use of the following API endpoints with Insomnia or Postman clients. Alternatively, feel free to explore them through your browser of choice.

- **Register a new user using DJOSER endpoint:** `/auth/users/`
- **Log in and obtain an authentication token:** `/api-token-auth/`
- **Log in using the DJOSER endpoint:** `/auth/token/login`
- **Menu items:** `/api/menu/`, `/api/menu/{menuItemId}`
- **Table reservations:** `/api/booking/tables/`, `/api/booking/tables/{bookingId}`
