# Airline Ticketing System API


![EntityRelationDiagram](https://github.com/user-attachments/assets/85a6c3f9-9231-4ee8-af5f-588188b67064)

https://drive.google.com/file/d/1CUrU1w0DSTOEvM_rDAr18bV7aX_7wi80/view?usp=sharing

[[http://airplane-web-api-bkefgjaabkcwa2df.italynorth-01.azurewebsites.net/swagger/index.html](https://kingserkan35.onrender.com/swagger-ui.html
)](https://kingserkan35.onrender.com/swagger-ui/index.html)

The video could not be loaded because the video size is too large.



This is a simple airline ticketing system API.

## Setup

1. Download the project to your computer
2. Set up MySQL database
3. Run the following command:

```
./mvnw spring-boot:run
```

## Using Swagger UI

After starting the application, access Swagger UI in your browser at:

```
http://localhost:8080/swagger-ui.html
```

## API Features

- User login
- Adding and querying flights
- Purchasing tickets
- Check-in
- Viewing passenger lists

## Postman Collection

You can import the Postman collection file (`Airline_Ticketing_API.postman_collection.json`) to test API endpoints.

## Test Users

- Admin: username: admin, password: admin123
- User: username: user, password: user123

## Example Requests

### Login
```json
{
  "username": "admin",
  "password": "admin123"
}
```

### Add Flight
```json
{
  "flightNumber": "TK101",
  "airportFrom": "IST",
  "airportTo": "JFK",
  "dateFrom": "2025-05-15T10:00:00",
  "dateTo": "2025-05-15T22:00:00",
  "duration": 720,
  "capacity": 200
}
```

### Buy Ticket
```json
{
  "flightNumber": "TK101",
  "date": "2025-05-15T10:00:00",
  "passengerNames": ["John Doe", "Jane Doe"]
}
```

## Deployment

### Local Deployment
1. Build the JAR file:
   ```
   ./mvnw clean package
   ```
2. Run the JAR file:
   ```
   java -jar target/airline-ticketing-0.0.1-SNAPSHOT.jar
   ```

### Docker Deployment
1. Build Docker image:
   ```
   docker build -t airline-ticketing-api .
   ```
2. Run Docker container:
   ```
   docker run -p 8080:8080 airline-ticketing-api
   ```

### Cloud Deployment (AWS)
1. Create an EC2 instance
2. Install Java and MySQL
3. Upload the JAR file
4. Configure the application.properties with your database settings
5. Run the application using:
   ```
   java -jar airline-ticketing-0.0.1-SNAPSHOT.jar
   ```

   I used spring boot for the first time and since it was my first time writing an API I encountered a lot of errors, mistakes and confusion.

Even though it is not a perfect project I think I have created a good project.

🔧Technologies Used Java 17

Spring Boot

Spring Data JPA (Hibernate)

Spring Security (JWT)

MySQL

Maven

📚Features Add, list, and search flights

Purchase tickets

Perform check-in

List passengers

Secure login with JWT

🔐Default Admin User ( It is not working) Username: Admin

Password: 1234

🚀Run the Project Update your MySQL info in application.properties.

Create the database (tables will be auto-generated).

Run the project from an IDE

📁API Endpoints

Method Endpoint Description POST /auth/login Login using JWT

GET /flights List all flights

POST /flights Create a new flight

POST /tickets Buy a ticket

POST /checkin Perform a check-in

GET /passanger List of passengers of seats

⚠️ Challenges Faced

1-)Database Connection Issues Incorrect URL, username, or password in application.properties.
MySQL not running or running on another port.

2-)JPA Mapping Issues Wrong @OneToMany or @ManyToOne mappings can cause recursion.
Infinite loops and StackOverflowError if DTO is not used.

Incorrect boolean mapping (int vs tinyint(1) in MySQL).

3-)Spring Security & JWT Problems JWT not generated or not passed correctly in headers.
Getting 403 Forbidden or 401 Unauthorized errors.

BadCredentialsException due to plain text password.

NoSuchBeanDefinitionException due to missing config classes.

4-)Missing Validation No @Valid, @NotNull, or @Size annotations leads to silent failures.
API may accept invalid or null data without proper feedback.

5-)Unique Constraints in DB Adding duplicate entries (e.g., flight number) causes exceptions.
Use @Column(unique = true) for usernames, emails, etc.

6-)Check-in Logic Errors Allowing multiple check-ins for the same ticket.
Not validating ticket ownership or status before check-in.

7-)DTO vs Entity Confusion Without DTO, JSON responses may be deeply nested or infinite.
Missing @JsonIgnore, @JsonManagedReference can break JSON serialization.

8-)Data Update Problems save() might not trigger immediate DB update, use saveAndFlush() when needed.
Missing @Transactional can prevent data from persisting.

Missing Swagger/OpenAPI Harder to test endpoints.
Swagger helps visualize and test REST APIs easily.

API Endpoints

Method Endpoint Description POST /auth/login Login using JWT GET /flights List all flights POST /flights Create a new flight POST /tickets Buy a ticket POST /checkin Perform a check-in
