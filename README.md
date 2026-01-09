🧠 Spring Boot Quiz Application
A RESTful Quiz Application built using Spring Boot, Spring Data JPA, and PostgreSQL.
This application allows creating quizzes dynamically, fetching questions, submitting answers, and calculating results with a clean layered architecture.

🚀 Features

✅ Create quizzes dynamically by category
🎲 Random question selection using native queries
🔒 Secure question delivery (answers hidden from users)
📊 Automated score calculation
🏗️ Clean layered architecture (Controller → Service → DAO)
🎯 DTO pattern for data transfer
💾 Transaction management for data consistency


🛠️ Tech Stack
TechnologyPurposeJavaCore programming languageSpring BootBackend frameworkSpring Data JPAORM and database operationsHibernateJPA implementationPostgreSQLRelational databaseMavenBuild and dependency management

📁 Project Structure
src/main/java/com/telusko/quizApp
│
├── Controller
│   ├── QuestionController.java
│   └── QuizController.java
│
├── Service
│   ├── QuestionService.java
│   └── QuizService.java
│
├── dao
│   ├── QuestionDao.java
│   └── QuizDao.java
│
├── model
│   ├── Question.java
│   ├── Quiz.java
│   ├── Response.java
│   └── QuestionWrapper.java
│
└── QuizAppApplication.java

🎨 Key Design Decisions

DTO Pattern: QuestionWrapper hides correct answers from users during quiz delivery
ID-Based Evaluation: Responses are matched using question IDs for accurate scoring
Transactional Quiz Creation: Ensures data consistency when creating quizzes
Native Query for Random Selection: Efficient question randomization using database-level queries


⚙️ Configuration
Prerequisites

Java 17 or higher
PostgreSQL installed and running
Maven

Database Setup

Create a PostgreSQL database named questiondb
Update your application.properties:

propertiesserver.port=8090

spring.datasource.url=jdbc:postgresql://localhost:5432/questiondb
spring.datasource.username=postgres
spring.datasource.password=YOUR_PASSWORD

spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

🚀 How to Run Locally
1️⃣ Clone the Repository
bashgit clone https://github.com/Vishwareddy5/springboot-quiz-app.git
cd springboot-quiz-app
2️⃣ Configure Database

Create a PostgreSQL database named questiondb
Update username and password in application.properties

3️⃣ Run the Application
bash./mvnw spring-boot:run
The application will start on http://localhost:8090

📥 API Endpoints
📝 Question Management
Get All Questions
httpGET /question/allQuestions
Get Questions by Category
httpGET /question/category/{category}
Add New Question
httpPOST /question/add
Content-Type: application/json

{
  "questionTitle": "What is Java?",
  "option1": "Programming Language",
  "option2": "Coffee",
  "option3": "Island",
  "option4": "Framework",
  "rightAnswer": "Programming Language",
  "difficulty": "Easy",
  "category": "java"
}
🎯 Quiz Operations
Create Quiz
httpPOST /quiz/create?category=java&numQ=5&title=JavaQuiz
Get Quiz Questions
httpGET /quiz/get/1
Response: Returns questions without exposing correct answers
json[
  {
    "id": 1,
    "questionTitle": "What is Java?",
    "option1": "Programming Language",
    "option2": "Coffee",
    "option3": "Island",
    "option4": "Framework"
  }
]
Submit Quiz
httpPOST /quiz/submit/1
Content-Type: application/json

[
  { "id": 1, "response": "A language" },
  { "id": 5, "response": "Use of pointers" },
  { "id": 6, "response": "4 bytes" }
]
Response:
json{
  "score": 2,
  "totalQuestions": 3
}

🎯 Sample Usage Flow

Add Questions → POST /question/add
Create Quiz → POST /quiz/create?category=java&numQ=5&title=JavaBasics
Get Quiz → GET /quiz/get/1 (Returns questions without answers)
Submit Answers → POST /quiz/submit/1 (Get your score!)


🔮 Future Enhancements

🔐 User authentication (JWT)
📈 Quiz history & analytics
⏱️ Timer-based quizzes
👨‍💼 Admin dashboard
🏆 Leaderboard system
📊 Difficulty-based scoring
🎨 Frontend integration


🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

Fork the project
Create your feature branch (git checkout -b feature/AmazingFeature)
Commit your changes (git commit -m 'Add some AmazingFeature')
Push to the branch (git push origin feature/AmazingFeature)
Open a Pull Request


👨‍💻 Author
Viswa
Spring Boot Developer | REST APIs | PostgreSQL



🙏 Acknowledgments

Spring Boot Documentation
PostgreSQL Community
Telusko YouTube Channel


<div align="center">
⭐ Star this repository if you found it helpful!
Made with ❤️ and ☕ by Viswa
</div>
