# Binary Calculator Webapp

A Spring Boot web application and REST API for performing binary arithmetic and bitwise operations, built for SOFE 3980U (Software Testing and Quality Assurance) - Lab 2.

This project extends the `Binary` class from [Lab 1](https://github.com/Atharva1972/Binary-Calculator-Lab-1) into a full web application, exposing the same logic through both a browser-based calculator UI and a REST API.

## Features

- **Web calculator UI** (`/`) - an interactive binary calculator supporting Add (`+`), Multiply (`*`), AND (`&`), and OR (`|`).
- **REST API** - each operation is available as both a plain-text endpoint and a JSON endpoint:
  | Operation | Plain text | JSON |
  |---|---|---|
  | Add | `GET /add?operand1=111&operand2=1010` | `GET /add_json?operand1=111&operand2=1010` |
  | Multiply | `GET /multiply?operand1=111&operand2=1010` | `GET /multiply_json?operand1=111&operand2=1010` |
  | AND | `GET /and?operand1=111&operand2=1010` | `GET /and_json?operand1=111&operand2=1010` |
  | OR | `GET /or?operand1=111&operand2=1010` | `GET /or_json?operand1=111&operand2=1010` |
- **Demo endpoints** (from the earlier part of the lab):
  - `GET /hello?name=YourName` - Thymeleaf-rendered greeting.
  - `GET /helloAPI?name=YourName` - plain-text REST greeting.
  - `GET /emailAPI?fname=John&lname=Doe` - JSON suggested-email generator.

## Tech stack

- Java 17
- Spring Boot 2.1.2 (Spring MVC, Thymeleaf, Spring Boot Test)
- Apache Maven
- JUnit 4 + MockMvc for testing

## Running locally

```bash
mvn clean install
mvn spring-boot:run
```

Then open [http://localhost:8080](http://localhost:8080) for the calculator UI, or hit any of the API endpoints above directly.

## Running tests

```bash
mvn test
```

The project includes 31 unit tests across four test classes (`HelloControllerTest`, `HelloAPIControllerTest`, `BinaryControllerTest`, `BinaryAPIControllerTest`), using Spring's `@WebMvcTest` and `MockMvc` to test each controller in isolation. Each of the three newly implemented operators (Multiply, AND, OR) is tested against three scenarios: operands of unequal length, operands of equal length, and a zero-operand edge case.

## Project structure

```
src/main/java/com/ontariotechu/sofe3980U/
    Application.java          # Spring Boot entry point
    Binary.java                # Binary number representation + Add/OR/AND/Multiply logic
    BinaryController.java      # Web UI controller ("/")
    BinaryAPIController.java   # REST API controller
    BinaryAPIResult.java       # JSON response shape for the calculator API
    HelloController.java       # Demo view controller ("/hello")
    HelloAPIController.java    # Demo REST controller ("/helloAPI", "/emailAPI")
    APIResult.java             # JSON response shape for the email API

src/main/resources/templates/
    calculator.html            # Calculator UI
    result.html                 # Result view
    error.html                  # Invalid-operator error view
    hello.html                  # Demo greeting view

src/test/java/com/ontariotechu/sofe3980U/
    BinaryControllerTest.java
    BinaryAPIControllerTest.java
    HelloControllerTest.java
    HelloAPIControllerTest.java
```

## Author

Atharva Rajadhyaksha - Student ID 101041016
Course: [Software Testing and Quality Assurance](https://learn.ontariotechu.ca/courses/39683)