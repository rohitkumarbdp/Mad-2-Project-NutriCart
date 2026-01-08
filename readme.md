# NutriCart.com – Online Grocery Store Web Application

NutriCart.com is a full-stack online grocery store web application developed using **Flask** for the backend and **Vue.js** for the frontend. The platform supports multiple user roles and enables seamless product management, purchasing, and asynchronous background operations such as email notifications and sales report generation.

---

## Tech Stack

- **Backend:** Python, Flask  
- **Frontend:** Vue.js, HTML, CSS  
- **Database:** SQLite3  
- **Background Tasks:** Celery  
- **Message Broker:** Redis  

## Python Version

This project is developed and tested using **Python 3.10.13**.  
Using Python 3.10 is recommended for compatibility with all dependencies.

---

## User Roles and Features

### User
- Browse products across multiple categories
- Add products to cart and manage cart contents
- Purchase products seamlessly

### Admin
- Manage product categories
- Add, edit, or remove categories
- Approve or reject Store Manager registration requests

### Store Manager
- Add, edit, and delete products
- Request category creation or modification
- Trigger background jobs such as sales report generation

---

## Background Processing

The application uses **Celery with Redis** for asynchronous tasks, including:
- Sending email notifications
- Generating sales and activity reports

These tasks are executed in the background to keep the application responsive.

---

## Database Structure

The application uses **SQLite3** and consists of eight tables, including:
- Users
- Categories
- Products
- Carts
- Orders

Products are associated with categories using a **many-to-one relationship**.

---

## Default Credentials (For Demo)

### Admin
- **Email:** admin@gmail.com  
- **Password:** admin  

### User
- **Email:** user1@gmail.com  
- **Password:** user1  

### Store Manager
- **Email:** manager1@gmail.com  
- **Password:** manager1  

---

## Project Setup Instructions

### Prerequisites
Ensure the following are installed on your system:
- Python **3.10**
- Redis server
- Virtual environment support (`venv`)

---

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd NutriCart
```
### Step 2: Create and Activate Virtual Environment
```
python -m venv env
source env/bin/activate
```

### Step 3: Install Dependencies
```
pip install -r requirements.txt
```
### Step 4: Run the Flask Application
```
python main.py
```
The application will now be accessible in your browser.

### Step 5: Start Redis Server
Redis must be running before starting Celery.
```
redis-server
```
Keep this terminal running.
### Step 6: Start Celery Worker
Open a new terminal, activate the virtual environment, and run:
```
celery -A main.celery_app worker --loglevel=info
```
This starts the background task worker.
---
All three processes must be running simultaneously.

### Notes
•	The frontend is implemented using Vue.js and interacts with the Flask backend via APIs.
•   The database is automatically created when the application is run for the first time.
•	Background tasks such as email notifications and report generation are handled asynchronously using Celery.