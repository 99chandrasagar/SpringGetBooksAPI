# GetBooks API

This project demonstrates how to build a simple REST API using Spring Boot that serves a list of books without using a database. The data is hardcoded into the application for simplicity.

## Features
- RESTful API endpoint to retrieve a list of books.
- Data served directly from an in-memory list.
- Lightweight and easy-to-understand implementation.

## Prerequisites
Before running the application, ensure you have the following installed:

- Java 8 or later
- Maven or Gradle
- An IDE such as IntelliJ IDEA, Eclipse, or VS Code (optional but recommended)

## Steps to Create the API

### 1. Project Setup
1. Create a new Spring Boot project.
   - You can use [Spring Initializr](https://start.spring.io/).
   - Add the following dependencies:
     - Spring Web

2. Import the project into your IDE.

### 2. Create the `Book` Model
Create a class `Book` in the `model` package:

```java
package com.example.getbooks.model;

public class Book {
    private int id;
    private String name;
    private String imageUrl;

    // Constructors
    public Book(int id, String name, String imageUrl) {
        this.id = id;
        this.name = name;
        this.imageUrl = imageUrl;
    }

    // Getters and Setters
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getImageUrl() {
        return imageUrl;
    }

    public void setImageUrl(String imageUrl) {
        this.imageUrl = imageUrl;
    }
}
```

### 3. Create the `BookController`
Create a REST controller to expose the API endpoint:

```java
package com.example.getbooks.controller;

import com.example.getbooks.model.Book;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.Arrays;
import java.util.List;

@RestController
@RequestMapping("/api/v1")
public class BookController {

    @GetMapping("/books")
    public List<Book> getBooks() {
        return Arrays.asList(
            new Book(1, "harry potter", "harry_potter.jpg"),
            new Book(2, "Rise", "rise.jpeg")
        );
    }
}
```

### 4. Run the Application
1. Run the `main` method in the `GetBooksApplication` class (created by Spring Boot).
2. The application will start on the default port (8080).

### 5. Test the API
- Use Postman, curl, or your browser to test the API.
- Send a GET request to: `http://localhost:8080/api/v1/books`

You should receive the following JSON response:

```json
[
  {
    "id": 1,
    "name": "harry potter",
    "imageUrl": "harry_potter.jpg"
  },
  {
    "id": 2,
    "name": "Rise",
    "imageUrl": "rise.jpeg"
  }
]
```


## Dependencies
This project uses the following dependencies:
- Spring Boot Starter Web


