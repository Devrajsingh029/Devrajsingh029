<div align="center">

<!-- BANNER -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=2E8B57&height=200&section=header&text=Agriculture%20E-Commerce%20Backend&fontSize=42&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=REST%20API%20%7C%20Spring%20Boot%20%7C%20JWT%20%7C%20MySQL&descAlignY=58&descAlign=50" />

<!-- BADGES -->
<p>
  <img src="https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white" />
  <img src="https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/JWT-Auth-black?style=for-the-badge&logo=jsonwebtokens&logoColor=white" />
</p>
<p>
  <img src="https://img.shields.io/badge/Build-Passing-brightgreen?style=flat-square" />
  <img src="https://img.shields.io/badge/License-MIT-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/Status-Completed-success?style=flat-square" />
  <img src="https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square" />
</p>

<br/>

> 🌾 A **complete e-commerce backend** for agricultural products with REST APIs  
> for product listings, user registration, and order processing — secured with JWT Authentication.

<br/>

[📡 API Docs](#-api-endpoints) • [⚙️ Setup](#️-getting-started) • [🗃️ Schema](#️-database-schema) • [📬 Contact](#-contact)

</div>

---

## 📌 Table of Contents

- [✨ Features](#-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [🏗️ Architecture](#️-architecture)
- [📁 Folder Structure](#-folder-structure)
- [🗃️ Database Schema](#️-database-schema)
- [🔐 Security Flow](#-security-flow)
- [📡 API Endpoints](#-api-endpoints)
- [⚙️ Getting Started](#️-getting-started)
- [📋 Environment Variables](#-environment-variables)
- [🧪 Testing](#-testing)
- [📜 License](#-license)
- [📬 Contact](#-contact)

---

## ✨ Features

| Feature | Description |
|---|---|
| 🌿 Product Management | Full CRUD for agricultural product listings |
| 👤 User Registration | Secure sign-up, login and profile management |
| 📦 Order Processing | Place and manage orders linked to products and users |
| 🔐 JWT Security | All endpoints protected against unauthorized access |
| 🗄️ Normalized Schema | 4 related tables with foreign key constraints |
| 🧱 4-Module Architecture | Auth, Products, Users, Orders — cleanly separated |
| 🔗 JPA Relations | Hibernate-managed OneToMany and ManyToOne mappings |

---

## 🛠️ Tech Stack

<div align="center">

| Layer | Technology |
|---|---|
| **Language** | Java 17 |
| **Framework** | Spring Boot 3.x |
| **ORM** | Spring Data JPA + Hibernate |
| **Security** | JWT Authentication |
| **Database** | MySQL 8.0 |
| **Build Tool** | Maven |
| **API Testing** | Postman |
| **Version Control** | Git + GitHub |

</div>

<div align="center">
<br/>
<img src="https://skillicons.dev/icons?i=java,spring,mysql,maven,git,github,postman&theme=dark" />
</div>

---

## 🏗️ Architecture

```
Client (Postman / Frontend)
        │
        ▼
┌─────────────────────┐
│   Security Filter   │  ← JWT Validation on every request
└────────┬────────────┘
         │
         ▼
┌─────────────────────────────────────────────┐
│              Controller Layer               │
│  AuthController  │  ProductController       │
│  UserController  │  OrderController         │
└────────────────────┬────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────┐
│               Service Layer                 │
│   Business logic for all 4 modules          │
└────────────────────┬────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────┐
│             Repository Layer                │
│   Spring Data JPA + Hibernate               │
└────────────────────┬────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────┐
│           MySQL Database                    │
│   4 related tables with FK constraints      │
└─────────────────────────────────────────────┘
```

---

## 📁 Folder Structure

```
agri-ecommerce-backend/
│
├── src/
│   └── main/
│       ├── java/com/devraj/agri/
│       │   ├── controller/
│       │   │   ├── AuthController.java
│       │   │   ├── ProductController.java
│       │   │   ├── UserController.java
│       │   │   └── OrderController.java
│       │   │
│       │   ├── service/
│       │   │   ├── ProductService.java
│       │   │   ├── UserService.java
│       │   │   └── OrderService.java
│       │   │
│       │   ├── repository/
│       │   │   ├── ProductRepository.java
│       │   │   ├── UserRepository.java
│       │   │   └── OrderRepository.java
│       │   │
│       │   ├── model/
│       │   │   ├── Product.java
│       │   │   ├── User.java
│       │   │   └── Order.java
│       │   │
│       │   ├── security/
│       │   │   ├── JwtUtil.java
│       │   │   ├── JwtFilter.java
│       │   │   └── SecurityConfig.java
│       │   │
│       │   └── dto/
│       │       ├── ProductRequest.java
│       │       └── OrderRequest.java
│       │
│       └── resources/
│           └── application.properties
│
├── pom.xml
└── README.md
```

---

## 🗃️ Database Schema

```
┌──────────────────┐         ┌─────────────────────┐
│      users       │         │      products        │
├──────────────────┤         ├─────────────────────┤
│ id (PK)          │         │ id (PK)             │
│ name             │         │ name                │
│ email            │         │ description         │
│ password         │         │ price               │
│ role             │         │ stock_quantity      │
└────────┬─────────┘         │ category            │
         │                   └──────────┬──────────┘
         │                              │
         └─────────────┐  ┌────────────┘
                        ▼  ▼
               ┌──────────────────┐
               │      orders      │
               ├──────────────────┤
               │ id (PK)          │
               │ user_id (FK)  ───┼──→ users.id
               │ product_id (FK)──┼──→ products.id
               │ quantity         │
               │ total_price      │
               │ order_date       │
               └──────────────────┘
```

> **4 tables** — `users`, `products`, `orders`, `roles`  
> Linked via **foreign key constraints** for referential integrity.  
> All DB interactions handled via **Spring Data JPA and Hibernate**.

---

## 🔐 Security Flow

```
1.  POST /api/auth/register   →  User registers, password hashed with BCrypt
2.  POST /api/auth/login      →  Credentials validated, JWT token returned
3.  Request with Bearer token →  JwtFilter intercepts and validates signature
4.  Valid token               →  User identity extracted, request proceeds
5.  Invalid/expired token     →  401 Unauthorized returned immediately
```

---

## 📡 API Endpoints

### 🔑 Authentication

| Method | Endpoint | Access | Description |
|---|---|---|---|
| `POST` | `/api/auth/register` | 🌐 Public | Register new user |
| `POST` | `/api/auth/login` | 🌐 Public | Login and receive JWT token |

### 🌿 Products

| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/api/products` | 🌐 Public | Get all products |
| `GET` | `/api/products/{id}` | 🌐 Public | Get product by ID |
| `POST` | `/api/products` | 🔐 Auth | Add new product |
| `PUT` | `/api/products/{id}` | 🔐 Auth | Update product |
| `DELETE` | `/api/products/{id}` | 🔐 Auth | Delete product |

### 👤 Users

| Method | Endpoint | Access | Description |
|---|---|---|---|
| `GET` | `/api/users/{id}` | 🔐 Auth | Get user profile |
| `PUT` | `/api/users/{id}` | 🔐 Auth | Update user profile |

### 📦 Orders

| Method | Endpoint | Access | Description |
|---|---|---|---|
| `POST` | `/api/orders` | 🔐 Auth | Place a new order |
| `GET` | `/api/orders/{id}` | 🔐 Auth | Get order by ID |
| `GET` | `/api/orders/user/{userId}` | 🔐 Auth | Get all orders by user |

### 📌 Request / Response Example

**POST** `/api/orders`

```json
// Request Body (with Authorization: Bearer <token>)
{
  "productId": 3,
  "quantity": 2
}

// Response 201 Created
{
  "orderId": 12,
  "productName": "Organic Wheat",
  "quantity": 2,
  "totalPrice": 450.00,
  "orderDate": "2024-09-15T14:22:00"
}
```

---

## ⚙️ Getting Started

### ✅ Prerequisites

- Java 17+
- Maven 3.8+
- MySQL 8.0+
- Git

### 📥 Installation

**1. Clone the repository**
```bash
git clone https://github.com/Devrajsingh029/agri-ecommerce-backend.git
cd agri-ecommerce-backend
```

**2. Create the database**
```sql
CREATE DATABASE agridb;
```

**3. Configure `application.properties`**
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/agridb
spring.datasource.username=your_mysql_username
spring.datasource.password=your_mysql_password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

app.jwt.secret=your_jwt_secret_key
app.jwt.expiration=86400000
```

**4. Build and run**
```bash
mvn clean install
mvn spring-boot:run
```

**5. Test the API**
```
POST http://localhost:8080/api/auth/register
```

---

## 📋 Environment Variables

| Variable | Description | Example |
|---|---|---|
| `SPRING_DATASOURCE_URL` | MySQL connection string | `jdbc:mysql://host:3306/agridb` |
| `SPRING_DATASOURCE_USERNAME` | DB username | `root` |
| `SPRING_DATASOURCE_PASSWORD` | DB password | `password` |
| `APP_JWT_SECRET` | JWT signing secret | `mySecretKey123` |
| `APP_JWT_EXPIRATION` | Token expiry in ms | `86400000` (24h) |

---

## 🧪 Testing

All APIs tested with **Postman** across:
- ✅ All CRUD operations for Products, Users, Orders
- ✅ JWT token generation and validation
- ✅ Unauthorized access attempts (401 checks)
- ✅ Edge cases — missing fields, invalid IDs, duplicate emails
- ✅ HTTP codes: `200`, `201`, `400`, `401`, `404`

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repository
2. Create your branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 📬 Contact

<div align="center">

**Devraj Singh**  
Java Backend Developer | Bangalore, India

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/devraj-singh01)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:devrajsinghmehta@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Devrajsingh029)

</div>

---

<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=2E8B57&height=100&section=footer" />

⭐ **If you found this helpful, please star the repo!** ⭐

</div>
