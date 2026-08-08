# 🎓 AOU Study Tracker

> **A full-stack academic platform that helps university students organize courses, practice questions, track learning progress, and generate AI-powered questions.**

**AOU Study Tracker** is a multi-service educational platform designed to provide university students with a centralized environment for studying, practicing, and monitoring their academic progress.

---

## ✨ Features

### 👨‍🎓 Student Experience

* 🔐 User registration and authentication
* 📚 Course browsing and selection
* 📝 Multiple-choice question (MCQ) practice
* ✍️ Essay / long-answer question practice
* 📊 Course-specific progress tracking
* 📈 Percentage-based learning progress
* 🎯 Personalized study dashboard
* ✅ Answer submission and evaluation

### 🤖 AI-Powered Features

* AI-generated educational questions
* Dedicated Python AI service
* Flask API integration
* Hugging Face API integration
* Communication between the main backend and AI service

### 📊 Content Management

* Bulk educational content import through Excel
* Structured question storage
* Course and subject organization
* Database-driven educational content

---

## 🏗️ Architecture

The application follows a **multi-service architecture** built around three main components:

```text
                    ┌─────────────────┐
                    │     Student     │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    Frontend     │
                    │ HTML / Tailwind │
                    │      / JS       │
                    └────────┬────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │       Node.js Backend        │
              │         Express.js API       │
              └───────────┬───────────┬──────┘
                          │           │
                          │           ▼
                          │    ┌───────────────┐
                          │    │  AI Service   │
                          │    │ Python/Flask  │
                          │    │ Hugging Face  │
                          │    └───────────────┘
                          │
                          ▼
                  ┌───────────────┐
                  │    MongoDB    │
                  │    Database   │
                  └───────────────┘
```

### Request Flow

1. The student interacts with the frontend.
2. The frontend communicates with the Node.js / Express backend through REST APIs.
3. The backend manages authentication, courses, questions, and progress.
4. MongoDB stores application and educational data.
5. AI-related requests are forwarded to the Python / Flask service.
6. The AI service communicates with the Hugging Face API.
7. Generated questions are returned to the backend and displayed to the student.

---

## 🛠️ Tech Stack

| Layer               | Technologies                          |
| ------------------- | ------------------------------------- |
| **Frontend**        | HTML5, Tailwind CSS, JavaScript, GSAP |
| **Backend**         | Node.js, Express.js                   |
| **Database**        | MongoDB, Mongoose                     |
| **AI Service**      | Python, Flask, Hugging Face API       |
| **Deployment**      | Render, Vercel / Netlify              |
| **API Testing**     | Postman                               |
| **Version Control** | Git, GitHub                           |
| **System Design**   | Draw.io                               |

---

## 📂 Project Structure

```text
AOU_Study_Tracker_Project/
│
├── backend/
│   ├── models/
│   │   ├── User.js
│   │   ├── Subject.js
│   │   ├── Question.js
│   │   └── Progress.js
│   │
│   ├── routes/
│   │   ├── subjects.js
│   │   ├── questions.js
│   │   ├── progress.js
│   │   └── ai.js
│   │
│   ├── scripts/
│   │   └── seed.js
│   │
│   ├── data/
│   │   └── questions.xlsx
│   │
│   ├── server.js
│   ├── package.json
│   └── .env
│
├── ai/
│   ├── app.py
│   ├── requirements.txt
│   └── ...
│
├── frontend/
│   ├── src/
│   │   ├── config.js
│   │   ├── index.html
│   │   ├── home.html
│   │   ├── courses.html
│   │   ├── course-details.html
│   │   ├── practice.html
│   │   ├── mcq.html
│   │   ├── long-questions.html
│   │   ├── select-courses.html
│   │   ├── register.html
│   │   ├── img/
│   │   └── data/
│   │
│   └── README.md
│
└── README.md
```

---

## 🤖 AI Question Generation

The AI functionality is implemented as a **separate Python service**, allowing the AI component to operate independently from the main backend.

```text
Python
   │
   ▼
Flask API
   │
   ▼
Hugging Face API
   │
   ▼
Generated Questions
```

This separation keeps the AI service independent from the Node.js backend and makes the system easier to maintain and extend.

---

## 📊 Progress Tracking

The platform provides percentage-based progress tracking for individual courses.

Progress can be associated with:

* Questions attempted
* Correct answers
* Course completion
* Practice activity

Example:

```text
Course Progress
████████████████░░░░ 80%
```

---

## 📥 Excel Data Import

Educational content can be prepared and imported through Excel files, allowing large amounts of structured content to be added without manually entering every question.

Imported data may include:

* Course / Subject
* Question
* Question type
* Options
* Correct answer
* Additional educational content

---

## 📡 API

The backend exposes RESTful endpoints for the main application functionality.

### Subjects

```http
GET /api/subjects
```

Retrieve available subjects and courses.

### Questions

```http
GET  /api/questions
POST /api/questions
```

Retrieve and manage educational questions.

### Progress

```http
GET  /api/progress
POST /api/progress
```

Track and update student learning progress.

### AI

```http
POST /api/ai
```

Send requests for AI-generated educational questions.

> **Note:** Endpoint availability may vary depending on the current backend implementation.

---

## 🚀 Getting Started

### Prerequisites

Make sure the following are installed:

* Node.js
* npm
* Python 3.x
* MongoDB
* Git
* VS Code
* Live Server extension

### 1. Clone the Repository

```bash
git clone https://github.com/srcode11/srcode11.git
cd AOU_Study_Tracker_Project
```

### 2. Start the Backend

```bash
cd backend
npm install
npm start
```

Backend:

```text
http://localhost:5001
```

### 3. Start the AI Service

Open another terminal:

```bash
cd ai
pip install -r requirements.txt
python app.py
```

AI service:

```text
http://localhost:5002
```

### 4. Start the Frontend

Open:

```text
frontend/src
```

Run the project using **Live Server** in VS Code.

The frontend API configuration is located in:

```text
frontend/src/config.js
```

---

## 🔐 Environment Variables

Create a `.env` file inside the `backend` directory:

```env
PORT=5001
MONGODB_URI=your_mongodb_connection_string
```

If additional API configuration is required for the AI service, add the required variables to its environment.

> ⚠️ **Never commit API keys, passwords, database credentials, or other secrets to GitHub.**

---

## 🧪 Testing

API endpoints can be tested using **Postman**.

Testing covers the main backend functionality, including:

* Authentication
* Subjects
* Questions
* Progress
* AI requests
* API responses

---

## 📐 System Design

The project includes system-design diagrams created with Draw.io:

* **Use Case Diagram** — system actors and their interactions
* **Class Diagram** — core entities and relationships
* **Sequence Diagram** — system interaction flow when submitting answers
* **System Sequence Diagram (SSD)** — student-to-system interaction

Core entities include:

```text
User
Subject
Question
Progress
AI Question Generator
```

---

## 🎯 Project Goals

The project was designed to:

* Provide a centralized digital study environment
* Simplify access to courses and practice questions
* Help students monitor academic progress
* Reduce manual question creation through AI-assisted generation
* Provide a scalable backend architecture
* Centralize educational content management
* Support efficient bulk content management through Excel

---

## 🔮 Future Improvements

Potential improvements include:

* 📱 Mobile application
* 🔔 Study reminders and notifications
* 📅 Personalized study schedules
* 📈 Advanced learning analytics
* 🧠 More advanced AI-generated question types
* 🎯 Personalized recommendations based on performance
* 🏆 Gamification and achievement systems
* 👥 Student discussion and collaboration
* 🌐 Expanded multilingual support

---

sity learning.
</p>
