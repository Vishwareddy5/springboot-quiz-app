# 🧠 Spring Boot Quiz Application

A RESTful Quiz Application built using **Spring Boot**, **Spring Data JPA**, and **PostgreSQL**.  
This application allows creating quizzes dynamically, fetching questions, submitting answers, and calculating results with a clean layered architecture.

---

## 🚀 Features

- ✅ Create quizzes dynamically by category  
- 🎲 Random question selection using native queries  
- 🔒 Secure question delivery (answers hidden from users)  
- 📊 Automated score calculation  
- 🏗️ Clean layered architecture (Controller → Service → DAO)  
- 🎯 DTO pattern for data transfer  
- 💾 Transaction management for data consistency  

---

## 🛠️ Tech Stack

| Technology        | Purpose                          |
|------------------|----------------------------------|
| Java             | Core programming language        |
| Spring Boot      | Backend framework                |
| Spring Data JPA  | ORM and database operations      |
| Hibernate        | JPA implementation               |
| PostgreSQL       | Relational database              |
| Maven            | Build and dependency management  |

---


---

## 🎨 Key Design Decisions

- **DTO Pattern:** `QuestionWrapper` hides correct answers from users during quiz delivery  
- **ID-Based Evaluation:** Responses are matched using question IDs for accurate scoring  
- **Transactional Quiz Creation:** Ensures data consistency when creating quizzes  
- **Native Query for Random Selection:** Efficient question randomization using database-level queries  

---

## ⚙️ Configuration

### Prerequisites

- Java 17 or higher  
- PostgreSQL installed and running  
- Maven  

### Database Setup

1. Create a PostgreSQL database named **`questiondb`**  
2. Update your `application.properties`:

```properties
server.port=8090

spring.datasource.url=jdbc:postgresql://localhost:5432/questiondb
spring.datasource.username=postgres
spring.datasource.password=YOUR_PASSWORD

spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect


