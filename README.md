
# 🏦 BankSphere  

A **microservices-based banking platform** built with **Spring Boot, MySQL, Apache Kafka, React, and JWT authentication**, enabling secure customer and admin operations with real-time notifications.  

---

## 🚀 Features
- **Microservices Architecture**
  - **Customer Service** – Customer onboarding, deposits, withdrawals, fund transfers, and PDF statement generation.  
  - **Admin Service** – Manage customers, monitor transactions, and perform administrative operations.  
  - **Notification Service** – Kafka consumer for sending real-time transaction notifications.  

- **Unified Frontend (React + JWT)**
  - Secure login for both customers and admins.  
  - Role-based dashboards.  
  - Banking operations (deposits, withdrawals, transfers).  
  - Downloadable **PDF transaction statements**.  

- **Event-Driven Communication**
  - **Apache Kafka** used for publishing transaction events.  
  - Notification service consumes events for real-time updates.  

---

## 🛠️ Tech Stack
- **Backend:** Spring Boot (Customer, Admin, Notification services)  
- **Database:** MySQL  
- **Messaging:** Apache Kafka  
- **Frontend:** React.js, Tailwind CSS  
- **Authentication:** JWT (JSON Web Tokens)  
- **PDF Generation:** iTextPDF  

---

## 📂 Microservices Repositories
- [Customer Service](https://github.com/Narasimha9271/customer_service)  
- [Admin Service](https://github.com/Narasimha9271/admin_service)  
- [Notification Service](https://github.com/Narasimha9271/notification_service)  

---

## 🏗️ Architecture
```mermaid
flowchart TD
    subgraph Frontend [React Frontend]
        A[Customer/Admin Dashboard]
    end

    subgraph Backend [Spring Boot Microservices]
        B[Customer Service] --> D[(MySQL Database)]
        C[Admin Service] --> D
        B -->|Publishes Events| E[Kafka Broker]
        C -->|Publishes Events| E
        E --> F[Notification Service]
    end

    A -->|JWT Auth| B
    A -->|JWT Auth| C
    F -->|Sends Notifications| A
