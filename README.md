# 🚗 Car Doctor Pro
> **"Diagnose Smarter. Repair Confidently."**  
> A Complete Professional iFixit-Inspired Vehicle Diagnosis and Repair Platform built with Java 17+, Spring Boot 3.x, MySQL 8+, Flyway, and an AI-Augmented Automotive Assistance Engine.

---

## 🌟 Overview
**Car Doctor Pro** is a full-stack automotive engineering platform designed to eliminate guesswork in vehicle troubleshooting and empower owners with transparent, verified repair tutorials. Inspired by the clarity and structured checklists of **iFixit**, it specializes exclusively in automobiles, multi-step symptom-to-cause diagnostic inference, and workshop safety standards.

### Key Capabilities
1. **Interactive Vehicle Diagnosis Wizard**:
   - Multi-step diagnostic workflow: select vehicle &rarr; select primary symptom &rarr; answer targeted powertrain questions &rarr; describe symptoms &rarr; view clinical diagnosis report.
   - Transparent rules-based diagnostic engine ranking possible causes by calibrated confidence scores.
   - Non-negotiable physical safety rules service with emergency **STOP DRIVING** directives for brake failures, severe overheating boil-over, and fuel leaks.
2. **Searchable Repair Guide Library**:
   - iFixit-style repair tutorials with step numbers, tool requirements, replacement parts checklists, and safety warning banners.
   - Interactive checkbox for every completed step with real-time percentage progress bar.
   - Tutorial progress and favorites persist across sessions for authenticated drivers.
3. **"Dr. Car" AI Mechanic Assistant**:
   - Floating, responsive chatbot available on all pages.
   - Context-aware: incorporates the active vehicle (brand, model, year, fuel type).
   - Intelligent rule-based fallback when no external LLM API key is configured.
   - Refuses dangerous or illegal vehicle actions (e.g., cutting brake lines, probing EV high-voltage cables, opening hot radiators).
4. **Vehicle Selector & Garage**:
   - Dependent cascading dropdowns: Brands &rarr; Models &rarr; Production Years &rarr; Fuel Types &rarr; Transmissions.
   - Pre-populated with Indian and global automotive manufacturers (Maruti Suzuki, Tata Motors, Mahindra, Hyundai, Honda, Toyota, Kia, Renault, Volkswagen, Skoda, MG, Nissan).
5. **Driver Profile & Maintenance**:
   - Saved vehicle garage management.
   - Diagnostic history log.
   - Scheduled maintenance reminder tracking (due dates & odometer milestones).
6. **Administrator Dashboard**:
   - Live telemetry and chart visualizations (Chart.js) for diagnoses by category and guides by difficulty.
   - Complete CRUD interfaces to publish tutorials and configure diagnostic rules.
   - Security audit trail and community user feedback moderation.

---

## 🛠️ Technology Stack
- **Backend**:
  - Java 17+ (JDK 27 tested and verified)
  - Spring Boot 3.3.5
  - Spring Web REST APIs
  - Spring Data JPA (Hibernate 6)
  - Spring Security with Stateless JWT Authentication & BCrypt Password Hashing
  - Bean Validation (`jakarta.validation`)
  - Spring Boot Actuator
  - Flyway Database Migrations
- **Database**:
  - MySQL 8+ production support (`application-mysql.properties`)
  - Zero-config H2 database in MySQL compatibility mode for instant local execution
- **Frontend**:
  - HTML5, CSS3, Modern ES6+ JavaScript
  - Bootstrap 5.3.3 & Bootstrap Icons
  - Chart.js 4.4.4
  - Glassmorphic UI with dark charcoal (`#0c1013`), deep forest green (`#071f18`), and bright lime green (`#00e676`) accents
  - Reduced-motion accessibility (`prefers-reduced-motion: reduce`)
- **Testing**:
  - JUnit 5 & Mockito
  - Unit and integration tests for diagnostic rules, safety directives, and authentication

---

## 📂 Project Structure
```
cardoctor/
├── pom.xml                                      # Maven dependencies and build plugins
├── .env.example                                 # Sample environment variables
├── .gitignore
├── README.md                                    # Documentation
├── src/
│   ├── main/
│   │   ├── java/com/cardoctorpro/
│   │   │   ├── CarDoctorProApplication.java     # Spring Boot Entry Point
│   │   │   ├── config/                          # Security, OpenAPI, App config
│   │   │   │   ├── OpenApiConfig.java
│   │   │   │   └── SecurityConfig.java
│   │   │   ├── controller/                      # REST API Endpoints
│   │   │   │   ├── AdminController.java
│   │   │   │   ├── AuthController.java
│   │   │   │   ├── CategoryController.java
│   │   │   │   ├── ChatbotController.java
│   │   │   │   ├── DiagnosisController.java
│   │   │   │   ├── GuideController.java
│   │   │   │   ├── UserController.java
│   │   │   │   └── VehicleController.java
│   │   │   ├── dto/                             # Data Transfer Objects
│   │   │   ├── entity/                          # JPA Entities
│   │   │   ├── exception/                       # Custom exceptions & global handler
│   │   │   ├── repository/                      # Spring Data Repositories
│   │   │   ├── security/                        # JWT Provider & UserDetailsService
│   │   │   └── service/                         # Business & Diagnostic Logic
│   │   │       ├── AdminService.java
│   │   │       ├── AuthService.java
│   │   │       ├── ChatbotService.java
│   │   │       ├── DiagnosticEngineService.java
│   │   │       ├── GuideService.java
│   │   │       ├── SafetyRulesService.java
│   │   │       ├── UserService.java
│   │   │       └── VehicleService.java
│   │   └── resources/
│   │       ├── application.yml                  # Default application configuration
│   │       ├── application-mysql.properties     # MySQL 8+ production profile
│   │       ├── db/migration/
│   │       │   ├── V1__init_schema.sql          # Flyway schema initialization
│   │       │   └── V2__seed_data.sql            # Automotive brands, models & guides
│   │       └── static/                          # Production Web Frontend
│   │           ├── index.html                   # Home page
│   │           ├── diagnose.html                # Vehicle Diagnosis Wizard
│   │           ├── guides.html                  # Repair Guide Library
│   │           ├── guide-detail.html            # Step-by-Step Tutorial
│   │           ├── vehicles.html                # Vehicle Selection & Garage
│   │           ├── profile.html                 # Profile, History & Reminders
│   │           ├── admin.html                   # Administrator Dashboard
│   │           └── assets/
│   │               ├── css/style.css            # Dark/forest/lime design system
│   │               └── js/
│   │                   ├── api.js               # Central API Client
│   │                   ├── app.js               # Common UI logic
│   │                   └── chatbot.js           # Dr. Car floating assistant
│   └── test/
│       └── java/com/cardoctorpro/service/
│           ├── AuthServiceTest.java             # Auth & JWT unit tests
│           ├── DiagnosticEngineServiceTest.java # Diagnostic inference tests
│           └── SafetyRulesServiceTest.java       # Safety override tests
```

---

## 🚀 Quick Start Guide

### 1. Prerequisites
- **Java Development Kit (JDK)**: Java 17 or higher (tested with Oracle JDK 27).
- **Maven**: Apache Maven 3.9+ (bundled or installed).
- **MySQL 8+** (Optional - by default, Car Doctor Pro runs zero-config using an embedded file-based database with MySQL compatibility mode).

### 2. Running Unit & Integration Tests
Run all automated test suites:
```bash
mvn test
```
All unit tests in `AuthServiceTest`, `DiagnosticEngineServiceTest`, and `SafetyRulesServiceTest` will execute.

### 3. Running the Application
Launch the Spring Boot server:
```bash
mvn spring-boot:run
```
Once started, the application is live at:
- **Web Platform**: [http://localhost:8080](http://localhost:8080)
- **Interactive Swagger UI**: [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)
- **OpenAPI v3 Docs**: [http://localhost:8080/v3/api-docs](http://localhost:8080/v3/api-docs)
- **Actuator Health**: [http://localhost:8080/actuator/health](http://localhost:8080/actuator/health)

---

## 🗄️ Database Configuration

### Option A: Default Zero-Config Development (Out of the Box)
Car Doctor Pro runs immediately without needing to configure or install MySQL. Flyway automatically executes migrations `V1__init_schema.sql` and `V2__seed_data.sql` on startup.

### Option B: MySQL 8+ Production Setup
1. Create a database in your local or cloud MySQL instance:
   ```sql
   CREATE DATABASE cardoctor CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```
2. Set your environment variables (or update `.env`):
   ```bash
   export SPRING_DATASOURCE_URL="jdbc:mysql://localhost:3306/cardoctor?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC"
   export SPRING_DATASOURCE_USERNAME="root"
   export SPRING_DATASOURCE_PASSWORD="your_password"
   export SPRING_DATASOURCE_DRIVER="com.mysql.cj.jdbc.Driver"
   ```
3. Run with the MySQL profile:
   ```bash
   mvn spring-boot:run -Dspring-boot.run.profiles=mysql
   ```

---

## 🔑 Demo Credentials
Car Doctor Pro includes pre-seeded test accounts for instant evaluation:

| Role | Username | Password | Full Name | Access Level |
|---|---|---|---|---|
| **Administrator** | `admin` | `Admin@123` | Chief Automotive Architect | Full platform control, publishing, telemetry |
| **Mechanic Admin** | `mechanic_dan` | `Admin@123` | Dan Master Mechanic | Guide & diagnostic rule authoring |
| **Driver / User** | `driver_rahul` | `Admin@123` | Rahul Sharma | Garage management, favorites, progress |

---

## 📡 REST API Reference

### Authentication (`/api/auth`)
- `POST /api/auth/register`: Register new user account.
- `POST /api/auth/login`: Authenticate and receive signed JWT.
- `GET /api/auth/me`: Get details of currently authenticated user.

### Vehicles (`/api`)
- `GET /api/brands`: List active vehicle manufacturers.
- `GET /api/brands/{id}/models`: List models for manufacturer.
- `GET /api/models/{id}/variants`: List fuel & engine variants.
- `GET /api/models/{id}/years`: List valid model production years.

### Diagnostics (`/api/diagnosis`)
- `GET /api/diagnosis/symptoms`: List symptoms with severity categories.
- `GET /api/diagnosis/symptoms/{id}`: Get symptom follow-up questions & answer options.
- `POST /api/diagnosis/sessions`: Initialize diagnostic session for a car.
- `POST /api/diagnosis/sessions/{token}/answers`: Submit answers and generate ranked diagnosis report.
- `GET /api/diagnosis/sessions/{token}/results`: Retrieve past diagnosis report.

### Repair Guides (`/api/guides`)
- `GET /api/guides`: Search and filter guides with pagination & sorting (`categoryId`, `difficulty`, `query`, `page`, `size`, `sortBy`).
- `GET /api/guides/featured`: Top 6 repair tutorials.
- `GET /api/guides/{slug}`: Full guide with steps, tools, parts, and safety directives.
- `POST /api/guides/{id}/favorite`: Toggle favorite tutorial.
- `POST /api/guides/{id}/progress`: Synchronize completed step checkboxes.
- `POST /api/guides/{id}/feedback`: Submit user feedback.

### AI Mechanic Assistant Dr. Car (`/api/chat`)
- `POST /api/chat/messages`: Send message and receive vehicle-contextual guidance.
- `GET /api/chat/conversations/{id}/messages`: Load active conversation history.

### User Garage & Profile (`/api/users`)
- `GET /api/users/profile`: Activity metrics & profile.
- `GET /api/users/vehicles`: Saved garage cars.
- `POST /api/users/vehicles`: Add car to garage.
- `DELETE /api/users/vehicles/{id}`: Delete car from garage.
- `GET /api/users/favorites`: User bookmarked guides.
- `GET /api/users/diagnosis-history`: Past diagnosis reports.
- `GET /api/users/reminders`: Scheduled maintenance tasks.
- `POST /api/users/reminders`: Create maintenance reminder.
- `DELETE /api/users/reminders/{id}`: Delete maintenance reminder.

### Admin Dashboard (`/api/admin`)
- `GET /api/admin/dashboard`: Overall statistics and distribution maps.
- `POST /api/admin/guides`: Author and publish new repair tutorial.
- `DELETE /api/admin/guides/{id}`: Delete or archive tutorial.
- `POST /api/admin/diagnostic-rules`: Add symptom-to-cause inference rule.
- `GET /api/admin/audit-logs`: Security audit trail.
- `GET /api/admin/feedback`: Review community feedback.

---

## 🔒 Diagnostic Safety Protocols
Vehicle repair presents inherent physical and electrical hazards. Car Doctor Pro implements a centralized `SafetyRulesService` that supersedes ordinary advice:
1. **Hydraulic Brake Loss**: Immediately displays a red emergency alert banner directing the driver to stop safely, call roadside assistance, and forbids road testing.
2. **Pressurized Cooling System**: Flags severe scald hazards and strictly prohibits opening radiator caps while hot.
3. **High-Voltage EV / Hybrid Systems**: Highlights 400V–800V DC electric shock hazards on orange cabling.
4. **Vehicle Lifting Safety**: Enforces mechanical jack stands and wheel chocks whenever underbody work is mentioned.

---

## 📄 License
This project is licensed under the Apache License 2.0.
