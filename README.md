# 🧭 Service-Registry

A service discovery server built on Netflix Eureka. All microservices register themselves here on startup, allowing the API Gateway and other services to locate them dynamically by name rather than hardcoded URLs.

## 📌 Student & Project Information

| Field | Details |
|---|---|
| **Student Name** | Sathindu Sathsara Kumara |
| **Student Number** | 241711053 |
| **GCP Project ID** | sathindu-gcp-lab |
| **Submission Type** | Alternative Option (Capstone Project) |

## 📖 About

This project is part of the Enterprise Cloud Application (ECA) module in the Higher Diploma in Software Engineering (HDSE) program at the Institute of Software Engineering (IJSE). It is intended exclusively for students enrolled in this program.

Service-Registry is the central directory for the entire ECA microservices platform. Every service — Api-Gateway, Student-Service, Program-Service, and Enrollment-Service — registers itself here on startup, enabling dynamic, name-based service discovery instead of fragile hardcoded URLs.

## 🛠️ Tech Stack

| Technology | Details |
|---|---|
| **Java** | 25 |
| **Spring Boot** | 4.1.0 |
| **Spring Cloud** | 2025.1.2 |
| **Spring Cloud Netflix Eureka Server** | Service discovery |
| **Spring Cloud Config Client** | Fetches config from Config-Server |

## 🔍 How It Works

The Service-Registry acts as the central directory for the microservices architecture. When a service starts, it registers with this server. The Api-Gateway queries this registry to resolve service locations using load-balanced URIs (e.g., `lb://STUDENT-SERVICE`).

## ⚙️ Service Details

| Property | Value |
|---|---|
| **Port** | 9001 |
| **Artifact ID** | Service-Registry |
| **Group ID** | lk.ijse.eca |
| **Config Source** | `http://localhost:9000` (Config-Server) |

## 🏛️ How This Service Fits the Architecture

```text
┌────────────────────────────┐
│    Config-Server (9000)    │
└──────────────┬─────────────┘
               │ config on startup
               ▼
┌────────────────────────────┐
│   Service-Registry (9001)  │
│   Netflix Eureka Server    │
└──────────────┬─────────────┘
               │ registration & discovery
   ┌───────────┼────────────┬──────────────┬────────────────┐
   ▼           ▼            ▼              ▼                ▼
Api-Gateway Student-     Program-       Enrollment-      (future
(7000)      Service      Service        Service          services)
            (8000)       (8001)         (8002)
```

## 🚀 Getting Started

Follow the lecture guidelines, refer to the lecture video for more information and how to get started correctly.

⚠️ **Important:** Config-Server must be running before starting the Service-Registry, as it fetches its configuration from Config-Server on startup.

### 🔢 Startup Order

| Step | Service | Port |
|---|---|---|
| 1️⃣ | Config-Server | 9000 |
| 2️⃣ | Service-Registry | 9001 |
| 3️⃣ | Other services (Api-Gateway, Student, Program, Enrollment) | — |

### ▶️ Run the Service

```bash
./mvnw spring-boot:run
```
The Eureka dashboard will be available at: `http://localhost:9001`

## 💬 Need Help?

If you encounter any issues, feel free to reach out and start a discussion via the Slack workspace.

## 📄 License

This project was developed as part of the Enterprise Cloud Architecture university module (Capstone Project — Alternative Option).
