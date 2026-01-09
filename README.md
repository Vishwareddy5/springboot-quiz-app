# 🧠 Quiz Management System (Spring Boot)

A backend quiz application built using **Spring Boot** and **PostgreSQL** that dynamically generates quizzes based on category, securely delivers questions, evaluates user responses, and returns results.

This project demonstrates clean architecture, proper database relationships, and industry-standard backend design.

---

## 🔹 Features

- 📘 **Question Management**
  - Add, update, delete, and retrieve questions
  - Filter questions by category

- 🧠 **Dynamic Quiz Generation**
  - Create quizzes based on **category** and **number of questions**
  - Random selection of questions from the database

- 🔒 **Secure Question Delivery**
  - Answers are never exposed to the client
  - Uses DTO (`QuestionWrapper`) to hide correct answers

- 🧮 **Server-Side Evaluation**
  - Accepts user responses
  - Matches answers using **question IDs**
  - Calculates and returns the final score

- 🗃 **Relational Database Design**
  - Many-to-Many relationship between `Quiz` and `Question`
  - Join table: `quiz_questions`

---

## 🛠 Tech Stack

- **Backend:** Spring Boot (Java)
- **ORM:** Hibernate / JPA
- **Database:** PostgreSQL
- **Build Tool:** Maven
- **Utilities:** Lombok
- **Architecture:** Controller → Service → Repository

---

## 📐 Database Schema

### Tables

#### `question`
| Column | Description |
|-------|-------------|
| id | Question ID |
| question_title | Question text |
| option1–4 | Answer options |
| right_answer | Correct answer |
| category | Question category |
| difficulty_level | Difficulty level |

#### `quiz`
| Column | Description |
|--------|-------------|
| id | Quiz ID |
| title | Quiz title |

#### `quiz_questions`
Join table mapping quizzes to questions (Many-to-Many).

---

## 🔌 API Endpoints

### 📘 Question APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/question/allquestions` | Fetch all questions |
| GET | `/question/category/{cat}` | Get questions by category |
| POST | `/question/add` | Add a new question |
| PUT | `/question/{id}` | Update a question |
| DELETE | `/question/{id}` | Delete a question |

---

### 🧠 Quiz APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/quiz/create?category={cat}&numQ={n}&title={title}` | Create a quiz |
| GET | `/quiz/get/{id}` | Get quiz questions (without answers) |
| POST | `/quiz/submit/{id}` | Submit answers and get score |

---

## 📥 Sample Requests

### ▶ Create Quiz
```http
POST /quiz/create?category=java&numQ=5&title=JavaQuiz
