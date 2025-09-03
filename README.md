# HR Management API

A professional backend system for Human Resource (HR) management, built with **NestJS**, **GraphQL**, and **PostgreSQL**. It provides features for managing employee records, payroll, and leave requests. The project also integrates **Redis caching** for performance optimization and **BullMQ** for handling payroll notifications asynchronously.

---

## 🚀 Features

* **Employee Management**: Create, read, update, and delete employee records.
* **Payroll System**: Process payrolls with notification queues.
* **Leave Management**: Request and approve leaves with balance tracking.
* **GraphQL API**: Flexible and strongly typed schema for querying and mutations.
* **Redis Caching**: Improved performance for frequently accessed queries.
* **BullMQ Queues**: Asynchronous payroll notifications.
* **Dockerized Setup**: Run the entire stack with Docker Compose.

---

## 🛠️ Tech Stack

* **Backend Framework**: [NestJS](https://nestjs.com/)
* **API Layer**: [GraphQL](https://graphql.org/)
* **Database**: [PostgreSQL](https://www.postgresql.org/)
* **ORM**: [Prisma](https://www.prisma.io/) (or TypeORM)
* **Cache & Queues**: [Redis](https://redis.io/)
* **Job Queue**: [BullMQ](https://docs.bullmq.io/)
* **Containerization**: [Docker Compose](https://docs.docker.com/compose/)

---

## 📂 Project Structure

```
hr-management-api/
├─ src/
│  ├─ employees/       # Employee CRUD
│  ├─ payroll/         # Payroll processing
│  ├─ leave/           # Leave management
│  ├─ notifications/   # BullMQ queues
│  └─ common/          # Shared modules, interceptors, guards
├─ prisma/             # Prisma schema & migrations
├─ docker-compose.yml  # Services (Postgres, Redis, API)
├─ package.json        # Dependencies & scripts
├─ tsconfig.json       # TypeScript config
└─ .env.example        # Environment variables
```

---

## ⚙️ Installation

### Prerequisites

* Node.js (>= 18.x)
* Docker & Docker Compose
* PostgreSQL & Redis (if running locally without Docker)

### Steps

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/hr-management-api.git
   cd hr-management-api
   ```

2. Copy environment variables:

   ```bash
   cp .env.example .env
   ```

3. Start services with Docker:

   ```bash
   docker-compose up --build -d
   ```

4. Run migrations:

   ```bash
   npx prisma migrate dev
   ```

5. Access GraphQL Playground:

   ```
   http://localhost:4000/graphql
   ```

---

## 🔑 Example Environment Variables (`.env`)

```
DATABASE_URL=postgresql://hruser:hrpass@localhost:5432/hrdb
REDIS_URL=redis://localhost:6379
PORT=4000
JWT_SECRET=changeme
```

---

## 📊 Example GraphQL Queries

### Create Employee

```graphql
mutation {
  createEmployee(data: { firstName: "John", lastName: "Doe", email: "john@example.com", salary: 5000 }) {
    id
    firstName
    email
  }
}
```

### Fetch Employees

```graphql
query {
  employees {
    id
    firstName
    lastName
    email
  }
}
```

### Run Payroll

```graphql
mutation {
  runPayroll(period: "2025-08") {
    processedCount
    period
  }
}
```

---

## 📦 NPM Scripts

```json
"scripts": {
  "start": "nest start",
  "start:dev": "nest start --watch",
  "build": "nest build",
  "prisma:generate": "prisma generate",
  "migrate:dev": "prisma migrate dev",
  "lint": "eslint . --ext .ts",
  "test": "jest"
}
```

---

## 🚧 Roadmap

* [ ] Add audit logging for employee changes
* [ ] Integrate S3-compatible storage for payslips
* [ ] Implement HR analytics dashboard
* [ ] Role-based access control for admins and employees

---

## 🧑‍💻 Contributing

Contributions are welcome! Please fork the repo and submit a pull request.

---

## 📜 License

This project is licensed under the MIT License.

---

## 📖 References

* [NestJS Documentation](https://docs.nestjs.com/)
* [Prisma Documentation](https://www.prisma.io/docs)
* [BullMQ Documentation](https://docs.bullmq.io)
* [GraphQL Documentation](https://graphql.org/)
