# 🚗 Vehicle Parking Management System

A full-stack **Vehicle Parking Management System** that allows users to search, reserve, and release parking spots in real time, while administrators can manage parking lots, parking spots, users, and monitor revenue & occupancy analytics.

The project is built with a **Flask backend** and a **Vue 3 frontend**, following a clean, scalable, and industry-standard architecture.

---

## 🚀 Project Overview

The **Vehicle Parking Website** solves real-world parking management challenges by providing:

- Real-time parking availability
- Secure role-based access (Admin & User)
- Dynamic parking spot creation and management
- Automated parking cost calculation
- Analytics dashboards for admins and users

This project demonstrates:
- REST API development using Flask
- JWT-based authentication and authorization
- Relational database modeling with SQLAlchemy
- Frontend SPA development using Vue 3
- Clean separation of frontend and backend
- Real-world business logic implementation

---

## ✨ Features

### 👤 User Features
- User registration and login
- View available parking lots
- Search parking by location or pin code
- View parking spots inside a parking lot
- Reserve a parking spot
- Release a reserved spot
- Automatic parking cost calculation
- View parking history
- View total amount spent
- User parking summary
- Edit user profile

### 🛠 Admin Features
- Admin login
- Create, update, and delete parking lots
- Automatic creation of parking spots
- Dynamically increase or decrease parking spots
- Prevent deletion of occupied spots
- View all parking lots with occupancy status
- Search parking lots by:
  - Location
  - Address
  - Pin code
  - ID
- Revenue and occupancy analytics
- Manage users
- View and edit admin profile

---

## 🧱 Tech Stack

### Backend
- **Framework:** Flask 3.1.x
- **Authentication:** Flask-JWT-Extended
- **Database:** SQLite
- **ORM:** SQLAlchemy
- **CORS:** Flask-CORS
- **Background Tasks:** Celery (ready for async jobs)

### Frontend
- **Framework:** Vue 3
- **Routing:** Vue Router
- **HTTP Client:** Axios
- **Styling:** Bootstrap 5
- **Build Tool:** Vite
- **Authentication:** JWT (LocalStorage)

---

## 📁 Project Structure
```bash
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
│ ├── index.html
│ ├── src/
│ │ ├── main.js
│ │ ├── App.vue
│ │ ├── routes.js
│ │ └── components/
│ └── README.md
└── README.md
```

---

## ⚙️ Backend Setup

```bash

1️⃣ Navigate to Backend
cd backend

2️⃣ Create Virtual Environment
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

3️⃣ Install Dependencies
pip install -r requirements.txt

4️⃣ Run Backend Server
python app.py
Backend runs at: http://127.0.0.1:5000

```
## ⚙️ Frontend Setup

```bash
1️⃣ Navigate to Frontend
cd frontend

2️⃣ Install Dependencies
npm install

3️⃣ Run Frontend Server
npm run dev

Frontend runs at: http://localhost:5173

CORS is enabled for frontend-backend communication.

```

## 🔐 Default Admin Credentials
Created automatically on first backend run

- Username: admin

- Email: admin@gmail.com

- Password: 123456

 
##  🗄 Database Schema Overview
### Main Entities
- User

- ParkingLot

- ParkingSpot

- Reservation

### Relationships
- One User → Many Reservations

- One ParkingLot → Many ParkingSpots

- One ParkingSpot → Many Reservations

##  🔌 API Overview (Key Routes)

### Authentication
|Route	| Method	| Description |
|--------|---------|------------|
|`/api/register`	| POST	| Register user |
|`/api/login`	| POST	| Login & get JWT |
|`/api/me`	| GET		| Logged-in user info |
	
		
	

### Admin APIs

|Route	| Method	| Description |
|--------|---------|------------|
|`/admin/parkinglots`	| GET / POST	| Manage parking lots |
|`/admin/parkingLots/<id>`	| GET / PUT	| View / update lot |
|`/admin/parkinglots/<id>`	| DELETE	| Delete lot |
|`/api/delete-spot/<lot_id>/<spot_id>`	| DELETE	| Delete spot |
|`/admin/search`	| GET	| Search parking lots |
|`/admin/summary`	| GET	| Revenue & occupancy |
|`/admin/users`	| GET	| 	View users |
|`/admin/profile`	| GET / PUT	| Admin profile |
		
		 

### User APIs

|Route	| Method	| Description |
|--------|---------|------------|
|`/user/parkinglots`	| GET		| Available parking |
|`/user/parkinglots/<id>/spots`	| GET 	| View spots|
|`/api/release`	| POST	| Release spot |
|`/api/user/parkinglots`	| 	GET		| User dashboard |
|`/user/summary`	| GET	| User summary|
|`/user/profile`	| 	GET / PUT		| User profile |
 

 
	
 
 
		

 



## 📊 Business Logic Highlights
- Parking cost calculated per hour

- Minimum parking duration = 1 hour

- Spot status updates automatically

- Admin cannot delete occupied spots

- Dynamic spot count synchronization

- Revenue calculated per occupied spot

## 🎯 Learning Outcomes
- Full-stack application architecture

- RESTful API design

- JWT authentication & role-based access

- SQLAlchemy relationships and joins

- Vue 3 SPA development

- Secure frontend-backend communication

- Real-world system design thinking

##  📌 Future Enhancements
- Live updates with WebSockets

- Payment gateway integration

- Time-based billing (minute-level)

- Admin dashboard charts

- Route guards (frontend)

- Deployment using Docker / AWS / Render

- Email / OTP verification