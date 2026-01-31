# 🚗 Vehicle Parking Management System

A full-stack **Vehicle Parking Management System** that allows users to view available parking lots, reserve and release parking spots, and track parking history, while administrators can manage parking lots, spots, users, and monitor revenue & occupancy statistics.

The project is structured with **separate backend and frontend folders**, following industry-standard architecture.

---

## 🚀 Project Overview

The **Vehicle Parking Website** is designed to solve real-world parking management problems by providing a secure, role-based system for both **Users** and **Admins**.

It supports:
- Real-time parking spot availability
- Secure authentication using JWT
- Dynamic parking lot and spot management
- Cost calculation based on parking duration
- Admin dashboards with analytics and summaries

This project demonstrates:
- REST API development using Flask
- Role-based access control
- JWT authentication & authorization
- Relational database modeling with SQLAlchemy
- Clean backend architecture
- Scalable design with Celery integration

---

## ✨ Features

### 👤 User Features
- User registration and login
- View available parking lots
- View parking spots inside a parking lot
- Reserve a parking spot
- Release a parking spot
- Automatic parking cost calculation
- View parking history
- View total amount spent
- Update user profile
- View personal parking summary

### 🛠 Admin Features
- Admin login
- Create, update, and delete parking lots
- Automatically generate parking spots per lot
- Increase or decrease parking spots dynamically
- Prevent deletion of occupied spots
- View all parking lots with occupancy status
- Search parking lots by:
  - Location
  - ID
  - Address
  - Pin code
- View revenue and occupancy summary
- Manage users
- View and update admin profile

---

## 🧱 Tech Stack

### Backend
- **Framework:** Flask 3.1.2
- **Authentication:** Flask-JWT-Extended
- **Database:** SQLite
- **ORM:** SQLAlchemy
- **CORS:** Flask-CORS
- **Background Tasks:** Celery
- **Security:** JWT Tokens

### Frontend
- Frontend runs separately (e.g., React / Vite)
- Communicates with backend via REST APIs

---

## 📁 Project Structure

vehicle-parking-website/
├── backend/
│ ├── app.py
│ ├── applications/
│ │ ├── config.py
│ │ ├── database.py
│ │ ├── models.py
│ │ ├── routes.py
│ │ ├── security.py
│ │ ├── celery_init.py
│ └── requirements.txt
├── frontend/
│ └── (frontend code)
└── README.md


---

## ⚙️ Backend Installation & Setup

### 1️⃣ Navigate to Backend Folder
```bash
cd backend
2️⃣ Create Virtual Environment (Recommended)
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate
3️⃣ Install Dependencies
pip install -r requirements.txt
requirements.txt
Flask==3.1.2
Flask-JWT-Extended==4.7.1
Flask-SQLAlchemy==3.1.1
Werkzeug==3.1.3
SQLAlchemy==2.0.44
PyJWT==2.10.1
blinker==1.9.0
click==8.3.0
colorama==0.4.6
greenlet==3.2.4
itsdangerous==2.2.0
Jinja2==3.1.6
MarkupSafe==3.0.3
typing_extensions==4.15.0
4️⃣ Run the Backend Server
python app.py
Backend will run at:

http://127.0.0.1:5000
CORS is enabled for frontend at:

http://localhost:5173
🔐 Default Admin Credentials
Created automatically on first run

Username: admin

Email: admin@gmail.com

Password: 123456

⚠️ Change credentials before deployment.

🗄 Database Schema Overview
Main Entities
User

ParkingLot

ParkingSpot

Reservation

Relationships
One User → Many Reservations

One ParkingLot → Many ParkingSpots

One ParkingSpot → Many Reservations

🔌 API Documentation (Core Routes)
🔐 Authentication
Route	Method	Description
/api/register	POST	Register new user
/api/login	POST	Login user and get JWT
/api/me	GET	Get logged-in user profile
🛠 Admin Routes
Route	Method	Description
/admin/parkinglots	GET	View all parking lots
/admin/parkinglots	POST	Create parking lot
/admin/parkingLots/<id>	GET	Get parking lot by ID
/admin/parkingLots/<id>	PUT	Update parking lot
/admin/parkinglots/<id>	DELETE	Delete parking lot
/api/delete-spot/<lot_id>/<spot_id>	DELETE	Delete parking spot
/admin/search	GET	Search parking lots
/admin/summary	GET	Revenue & spot summary
/admin/users	GET	View all users
/admin/profile	GET / PUT	Admin profile
👤 User Routes
Route	Method	Description
/user/parkinglots	GET	View available parking lots
/user/parkinglots/<id>/spots	GET	View spots in lot
/api/reserve	POST	Reserve parking spot
/api/release	POST	Release parking spot
/api/user/parkinglots	GET	User dashboard
/user/summary	GET	User parking summary
/user/profile	GET / PUT	User profile
📊 Business Logic Highlights
Parking cost calculated per hour

Minimum parking duration = 1 hour

Spot status updates automatically on reserve/release

Admin cannot delete occupied spots

Dynamic spot count management per parking lot

Revenue calculated per occupied spot

🎯 Learning Outcomes
RESTful API design with Flask

JWT authentication & role-based authorization

SQLAlchemy relationships and joins

Secure backend architecture

Pagination and search optimization

Real-world business logic implementation

Scalable design using Celery

📌 Future Enhancements
Live WebSocket updates for spot availability

Online payment integration

Time-based billing (minute-level)

Admin analytics dashboard (charts)

Deployment using Docker / Render / AWS

OTP / email verification

Role-based frontend UI





















# 🚗 Vehicle Parking Management System (Flask Backend)

This is the backend API for the **Vehicle Parking Website**, developed using **Flask**, **SQLAlchemy**, and **SQLite3**.  
It allows users to register, log in, and manage parking-related information within different cities and car parks.

---

## 📅 Today's Progress (27 Oct 2025)

### ✅ Project Setup
- Initialized Flask backend with proper folder structure.
- Configured virtual environment (`.env`) and installed dependencies.
- Created SQLite database file: `secureDb.sqlite3`.
- Integrated **SQLAlchemy ORM** for database models.
- Added **CORS** and **JWT Authentication** setup.

---

## 🧱 Database Models Created

### **User**
- Fields: `first_name`, `last_name`, `email`, `vehicle_reg_number`, `postcode`, `phone_number`, `gender`, `age`, etc.
- Relationships:
  - Belongs to one **City**
  - Can access multiple **Car Parks**

### **City**
- Represents a city that contains car parks.
- Fields: `id`, `name`

### **CarPark**
- Represents parking lots within a city.
- Fields: `id`, `name`, `city_id`

### **user_carparks (Association Table)**
- Handles the **many-to-many relationship** between users and car parks.

---

## ⚙️ API Routes Implemented

### 1️⃣ **City Management**

#### ➕ Add City
**POST** `/cities`
```json
{
  "name": "Chennai"
}






📋 Get All Cities

GET /cities

2️⃣ Car Park Management
➕ Add Car Parks Under a City

POST /create_carparks

{
  "carparks": [
    {"name": "Central Mall Parking", "city_id": 1},
    {"name": "Phoenix Market City", "city_id": 1}
  ]
}

📋 Get Cities With Car Parks

GET /get_cities_with_carparks

3️⃣ User Authentication
🧍‍♂️ Sign Up

POST /signup

{
  "first_name": "Vivekanand",
  "last_name": "Kumawat",
  "email": "vivekanand@gmail.com",
  "confirm_email": "vivekanand@gmail.com",
  "vehicle_reg_number": "RJ23AB1234",
  "postcode": "332001",
  "phone_number": "9876543210",
  "preferred_mode": "Email & SMS",
  "password": "12345",
  "confirm_password": "12345",
  "gender": "Male",
  "age": 21,
  "city_id": 1,
  "carpark_ids": [1, 2]
}

🔐 Login

POST /login

{
  "email": "vivekanand@gmail.com",
  "password": "12345"
}


Response:

{
  "message": "Login successful",
  "token": "JWT_ACCESS_TOKEN",
  "user": {
    "id": 1,
    "email": "vivekanand@gmail.com",
    "name": "Vivekanand"
  }
}

🧪 Testing with Postman

Open Postman.

Use the above endpoints to:

Add cities and car parks.

Create new users.

Log in and verify JWT authentication.

Use GET routes to confirm database data.

🛠️ Tech Stack

Backend: Flask

Database: SQLite3

ORM: SQLAlchemy

Auth: Flask-JWT-Extended

CORS: flask-cors

Testing: Postman

👨‍💻 Author

Vivekanand Kumawat
IIT Madras BS Degree Student in Data Science
Backend Developer | Flask | Python | SQLAlchemy

🚀 Next Steps

Add user dashboard routes.

Implement vehicle parking booking logic.

Connect backend with frontend UI.