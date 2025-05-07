# Student-Course Management System

A Spring Boot–powered web application for managing students and courses in a many-to-many relationship. Users can perform CRUD operations on both entities, and enroll students in courses. Built with Spring MVC, Spring Data JPA, JSP views, and MySQL.

## Table of Contents

- [Project Overview](#project-overview)  
- [Folder Structure](#folder-structure)  
- [Entity Relationship](#entity-relationship)  
- [Features](#features)  
- [Technology Stack](#technology-stack)  
- [Prerequisites](#prerequisites)  
- [Getting Started](#getting-started)  
- [Running Tests](#running-tests)  
- [Sample Data Initialization](#sample-data-initialization)  
- [Custom JPQL Query](#custom-jpql-query)  
- [License](#license)  

## Project Overview

This application demonstrates how to:

- Model and persist a many-to-many relationship between `Student` and `Course` entities using Spring Data JPA.  
- Expose CRUD operations for both entities via Spring MVC controllers.  
- Render server-side views with JSP, JSTL, and Bootstrap for a responsive UI.  
- Seed the database with sample data at startup.

## Folder Structure

student-course-management/
├── pom.xml
├── src/
│ ├── main/
│ │ ├── java/com/example/studentcourse/
│ │ │ ├── config/
│ │ │ │ └── DataInitializer.java
│ │ │ ├── controller/
│ │ │ │ ├── HomeController.java
│ │ │ │ ├── StudentController.java
│ │ │ │ └── CourseController.java
│ │ │ ├── model/
│ │ │ │ ├── Student.java
│ │ │ │ └── Course.java
│ │ │ ├── repository/
│ │ │ │ ├── StudentRepository.java
│ │ │ │ └── CourseRepository.java
│ │ │ ├── service/
│ │ │ │ ├── StudentService.java
│ │ │ │ ├── StudentServiceImpl.java
│ │ │ │ ├── CourseService.java
│ │ │ │ └── CourseServiceImpl.java
│ │ │ └── StudentCourseApplication.java
│ │ ├── resources/
│ │ │ └── application.properties
│ │ └── webapp/WEB-INF/views/
│ │ ├── common/
│ │ │ ├── header.jsp
│ │ │ └── footer.jsp
│ │ ├── home.jsp
│ │ ├── listStudents.jsp
│ │ ├── addStudent.jsp
│ │ ├── updateStudent.jsp
│ │ ├── viewStudent.jsp
│ │ ├── listCourses.jsp
│ │ ├── addCourse.jsp
│ │ ├── updateCourse.jsp
│ │ └── viewCourse.jsp
│ └── test/
│ ├── java/com/example/studentcourse/
│ │ ├── repository/
│ │ │ ├── StudentRepositoryTest.java
│ │ │ └── CourseRepositoryTest.java
│ │ └── service/
│ │ ├── StudentServiceTest.java
│ │ └── CourseServiceTest.java
│ └── resources/
│ └── application-test.properties


## Entity Relationship

- A **Student** can enroll in multiple **Courses**.  
- A **Course** can have multiple **Students**.  
- This bidirectional many-to-many relationship is mapped via a join table.

## Features

1. **Student Management**  
   - Create, view, update, and delete student records  
   - Display enrolled courses per student  

2. **Course Management**  
   - Create, view, update, and delete course records  
   - Display enrolled students per course  

3. **Enrollment Operations**  
   - Register or deregister students in/from courses  
   - View all enrollments  

## Technology Stack

- **Language:** Java 11+  
- **Frameworks:** Spring Boot 2.7, Spring MVC, Spring Data JPA (Hibernate)  
- **View Layer:** JSP, JSTL, Bootstrap 5  
- **Database:** MySQL 8+  
- **Build:** Maven 3.6+  
- **Testing:** JUnit 5, Mockito  

## Prerequisites

- Java Development Kit (JDK) 11 or higher  
- Maven 3.6 or higher  
- MySQL Server 8.0 or higher  

## Getting Started

1. **Clone the repository**  
git clone https://github.com/yourusername/student-course-management.git
cd student-course-management
2. **Create the database**  
CREATE DATABASE student_course_db;
3. **Configure application properties**  
Open `src/main/resources/application.properties` and set your MySQL URL, username, and password.  
spring.datasource.url=jdbc:mysql://localhost:3306/student_course_db
spring.datasource.username=YOUR_DB_USERNAME
spring.datasource.password=YOUR_DB_PASSWORD
spring.jpa.hibernate.ddl-auto=update
spring.mvc.view.prefix=/WEB-INF/views/
spring.mvc.view.suffix=.jsp

4. **Build and run**  
mvn clean install
mvn spring-boot:run

5. **Access the application**  
Open your browser and go to:  
http://localhost:8080

## Running Tests

Execute all unit and integration tests with:

mvn test


## Sample Data Initialization

On application startup, the `DataInitializer` component seeds the database with:

- 10 sample students  
- 10 sample courses  
- Random enrollments linking students and courses  

This allows you to explore the UI without manual data entry.

## Custom JPQL Query

A demonstration of a custom JPQL query in `StudentRepository`:

@Query("SELECT s.name AS studentName, c.title AS courseTitle " +
"FROM Student s JOIN s.courses c")
List<Object[]> fetchStudentCourseData();

This fetches pairs of student names and their enrolled course titles via a JOIN.

## License

This project is licensed under the [MIT License](LICENSE).  
Feel free to use, modify, and distribute under the terms of that license.
