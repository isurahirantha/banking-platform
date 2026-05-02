# Banking Platform

This project is a **Spring Boot multi-module microservices platform** designed for a modern banking application. 

## Technology Stack

* **Java:** 21
* **Spring Boot:** 3.3.4
* **Spring Cloud:** 2023.0.3
* **Build Tool:** Maven

## Architecture Overview

The project is structured with a root `pom.xml` that manages dependency versions centrally and declares all the child modules. The microservices architecture is divided into three main categories:

### 1. Infrastructure Services
These modules form the backbone of the microservices architecture, handling routing, configuration, and service discovery:

* **`eureka-server`**: Acts as the Service Registry. Other microservices register themselves here to discover and communicate with each other dynamically.
* **`config-server`**: Provides centralized configuration management for all microservices, allowing you to manage environment-specific properties in one place.
* **`api-gateway`**: The single entry point into the system for external clients. It routes incoming API requests to the appropriate backend microservices and handles cross-cutting concerns like security, rate limiting, and CORS.

### 2. Core Business Microservices
These modules handle the actual business logic of the banking platform:

* **`auth-service`**: Manages user authentication, authorization, and token generation (JWT/OAuth2).
* **`customer-service`**: Manages user profiles, personal details, and KYC (Know Your Customer) information.
* **`account-service`**: Manages bank accounts, balances, and account-related operations.
* **`fund-transfer-service`**: Handles the logic for moving money between accounts (internal and external transfers).
* **`bill-payment-service`**: Handles utility bill payments and scheduled payments.
* **`card-service`**: Manages credit and debit cards, including issuing, blocking, and limits.

### 3. Support & Security Services
These modules provide auxiliary functions and security mechanisms:

* **`notification-service`**: Responsible for sending out emails, SMS, or push notifications to customers for OTPs, alerts, and transaction receipts.
* **`audit-service`**: Centralizes audit logging, keeping a secure and immutable record of critical actions performed within the system for compliance and tracking.
* **`fraud-service`**: Analyzes transactions and user activities to detect and prevent potentially fraudulent behavior in real-time.
