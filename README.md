# Netbanking
Internet Banking Platform is a full-stack web app for secure online banking. Manage accounts, transactions, loans, cards, bills, and beneficiaries. Built with Java Spring Boot and Oracle JET. Includes admin dashboard, user authentication, notifications, and role-based access.
# Net Banking Platform

## Description

Internet Banking Platform is a full-stack web application offering a comprehensive suite of online banking services. It enables users to manage accounts, perform transactions, apply for loans and cards, pay bills, handle beneficiaries, and access branch information. The backend is built with Java Spring Boot and the frontend uses Oracle JET, providing a secure, modern user experience for both customers and administrators.

## Features

- User authentication and registration with OTP/email integration
- Account management (view, create, details, history)
- Funds transfer between accounts and to beneficiaries
- Card management (issue, block, view card status)
- Loan application and management (apply, view, repay)
- Transactions overview and advanced filtering
- Admin dashboard with statistics and management operations
- Notifications and audit logs
- Role-based access control via JWT authentication
- Built-in security using Spring Security
- Email/SMS notifications for critical actions

## Installation

### Backend (Spring Boot API server)

1. **Install Java 17** and **Maven**.
2. **Clone the repository** and navigate to the backend folder:
    ```sh
    cd netBanking_backend
    ```
3. **Configure environment variables** (see Configuration section).
4. **Install MySQL** and create a database named `netbanking`.
5. in **Mysql** u need to provide roles to the user. example- after sign up, each user is considered as customer but in mysql u need to update role to admin after checking their id.
   select * from users; (to view id of user that needs to be made as admin)
   UPDATE users SET role = 'admin' WHERE user_id = 1;

7. **Build and run the backend:**
    ```sh
    mvn clean install
    mvn spring-boot:run
    ```
   The API will start on the port defined in your configuration (defaults to `8080`).

### Frontend (Oracle JET Web App)

1. **Install Node.js v16+** and npm.
2. **Navigate to the frontend folder:**
    ```sh
    cd netbanking_frontend
    ```
3. **Install dependencies:**
    ```sh
    npm install
    ```
4. **Run the app in development mode:**
    ```sh
    ojet serve
    ```
   The UI app opens in your browser (defaults to Chrome).

   **Remove old dependencies (if issues occur)**:
   '''Remove-Item -Recurse -Force node_modules, package-lock.json '''

## Usage

- **User login and registration** is available at the root page of the frontend app.
- After login, users can:
  - View balances and account details
  - Transfer funds, pay bills, manage cards and loans
  - Add/view beneficiaries
  - Review transaction history
  - Apply for new accounts, cards, or loans
- **Admin** users can access dashboards with bank-wide metrics, manage branches, users, and accounts.
- Transactional actions (transfer, loan, card) will hit the respective secured API endpoints on the backend for approvals and after aadmin approval they will be provided to users;

## Configuration

### Backend Environment Variables

These can be set in your shell or an `.env` file (use a tool like [direnv](https://direnv.net/) or set in your IDE):

- set these up before running backend:
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

All other config (DB URL, driver, Hibernate options, mail SMTP, etc.) is set in `internetBanking/src/main/resources/application.properties`.

### Frontend

- No additional environment variables are required by default.
- Configuration for themes or API endpoints (if required) can be adjusted in the source (`ib_frontend/src/js/path_mapping.json`).

## Technologies Used

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
    - SCSS/CSS, modern browser support (default theme "redwood")
- **Tooling:**
    - Maven (Java build & dependency management)
    - Oracle JET CLI (frontend dev server & build)
    - Chrome (default dev/test browser)

## Project Structure

```
internetBanking/         # Java Spring Boot backend
  ├── src/main/java/com/oracle/internetBanking/
  │   ├── controller/      # API controllers (RESTful endpoints)
  │   ├── service/         # Business logic
  │   ├── repository/      # JPA repositories
  │   ├── entities/        # Database entities
  │   └── config/          # Security/JWT/configuration
  ├── src/main/resources/
  │   └── application.properties    # Main config/environment
  └── pom.xml             # Maven config & dependencies

ib_frontend/             # Oracle JET frontend
  ├── src/css/            # Styles/Themes
  ├── src/js/             # Main app, viewModels, services, views
  │   ├── viewModels/     # Page logic and state
  │   ├── views/          # HTML fragments per page/module
  │   ├── services/       # API integration
  └── package.json        # Dependencies & scripts
```

## License

This project is provided for demonstration and educational purposes.

