# 💳 Netbanking Platform
Netbanking Platform is a full-stack web app for secure online banking. . Built with Java Spring Boot and Oracle JET. Includes admin dashboard, user authentication, notifications and role-based access.

## 🌐 Overview

NetBanking is a modern web application designed for both **customers** and **administrators**.  
It enables users to manage accounts, perform transactions, apply for loans and cards, pay bills, handle beneficiaries, and access branch information. The backend is built with Java Spring Boot and the frontend uses Oracle JET, providing a secure, modern user experience for both customers and administrators.

## 🚀Features

- 🔐 **User authentication & registration** (OTP/Email integration)
- 💼 **Account management** — create, view, and manage bank accounts
- 💸 **Funds transfer** — between accounts or to beneficiaries
- 💳 **Card management** — issue, block, and view card details
- 🏦 **Loan management** — apply, view, and repay loans
- 📊 **Admin dashboard** — analytics, user management, and approvals
- 📅 **Transactions overview** — history with advanced filtering
- 📩 **Email/SMS notifications** for critical events
- 🧩 **Role-based access control** using JWT
- 🧱 **Spring Security** for backend protection


##  ⚙️ Installation

### 🖥️ Backend — `netbanking_backend`

1. **Install prerequisites**
   - [Java 17+](https://adoptium.net/)
   - [Maven](https://maven.apache.org/)
   - [MySQL](https://www.mysql.com/)
2. **Clone the repository**,unzip it and navigate to the backend folder:
    cd backend
4. **Configure environment variables** (see Configuration section).
5. **Install MySQL** and create a database named `netbanking`.
   CREATE DATABASE netbanking;
6. in **Mysql** u need to provide roles to the user. example- after sign up, each user is considered as customer but in mysql u need to update role to admin after checking their id.
   select * from users; (to view id of user that needs to be made as admin)
   UPDATE users SET role = 'admin' WHERE user_id = 1;
7. Configure **environment:**
Edit src/main/resources/application.properties with your database credentials and mail settings.
8. **Build and run the backend:**
    mvn clean install
    mvn spring-boot:run
   The API will start on the port defined in your configuration (defaults to `8080`).

### 🖥️ Frontend (Oracle JET Web App)

1. **Install Node.js v16+** and npm.
2. **unzip and Navigate to the frontend folder:**
    cd frontend/myApp
4. **Install dependencies:**
    npm install
5. **Run the app in development mode:**
    ojet serve
   The UI app opens in your browser (defaults to Chrome).
**Remove old dependencies (if issues occur)**:
   '''Remove-Item -Recurse -Force node_modules, package-lock.json '''

## 🧠Usage

- **User login and registration** is available at the root page of the frontend app.
- After login, **users** can:
  - View balances and account details
  - Transfer funds, pay bills, manage cards and loans
  - Review transaction history
  - Apply for new accounts, cards, or loans
- **Admin** users can:
   - Access an analytics dashboard
   - Manage users accounts permissions, branches(open new branches/edit     existing braches),debit/credit card approvals and loans approvals
   - Transactional actions (transfer, loan, card) will hit the respective   secured API endpoints on the backend for approvals and after aadmin approval they will be given to users;

## ⚙️ Configuration

### Backend Environment Variables

These can be set in your shell or an `.env` file (use a tool like [direnv](https://direnv.net/) or set in your IDE):

set these up before running backend:
- **Database Configuration:**
    - `DB_USER` - your MySQL username
    - `DB_PASSWORD` - your MySQL password
- **JWT Security:**
    - `JWT_SECRET` - Secret key for token signing
    - `JWT_EXPIRATION` - Token expiration duration (ms)
- **Mail Service:**
    - `MAIL_USERNAME` - Email address for SMTP
    - `MAIL_PASSWORD` - Email password (consider using app-specific password)
- **Server Port:**
    - `PORT` - (optional) Backend server port, defaults to 8080

All other config (DB URL, driver, Hibernate options, mail SMTP, etc.) is set in `netBanking_backend/src/main/resources/application.properties`.

### Frontend

- No additional environment variables are required by default.
- Configuration for themes or API endpoints (if required) can be adjusted in the source (`netbanking_frontend/src/js/path_mapping.json`).

## 🧩Technologies Used

- **Backend:**
    - Java 17
    - Spring Boot (Web, Data JPA, Security)
    - Spring Security, JWT for authentication/authorization
    - MySQL (relational database)
    - Thymeleaf (optional for server-side views/templates)
    - Lombok (for boilerplate reduction)
    - JavaMail (for email/OTP)
    - JUnit, Spring Boot Test (for testing)
- **Frontend:**
    - Oracle JET (JavaScript Extension Toolkit)
    - Node.js, npm
    - MVVM architecture
    - Karma, Mocha or Jest (testing) [tooling provided]
    - SCSS/CSS
- **Tooling:**
    - Maven (Java build & dependency management)
    - Oracle JET CLI (frontend dev server & build)
    - Chrome (default dev/test browser)

## 📁 Project Structure

📦 NetBanking  
├── 📄 README.md  
├── 📦 backend.7z   # Backend (Spring Boot)  
├── 📦 frontend.7z  # Frontend (Oracle JET- inside myApp)  

### Inside `backend/`
src/

├── main/java/com/oracle/internetBanking/

│   ├── controller/     # REST API endpoints

│   ├── service/        # Business logic

│   ├── repository/     # JPA repositories

│   ├── entities/       # Database entities

│   └── config/         # JWT & security setup

├── main/resources/

│   └── application.properties

└── pom.xml
### Inside `myApp/`

src/

├── css/                 # Styles and themes

├── js/

│   ├── viewModels/     # Page logic

│   ├── views/          # HTML views

│   ├── services/       # API calls

└── package.json         # Dependencies & scripts


