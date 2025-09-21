🚀 Deployment in Google Cloud Platform (GCP)


🌟 Project Overview

This repository contains my Enterprise Cloud Architecture assignment, demonstrating how to deploy a Spring Boot application with MySQL using Google Cloud SQL.

The project highlights:

Creating and configuring a Cloud SQL MySQL instance

Connecting it to a Spring Boot application

Running the app with a cloud-hosted database

🎥 Demo Video

📌 Watch the Demonstration - https://drive.google.com/file/d/1px0k0kVq5zW2zY6Zak0jRXP_Uvknzf8i/view?usp=sharing

⚙️ Google Cloud MySQL Configuration Guide
Phase 1: Access Google Cloud Console

Navigate to: Google Cloud SQL

Ensure you are working in the correct GCP project.

Phase 2: Create a Cloud SQL Instance

Click Create Instance → Choose MySQL.

Select MySQL 8.0 (recommended).

Set Instance ID (e.g., mysqldb-instance).

Configure root password (e.g., Mysql-ECA1!).

Choose Region (e.g., us-central1).

Availability: Single Zone (sufficient for development).

Phase 3: Configure Public IP Access

Open your instance → go to Connections.

Under Public IP, click Add network.

Name: development-access

IP Range: 0.0.0.0/0 ⚠️ (Development only – not secure for production!)

Save and note the Public IP (e.g., 34.133.212.154).

Phase 4: Create a Database

Connect to the instance via Cloud Shell or local terminal:

docker run -it --rm mysql:8 mysql -h <YOUR_PUBLIC_IP> -u root -p


Example:

docker run -it --rm mysql:8 mysql -h 34.133.212.154 -u root -p


Enter your root password, then create the database:

CREATE DATABASE eca_courses;
SHOW DATABASES;


You should see eca_courses in the list. ✅

Phase 5: Spring Boot Integration

Update your application-gcp.properties:

spring.datasource.url=jdbc:mysql://<PUBLIC_IP>:3306/eca_courses?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=YOUR_PASSWORD
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

server.port=8081


Run your Spring Boot application → it should now connect to Cloud SQL MySQL.

🚀 Getting Started

Clone the repository

Update the application-gcp.properties with your Cloud SQL credentials.

Start the Spring Boot application:

mvn spring-boot:run


Access the app in your browser:
👉 http://localhost:8081

📄 License - (LICENCE)

This project is licensed under the MIT License.
