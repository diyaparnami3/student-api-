# Student API

Simple Spring Boot REST API using an in-memory ArrayList.

## Requirements
- Java 17+
- Maven

## Run
```bash
mvn spring-boot:run
```

Server:
http://localhost:8080

## Endpoints

GET /students
GET /students/{id}
POST /students
PUT /students/{id}
DELETE /students/{id}

Example POST body:
```json
{
  "id": 1,
  "name": "Diya",
  "email": "diya@gmail.com",
  "course": "CSE"
}
```
Jenkins SCM polling test
