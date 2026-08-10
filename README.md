# 🎓 ProctorZ

### AI-Powered Online Proctoring — Real-Time, Intelligent & Privacy-Focused

**ProctorZ** is a full-stack AI-powered online examination and proctoring platform designed to make remote assessments more secure, transparent, and efficient.

The platform combines **real-time AI-based monitoring, automated violation detection, WebSocket communication, role-based dashboards, and online examination management** into a single system for Students, Teachers, and Administrators.

A key design principle of ProctorZ is **privacy-first proctoring**: face and behavioral analysis are performed directly in the student's browser, so the student's video stream does not need to be continuously uploaded to the backend.

---

## 🚀 Working Prototype

🔗 **Live Working Prototype:**
**[https://proctor-z.vercel.app/]**

The prototype demonstrates the complete examination workflow, including:

* Student registration and login
* Teacher exam creation
* Exam joining using a unique code
* Online examination interface
* Real-time AI proctoring
* Face and multi-person detection
* Gaze and head-pose monitoring
* Audio risk monitoring
* Automatic violation generation
* Real-time teacher monitoring
* Exam submission and scoring
* Violation and performance reports
* Role-based dashboards

> **Note:** The prototype link provides access to the working application. The source code is not publicly hosted.

---

# 🎯 Problem Statement

Traditional online examinations face several challenges:

* Difficulty monitoring students remotely
* Possibility of unauthorized assistance
* Multiple people appearing during an examination
* Students looking away from the examination screen
* Lack of real-time visibility for teachers
* Manual review of suspicious behavior
* Difficulty maintaining detailed examination records

ProctorZ addresses these challenges by combining **AI-powered browser monitoring with real-time communication and centralized examination management**.

---

# 💡 Proposed Solution

ProctorZ provides an intelligent online examination environment where student activity can be monitored automatically during an exam.

The system continuously analyzes the student's camera and microphone signals locally in the browser and identifies potentially suspicious behavior.

When a violation is detected:

```text
Student Browser
      │
      │ AI Monitoring
      ▼
Violation Detected
      │
      │ WebSocket
      ▼
Django Backend
      │
      │ Redis Channel Layer
      ▼
Teacher Dashboard
      │
      ▼
Real-Time Alert
```

This allows teachers to monitor multiple students without requiring continuous video streaming to the server.

---

# ✨ Key Features

| Feature                      | Description                                                     |
| ---------------------------- | --------------------------------------------------------------- |
| 🤖 **AI Proctoring**         | Real-time face detection, gaze tracking and head-pose analysis  |
| 👥 **Multi-Face Detection**  | Detects when more than one person appears in the camera frame   |
| 👁️ **Gaze Monitoring**      | Identifies potentially suspicious looking-away behavior         |
| 🎙️ **Audio Monitoring**     | Provides a real-time audio risk indicator                       |
| 📡 **Real-Time Monitoring**  | Sends detected violations to teachers through WebSockets        |
| 🚨 **Violation Management**  | Categorizes violations into low, medium and high severity       |
| 🔑 **Exam Join Codes**       | Generates unique six-character codes for examinations           |
| ⏱️ **Automatic Submission**  | Automatically submits an examination when the timer expires     |
| 📊 **Performance Analytics** | Displays examination scores and violation statistics            |
| 🤖 **ProctorZ AI Assistant** | AI-powered assistant for interacting with the platform          |
| 🔐 **Role-Based Access**     | Separate capabilities for Students, Teachers and Administrators |
| 🌙 **Dark/Light Mode**       | Supports both light and dark themes                             |
| 📱 **Responsive Interface**  | Designed for desktop and mobile screen sizes                    |

---

# 👨‍🎓 Student Dashboard

Students have access to a dedicated dashboard containing:

### 🏠 Overview

* Upcoming examinations
* Recent violations
* Performance summary
* Examination activity

### 📚 My Exams

* Completed examinations
* Examination history
* Scores and results

### 🔑 Join Exam

Students can enter a unique examination code to join an active exam.

### ⚠️ Violations

Students can view their recorded proctoring violations and their severity.

### 👤 Profile

Students can manage their profile information such as:

* Name
* Bio
* Department
* Avatar

---

# 👨‍🏫 Teacher Dashboard

Teachers can manage examinations and monitor students through a dedicated dashboard.

### 📊 Statistics

Teachers can view:

* Total examinations
* Number of students
* Submissions
* Detected violations

### 📝 Examination Management

Teachers can:

* Create examinations
* Add questions
* Edit examinations
* Activate/deactivate examinations
* Delete examinations
* Generate examination join codes

### 👥 Student Management

Teachers can view enrolled students and their examination activity.

### 🔴 Live Monitoring

The live monitoring dashboard provides real-time information about violations detected during an active examination.

For example:

```text
Student A
   ↓
Looking Away
   ↓
Medium Severity
   ↓
WebSocket
   ↓
Teacher Dashboard
```

Teachers can therefore identify potentially suspicious activity while the examination is in progress.

### 📈 Results

Teachers can view:

* Student scores
* Examination submissions
* Proctoring reports
* Violation statistics

### ⚠️ Violation Analytics

Violation data is presented using charts and student-level breakdowns to help teachers identify unusual activity.

---

# 🛡️ Administrator Dashboard

The Super Admin dashboard provides platform-wide management.

### 📊 Platform Statistics

Provides an overview of:

* Total users
* Examinations
* Submissions
* Violations
* Platform activity

### 👥 User Management

Administrators can:

* View users
* Activate/deactivate accounts
* Manage user roles

### 📝 Examination Management

Administrators can monitor examinations across the platform.

### ⚠️ Violation Management

Provides a complete platform-wide view of recorded violations.

### 🗒️ Audit Logs

Important administrative actions can be tracked through audit logs.

### ⚙️ System Settings

Platform-level configuration can be managed by administrators.

---

# 🤖 AI-Powered Proctoring

One of the main components of ProctorZ is its AI-based proctoring system.

The student's browser uses computer-vision models to analyze the camera feed.

### AI Monitoring Pipeline

```text
Student Camera
      ↓
Browser
      ↓
AI / Computer Vision
      ↓
Face Detection
      ↓
Gaze Analysis
      ↓
Head Pose Analysis
      ↓
Behavior Evaluation
      ↓
Violation Detection
```

### Face Detection

The system detects whether the student is visible in the camera.

Possible situations include:

* No face detected
* One face detected
* Multiple faces detected

### Multi-Face Detection

If multiple people appear in the camera frame, the system can generate a violation.

```text
1 Person  → Normal

0 People → Possible Violation

2+ People → High-Risk Violation
```

### Gaze Tracking

The system analyzes the student's eye direction to identify potentially suspicious looking-away behavior.

### Head Pose Analysis

Head orientation is analyzed to detect significant changes in viewing direction.

### Audio Monitoring

The platform provides an audio risk indicator that can help identify unusual audio activity during an examination.

---

# 🔐 Privacy-Focused Architecture

A major design decision in ProctorZ is that **AI-based camera analysis is performed on the client side**.

Instead of continuously uploading the student's video stream:

```text
Student Camera
      ↓
Browser
      ↓
AI Processing
      ↓
Violation Event
      ↓
Backend
```

Only relevant examination and violation information is communicated to the backend.

### Privacy Advantage

This architecture helps:

* Reduce unnecessary video transmission
* Reduce server-side video processing
* Reduce bandwidth requirements
* Improve privacy
* Make the system more scalable

> ProctorZ is designed around the principle of sending **events and metadata rather than continuously streaming the student's video to the server**.

---

# 📡 Real-Time WebSocket Communication

ProctorZ uses **WebSockets** to provide real-time communication between the student examination environment and teacher monitoring dashboard.

The architecture uses:

* Django Channels
* Daphne
* Redis Channel Layer

### Real-Time Flow

```text
Student Browser
      │
      │ Violation Event
      ▼
Django Channels
      │
      ▼
Redis
      │
      ▼
Teacher Monitoring Dashboard
      │
      ▼
Real-Time Alert
```

This allows teachers to receive violation events without repeatedly refreshing the dashboard.

---

# 🏗️ System Architecture

The overall architecture consists of three major layers.

```text
                 ┌──────────────────────┐
                 │   Student Browser    │
                 │                      │
                 │  React Application   │
                 │  AI Proctoring       │
                 │  Exam Interface      │
                 └──────────┬───────────┘
                            │
                   REST / WebSocket
                            │
                            ▼
                 ┌──────────────────────┐
                 │   Django Backend     │
                 │                      │
                 │ REST APIs            │
                 │ Authentication       │
                 │ Exam Management      │
                 │ Violation Management │
                 │ WebSocket Consumers  │
                 └───────┬───────┬──────┘
                         │       │
                    MongoDB     Redis
                         │       │
                         ▼       ▼
                 ┌──────────────────────┐
                 │   Persistent Data    │
                 │   & Real-Time Layer  │
                 └──────────────────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │  Teacher Dashboard   │
                 │                      │
                 │ Live Monitoring      │
                 │ Results              │
                 │ Violation Analytics  │
                 └──────────────────────┘
```

---

# 🧩 Technology Stack

## Frontend

* React 18
* Vite
* React Router
* Axios
* Tailwind CSS
* Framer Motion
* Recharts

## Backend

* Python
* Django
* Django REST Framework
* Django Channels
* Daphne

## Database & Real-Time Infrastructure

* MongoDB
* PyMongo
* Redis

## Authentication & Security

* JWT
* bcrypt
* Google OAuth 2.0
* Role-Based Access Control

## AI & Machine Learning

* face-api.js
* Browser-based computer vision
* Google Gemini for ProctorZ AI Assistant

## Deployment

* Vercel
* Render

---

# 🔑 Authentication & Authorization

ProctorZ implements multiple layers of access control.

### JWT Authentication

Users authenticate through JWT-based authentication.

### Google OAuth

Users can also authenticate using Google OAuth 2.0.

### Role-Based Access Control

The platform supports three major roles:

```text
                 ProctorZ
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
     Student     Teacher      Admin
        │           │           │
        ▼           ▼           ▼
     Take Exam   Manage Exam   Manage Platform
     View Result Monitor       Manage Users
     View Alerts View Results  Audit Logs
```

Each role receives access only to the functionality relevant to that role.

---

# 🚨 Violation Management

ProctorZ maintains a structured violation system.

Violations are categorized based on severity:

```text
LOW
 │
 ├── Minor suspicious behavior
 │
MEDIUM
 │
 ├── Repeated suspicious behavior
 │
HIGH
 │
 └── Critical suspicious behavior
```

The platform maintains violation information that can be used for:

* Student-level reports
* Examination-level reports
* Teacher monitoring
* Administrative analysis
* Performance review

---

# ⏱️ Automated Examination Workflow

The examination process follows a structured workflow.

```text
Teacher Creates Exam
        ↓
Exam Activated
        ↓
Unique Join Code Generated
        ↓
Student Enters Code
        ↓
Exam Environment Initialized
        ↓
AI Proctoring Starts
        ↓
Student Answers Questions
        ↓
Violations Monitored
        ↓
Exam Timer Ends
        ↓
Automatic Submission
        ↓
Score Generated
        ↓
Proctoring Report Generated
```

---

# 🤖 ProctorZ AI Assistant

The platform also includes an AI assistant designed to provide an interactive way of accessing information and assistance within the application.

The assistant is powered by **Google Gemini** and is integrated into the ProctorZ platform through a backend AI endpoint.

Potential use cases include:

* General platform assistance
* Examination-related questions
* Understanding examination results
* Interacting with platform information

---

# 📊 Analytics & Reporting

ProctorZ provides visual analytics for teachers and administrators.

The dashboards can display:

* Total examinations
* Student participation
* Submission statistics
* Examination scores
* Violation counts
* Violation severity
* Student-level violation breakdown

Charts are implemented using **Recharts**.

This allows teachers to understand examination activity without manually analyzing raw records.

---

# 🌐 Responsive User Interface

The application is designed to work across different screen sizes.

The interface includes:

* Responsive dashboards
* Mobile navigation
* Dark/light theme
* Interactive cards
* Tables
* Charts
* Real-time monitoring components

---

# 🔄 Complete End-to-End Flow

The complete ProctorZ system can be summarized as:

```text
                    TEACHER
                       │
                       ▼
                 Create Exam
                       │
                       ▼
                Generate Code
                       │
                       ▼
                    STUDENT
                       │
                       ▼
                 Join Exam
                       │
                       ▼
              Start Proctoring
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Camera        Gaze         Audio
          │            │            │
          └────────────┼────────────┘
                       ▼
                AI Analysis
                       │
                       ▼
              Violation Detection
                       │
                       ▼
                  WebSocket
                       │
                       ▼
                   Teacher
                       │
                       ▼
               Live Monitoring
                       │
                       ▼
                Exam Submission
                       │
                       ▼
                 Results & Report
```

---

# 💡 Key Innovation

The primary design idea behind ProctorZ is the combination of:

### 1. Client-Side AI

AI-based monitoring occurs directly within the student's browser.

### 2. Real-Time Communication

WebSockets allow teachers to receive violation events immediately.

### 3. Privacy-Focused Design

The system avoids continuously transmitting the student's video to the backend.

### 4. Role-Based Platform

Students, Teachers and Administrators receive separate dashboards and permissions.

### 5. Automated Monitoring

The platform automatically detects and records suspicious activity instead of relying entirely on manual observation.

---

# 📈 Scalability Considerations

The architecture is designed with scalability in mind.

### Redis

Redis acts as the channel layer for real-time WebSocket communication.

### Client-Side AI

Performing AI processing in the browser reduces the computational workload on the backend.

### MongoDB

MongoDB provides a flexible data model suitable for examination and proctoring metadata.

### REST + WebSocket Architecture

REST APIs handle standard application operations while WebSockets handle real-time events.

This separation allows each communication mechanism to be used for its appropriate purpose.

---

# 🎯 Project Outcomes

ProctorZ demonstrates how modern web technologies and AI can be combined to build an intelligent online examination platform.

The project brings together:

* Full-stack development
* Artificial intelligence
* Computer vision
* Real-time communication
* Database management
* Authentication
* Cloud deployment
* Role-based access control
* Data visualization

It provides a practical example of building a **privacy-conscious, real-time AI-enabled web application**.

---

# 🛠️ Project Highlights

### Full-Stack Development

Built an end-to-end platform using React and Django.

### AI Integration

Integrated browser-based computer vision for real-time examination monitoring.

### Real-Time Systems

Implemented WebSocket-based communication using Django Channels and Redis.

### Secure Authentication

Implemented JWT authentication, password hashing, Google OAuth and role-based authorization.

### Data Management

Used MongoDB for flexible storage of examination, submission and violation information.

### Cloud Deployment

Deployed the frontend and backend as separate cloud services.

---

### Responsibilities

* Designed the overall application architecture
* Developed the React frontend
* Developed Django REST APIs
* Implemented authentication and authorization
* Integrated AI-based proctoring
* Implemented real-time WebSocket communication
* Designed examination and violation workflows
* Integrated MongoDB and Redis
* Developed Student, Teacher and Admin dashboards
* Implemented analytics and reporting
* Integrated Gemini-powered AI assistance
* Worked on cloud deployment and application integration

---

# 📌 Project Information

**Project:** ProctorZ
**Category:** AI / Full-Stack / EdTech
**Type:** Online Examination & AI Proctoring Platform
**Frontend:** React + Vite
**Backend:** Django + Django REST Framework
**Database:** MongoDB
**Real-Time:** Django Channels + Redis
**AI:** face-api.js + Google Gemini
**Authentication:** JWT + Google OAuth 2.0
**Deployment:** Vercel + Render

---

# 🔗 Working Prototype

### 🚀 Try ProctorZ

**Live Prototype:**
**[[proctor-z.vercel.app](https://proctor-z.vercel.app/)]**

The prototype demonstrates the main functionality of the ProctorZ platform and provides an interactive view of the student, teacher, examination and proctoring workflows.

---

# 👨‍💻 Author

**Sumanth Nagireddy**

### ProctorZ

*Built with ❤️ to explore the future of secure, intelligent and privacy-focused online examinations.*
