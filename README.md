# 📝 Quiz App — Java Spring Boot REST API

**A professional Quiz Management System built with Java and Spring Boot, featuring real-time scoring, category-based question management, and a clean RESTful API.**

[![Java](https://img.shields.io/badge/Java-17-orange?style=flat-square&logo=java)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1.0-brightgreen?style=flat-square&logo=spring)](https://spring.io/projects/spring-boot)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue?style=flat-square&logo=postgresql)](https://www.postgresql.org/)
[![Maven](https://img.shields.io/badge/Maven-3.x-red?style=flat-square&logo=apachemaven)](https://maven.apache.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Compilation & Execution](#-compilation--execution)
- [Project Structure](#-project-structure)
- [Core Classes](#-core-classes)
- [API Reference](#-api-reference)
- [How to Use](#-how-to-use)
- [Features Explained](#-features-explained)
- [Data Storage](#-data-storage)
- [Testing](#-testing)
- [Screenshots / Examples](#-screenshots--examples)
- [Known Issues](#-known-issues)
- [Future Enhancements](#-future-enhancements)
- [Contributing](#-contributing)
- [License](#-license)
- [Support & Contact](#-support--contact)

---

## 🔍 Overview

**Quiz App** is a back-end REST API application built with **Java 17** and **Spring Boot 3**. It provides a complete quiz management system that allows:

- **Administrators** to create and manage a bank of categorised questions.
- **Users** to generate custom quizzes from any category, answer the questions, and receive an instant score.

The application is designed as a **learning and educational tool** that demonstrates best practices in layered architecture, JPA/Hibernate ORM, and RESTful API design with Spring Boot. It is ideal for students, educators, and developers looking to study or extend a real-world Java web service.

### Use Cases

| Role | Use Case |
|------|----------|
| Student | Practice quizzes on any topic |
| Teacher | Build question banks per subject/difficulty |
| Developer | Learn Spring Boot REST API patterns |
| Recruiter | Evaluate candidates on specific tech areas |

---

## ✨ Features

- ✅ **Question Management** — Add, retrieve, and filter questions by category
- ✅ **Quiz Creation** — Auto-generate quizzes with random questions from a chosen category
- ✅ **Multiple Choice Questions (MCQ)** — Each question has four options
- ✅ **Difficulty Levels** — Tag questions as Easy, Medium, or Hard
- ✅ **Category Filtering** — Retrieve questions or build quizzes per topic (e.g., Java, Python, SQL)
- ✅ **Secure Answer Delivery** — Correct answers are never exposed to quiz-takers
- ✅ **Real-Time Scoring** — Instant score calculation on quiz submission
- ✅ **RESTful API** — Clean JSON-based endpoints consumable by any front-end or tool
- ✅ **Persistent Storage** — All data is stored reliably in PostgreSQL

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Java 17 |
| Framework | Spring Boot 3.1.0 |
| ORM | Spring Data JPA / Hibernate |
| Database | PostgreSQL 15 |
| Build Tool | Apache Maven 3.x |
| Code Simplification | Lombok |
| Testing | JUnit 5 (Spring Boot Test) |

---

## ✅ Prerequisites

Ensure the following are installed before setting up the project:

| Requirement | Version | Notes |
|-------------|---------|-------|
| **Java (JDK)** | 17+ | [Download OpenJDK 17](https://adoptium.net/) |
| **Maven** | 3.6+ | Or use the included `mvnw` wrapper |
| **PostgreSQL** | 13+ | [Download PostgreSQL](https://www.postgresql.org/download/) |
| **IDE** *(optional)* | — | IntelliJ IDEA or Eclipse recommended |
| **Postman / curl** *(optional)* | — | For testing API endpoints |

### IDE Setup

**IntelliJ IDEA**
1. Open IntelliJ → *File → Open* → select the `quiz-app-spring-main` directory.
2. IntelliJ will auto-detect the Maven project and import dependencies.
3. Ensure the Project SDK is set to **Java 17** (*File → Project Structure → SDK*).

**Eclipse**
1. Install the *Spring Tools 4* plugin from the Eclipse Marketplace.
2. *File → Import → Existing Maven Projects* → browse to `quiz-app-spring-main`.
3. Verify the JRE is Java 17 in *Project → Properties → Java Compiler*.

---

## 📦 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/KUNALM17/Quiz_App.git
cd Quiz_App/quiz-app-spring-main
```

### 2. Create the PostgreSQL Database

Connect to PostgreSQL and create the required database:

```sql
CREATE DATABASE questiondb;
```

> The application uses Hibernate's `ddl-auto=update` setting, so tables are created automatically on first run.

---

## ⚙️ Configuration

The main configuration file is located at:

```
quiz-app-spring-main/src/main/resources/application.properties
```

```properties
spring.datasource.driver-class-name=org.postgresql.Driver
spring.datasource.url=jdbc:postgresql://localhost:5432/questiondb
spring.datasource.username=postgres
spring.datasource.password=<your_password>
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
```

> **⚠️ Security Note:** Replace `<your_password>` with your actual PostgreSQL password. For production environments, use environment variables or a secrets manager instead of hardcoding credentials.

| Property | Description | Default |
|----------|-------------|---------|
| `spring.datasource.url` | JDBC connection URL to the PostgreSQL database | `localhost:5432/questiondb` |
| `spring.datasource.username` | PostgreSQL username | `postgres` |
| `spring.datasource.password` | PostgreSQL password | *(set this)* |
| `spring.jpa.hibernate.ddl-auto` | Schema management strategy (`update`, `create`, `validate`) | `update` |
| `server.port` | Port the application listens on | `8080` *(Spring default)* |

---

## 🚀 Compilation & Execution

### Using the Maven Wrapper (Recommended)

The project includes a Maven wrapper so you do **not** need Maven installed globally.

**Linux / macOS:**
```bash
cd quiz-app-spring-main

# Build the project
./mvnw clean install

# Run the application
./mvnw spring-boot:run
```

**Windows:**
```bash
cd quiz-app-spring-main

# Build the project
mvnw.cmd clean install

# Run the application
mvnw.cmd spring-boot:run
```

### Using an Installed Maven

```bash
mvn clean install
mvn spring-boot:run
```

### Run the Packaged JAR

```bash
./mvnw clean package
java -jar target/quizapp-0.0.1-SNAPSHOT.jar
```

Once started, the API is available at:

```
http://localhost:8080
```

---

## 📁 Project Structure

```
Quiz_App/
└── quiz-app-spring-main/          # Spring Boot project root
    ├── mvnw                        # Maven wrapper (Linux/Mac)
    ├── mvnw.cmd                    # Maven wrapper (Windows)
    ├── pom.xml                     # Maven build & dependency config
    └── src/
        ├── main/
        │   ├── java/com/quiz/quizapp/
        │   │   ├── QuizappApplication.java   # Application entry point
        │   │   ├── controller/               # REST API layer
        │   │   │   ├── QuestionController.java
        │   │   │   └── QuizController.java
        │   │   ├── dao/                      # Data access layer (JPA Repos)
        │   │   │   ├── QuestionDao.java
        │   │   │   └── QuizDao.java
        │   │   ├── model/                    # Entities & DTOs
        │   │   │   ├── Question.java
        │   │   │   ├── Quiz.java
        │   │   │   ├── QuestionWrapper.java
        │   │   │   └── Response.java
        │   │   └── service/                  # Business logic layer
        │   │       ├── QuestionService.java
        │   │       └── QuizService.java
        │   └── resources/
        │       └── application.properties    # App configuration
        └── test/
            └── java/com/telusko/quizapp/
                └── QuizappApplicationTests.java
```

---

## 🧩 Core Classes

### Model Layer

| Class | Type | Description |
|-------|------|-------------|
| `Question` | JPA Entity | Represents a quiz question with 4 options, correct answer, difficulty, and category |
| `Quiz` | JPA Entity | Represents a quiz with a title and a list of associated questions (Many-to-Many) |
| `QuestionWrapper` | DTO | Transfers question data **without** the correct answer — used when serving questions to quiz-takers |
| `Response` | DTO | Captures a user's answer submission: `{ id: <questionId>, response: "<answer>" }` |

### DAO Layer (Data Access)

| Class | Extends | Description |
|-------|---------|-------------|
| `QuestionDao` | `JpaRepository<Question, Integer>` | Provides CRUD operations for questions. Includes `findByCategory()` and a native query `findRandomQuestionsByCategory()` |
| `QuizDao` | `JpaRepository<Quiz, Integer>` | Provides CRUD operations for quizzes |

### Service Layer (Business Logic)

| Class | Description |
|-------|-------------|
| `QuestionService` | Handles question retrieval (`getAllQuestions`, `getQuestionsByCategory`) and creation (`addQuestion`) |
| `QuizService` | Handles quiz creation from random questions, question delivery (via `QuestionWrapper`), and score calculation |

### Controller Layer (REST API)

| Class | Base Path | Description |
|-------|-----------|-------------|
| `QuestionController` | `/question` | Exposes endpoints to list and add questions |
| `QuizController` | `/quiz` | Exposes endpoints to create a quiz, fetch its questions, and submit answers |

---

## 📡 API Reference

### Question Endpoints

#### Get All Questions
```http
GET /question/allQuestions
```
**Response:** `200 OK`
```json
[
  {
    "id": 1,
    "questionTitle": "What is the size of int in Java?",
    "option1": "2 bytes",
    "option2": "4 bytes",
    "option3": "8 bytes",
    "option4": "Depends on the system",
    "rightAnswer": "4 bytes",
    "difficultylevel": "Easy",
    "category": "Java"
  }
]
```

#### Get Questions by Category
```http
GET /question/category/{category}
```
| Parameter | Type | Description |
|-----------|------|-------------|
| `category` | path | Category name, e.g. `Java`, `Python`, `SQL` |

#### Add a Question
```http
POST /question/add
Content-Type: application/json
```
**Request Body:**
```json
{
  "questionTitle": "What keyword is used to inherit a class in Java?",
  "option1": "implements",
  "option2": "extends",
  "option3": "inherits",
  "option4": "super",
  "rightAnswer": "extends",
  "difficultylevel": "Easy",
  "category": "Java"
}
```
**Response:** `201 Created` — `"success"`

---

### Quiz Endpoints

#### Create a Quiz
```http
POST /quiz/create?category={category}&numQ={numQ}&title={title}
```
| Parameter | Type | Description |
|-----------|------|-------------|
| `category` | query | Category to pick questions from |
| `numQ` | query | Number of questions to include |
| `title` | query | Title for the quiz |

**Response:** `201 Created` — `"Success"`

#### Get Quiz Questions
```http
GET /quiz/get/{id}
```
Returns questions **without** correct answers.

**Response:** `200 OK`
```json
[
  {
    "id": 1,
    "questionTitle": "What keyword is used to inherit a class in Java?",
    "option1": "implements",
    "option2": "extends",
    "option3": "inherits",
    "option4": "super"
  }
]
```

#### Submit Quiz Answers
```http
POST /quiz/submit/{id}
Content-Type: application/json
```
**Request Body:**
```json
[
  { "id": 1, "response": "extends" },
  { "id": 2, "response": "4 bytes" },
  { "id": 3, "response": "true" }
]
```
**Response:** `200 OK` — Returns the number of correct answers as an integer.
```json
2
```

---

## 🎯 How to Use

### Step 1 — Start the Application

```bash
cd quiz-app-spring-main
./mvnw spring-boot:run
```

Wait until you see `Started QuizappApplication` in the console.

### Step 2 — Add Questions (Admin)

Use Postman, curl, or any HTTP client to add questions to the database:

```bash
curl -X POST http://localhost:8080/question/add \
  -H "Content-Type: application/json" \
  -d '{
    "questionTitle": "Which method is the entry point in Java?",
    "option1": "start()",
    "option2": "run()",
    "option3": "main()",
    "option4": "init()",
    "rightAnswer": "main()",
    "difficultylevel": "Easy",
    "category": "Java"
  }'
```

### Step 3 — Create a Quiz

Generate a quiz with 5 random Java questions:

```bash
curl -X POST "http://localhost:8080/quiz/create?category=Java&numQ=5&title=Java+Basics"
```

Note the quiz ID returned in the response (check your database or response headers).

### Step 4 — Take the Quiz

Retrieve quiz questions (without answers):

```bash
curl http://localhost:8080/quiz/get/1
```

### Step 5 — Submit Answers and View Score

Post your answers and receive an instant score:

```bash
curl -X POST http://localhost:8080/quiz/submit/1 \
  -H "Content-Type: application/json" \
  -d '[
    { "id": 1, "response": "main()" },
    { "id": 2, "response": "extends" },
    { "id": 3, "response": "4 bytes" },
    { "id": 4, "response": "true" },
    { "id": 5, "response": "JVM" }
  ]'
```

The API returns your score (e.g., `4` out of 5).

---

## 📖 Features Explained

### Quiz Management System

Quizzes are created dynamically by selecting a category, number of questions, and a title. The `QuizService` uses a native PostgreSQL `RANDOM()` query via `QuestionDao` to ensure a fresh set of questions every time.

### Question Answering

When a user starts a quiz (via `GET /quiz/get/{id}`), the application returns questions through the `QuestionWrapper` DTO — a data transfer object that intentionally **omits** the correct answer and metadata, so users cannot see answers in the API response.

### Score Calculation

On submission, `QuizService.calculateResult()` iterates through the submitted `Response` objects and compares each answer to the stored correct answer in the database. It returns the total number of correct responses as a plain integer.

### Results Display

The score is returned directly in the API response as a number (e.g., `3`). A front-end application or client can use this to calculate the percentage and display detailed results.

---

## 🗄 Data Storage

All data is persisted in a **PostgreSQL** relational database using **Spring Data JPA / Hibernate**.

### Database Tables

| Table | Description |
|-------|-------------|
| `question` | Stores all quiz questions (id, title, options, answer, difficulty, category) |
| `quiz` | Stores quiz metadata (id, title) |
| `quiz_questions` | Junction table for the Many-to-Many relationship between `quiz` and `question` |

### Schema Generation

Tables are created and updated automatically by Hibernate on startup using the `spring.jpa.hibernate.ddl-auto=update` setting — no manual SQL scripts required.

### Entity Relationships

```
Quiz (1) ──────────────── (N) quiz_questions (N) ──────────────── (1) Question
```

A single `Quiz` can contain many `Question` records, and a single `Question` can belong to many quizzes.

---

## 🧪 Testing

### Run All Tests

```bash
./mvnw test
```

### Current Test Coverage

The project includes a basic Spring Boot context load test:

```java
@SpringBootTest
class QuizappApplicationTests {
    @Test
    void contextLoads() { }
}
```

> **Note:** This test requires a running PostgreSQL instance with the `questiondb` database configured. Ensure `application.properties` is set correctly before running tests.

### Manual API Testing with Postman

1. Import the API endpoints into Postman.
2. Set the base URL to `http://localhost:8080`.
3. Test each endpoint in order: add questions → create quiz → get questions → submit answers.

---

## 📸 Screenshots / Examples

### Example: Add a Question

**Request:**
```http
POST /question/add
Content-Type: application/json

{
  "questionTitle": "What does JVM stand for?",
  "option1": "Java Virtual Machine",
  "option2": "Java Variable Model",
  "option3": "Java Version Manager",
  "option4": "Java Verified Module",
  "rightAnswer": "Java Virtual Machine",
  "difficultylevel": "Easy",
  "category": "Java"
}
```

**Response:**
```
HTTP/1.1 201 Created
"success"
```

---

### Example: Full Quiz Workflow

```bash
# 1. Create quiz with 3 Java questions
POST /quiz/create?category=Java&numQ=3&title=Java+Starter

# 2. Fetch questions (no answers shown)
GET /quiz/get/1
→ Returns 3 questions with only options visible

# 3. Submit answers
POST /quiz/submit/1
Body: [{"id":1,"response":"Java Virtual Machine"}, ...]

# 4. Get score
→ 2   (2 out of 3 correct)
```

---

## ⚠️ Known Issues

- **Database credentials in source code** — `application.properties` contains a hardcoded password. This should be moved to environment variables before deploying.
- **No authentication/authorization** — All API endpoints are publicly accessible with no login required.
- **No input validation** — Malformed or incomplete JSON payloads may result in unhandled errors.
- **No pagination** — `GET /question/allQuestions` returns all records at once, which may be slow with large datasets.
- **Basic error handling** — Errors print stack traces to the console without structured error responses.
- **Minimal test coverage** — Only a context-load test exists; no unit or integration tests for services.

---

## 🔮 Future Enhancements

- [ ] **User Authentication** — JWT-based login system with user roles (Admin, Student)
- [ ] **True/False & Fill-in-the-Blank** — Extend the `Question` model to support additional question types
- [ ] **Timer Support** — Add time limits per question or per quiz
- [ ] **Result Analytics** — Track user performance over time with charts and reports
- [ ] **Swagger / OpenAPI Docs** — Auto-generated interactive API documentation
- [ ] **Input Validation** — Use `@Valid` and Bean Validation annotations
- [ ] **Pagination** — Add Spring Data pagination for large question sets
- [ ] **Environment Variables** — Externalize configuration with Spring Profiles and `.env` files
- [ ] **Frontend UI** — Build a React or Angular interface for an end-to-end experience
- [ ] **Comprehensive Tests** — Add unit tests for services and integration tests for controllers
- [ ] **Docker Support** — Containerise the app and database with Docker Compose

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** and commit with clear messages
   ```bash
   git commit -m "Add: description of your change"
   ```
4. **Push** to your fork
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open a Pull Request** targeting the `main` branch

### Code Standards

- Follow standard Java naming conventions
- Add Javadoc comments to new public methods
- Write unit tests for new service logic
- Update this README if you add or change features

---

## 📄 License

This project is licensed under the **MIT License**.

```
MIT License

Copyright (c) 2026 Kunal M

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

See the [LICENSE](LICENSE) file for full details.

---

## 📬 Support & Contact

- 🐛 **Bug Reports / Feature Requests:** [Open a GitHub Issue](https://github.com/KUNALM17/Quiz_App/issues)
- 💬 **Discussions:** [GitHub Discussions](https://github.com/KUNALM17/Quiz_App/discussions)
- 👤 **Author:** [KUNALM17](https://github.com/KUNALM17)

---

*Built with ❤️ using Java & Spring Boot — suitable for learning, educational projects, and portfolio showcasing.*
