# Blog Application using Spring Boot, MySQL, and Docker

This repository contains a complete implementation of a blog application built using **Spring Boot**, **MySQL**, and Docker for deployment.

---

## Objectives
- Develop a robust backend system for managing blog posts.
- Implement RESTful APIs for efficient interaction with the application.
- Ensure database persistence using MySQL and Docker volumes.
- Simplify deployment using Docker Compose.

---

## Features
- CRUD operations for managing blog posts.
- RESTful API endpoints.
- MySQL database for persistent data storage.
- Dockerized application for easy deployment.

---

## Technologies Used
- **Backend**: Spring Boot
- **Database**: MySQL
- **Containerization**: Docker
- **Build Tool**: Maven

---

## Project Structure
```
src/main/java/com/example/blogapp
├── controller
│   └── BlogController.java
├── model
│   └── Blog.java
├── repository
│   └── BlogRepository.java
├── service
    ├── BlogService.java
    └── BlogServiceImpl.java
```

---

## How to Run

### 1. Clone the Repository
```bash
git clone <repository-url>
cd blog-application
```

### 2. Build the Application
Use Maven to package the application into a JAR file:
```bash
mvn clean package
```

### 3. Run Using Docker Compose
Ensure Docker is running, then use:
```bash
docker-compose up --build
```

### 4. Test the Application
- Access the application at: `http://localhost:8080`
- Test APIs using tools like Postman:
  - **GET** `/api/blogs` - Retrieve all blogs.
  - **GET** `/api/blogs/{id}` - Retrieve a specific blog.
  - **POST** `/api/blogs` - Create a new blog.
  - **PUT** `/api/blogs/{id}` - Update an existing blog.
  - **DELETE** `/api/blogs/{id}` - Delete a blog.

---

## Environment Configuration
All configurations can be managed in `application.properties`:
```properties
spring.datasource.url=jdbc:mysql://mysql:3306/blog_db
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

Docker Compose automatically passes these properties using environment variables.

---

## API Architecture
### Diagram
```
  +-------------------+           +----------------------+         +----------------+
  |   Client (UI)     |  --->     | Spring Boot API Layer|  --->   |  MySQL Database|
  |  (Postman/Browser)|           |  (Controllers,       |         |  (Persistent   |
  |                   |           |   Services, Repos)   |         |   Storage)     |
  +-------------------+           +----------------------+         +----------------+
```
**Description**:
1. Client (Postman/Browser) sends HTTP requests.
2. Requests are handled by the API (Controller -> Service -> Repository).
3. MySQL database processes queries and sends responses back.

---

## API Examples
### Create Blog (POST)
```json
{
  "title": "Understanding Spring Boot",
  "content": "Spring Boot makes it easy to create production-ready applications."
}
```

### Update Blog (PUT)
```json
{
  "title": "Updated Blog Title",
  "content": "Updated blog content."
}
```

---

## Database Persistence
The database is stored in a Docker volume `mysql-data` to ensure data persistence across container restarts.

---

Happy coding!

