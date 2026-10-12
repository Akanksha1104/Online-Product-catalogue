# Online Product Catalogue

A web application for browsing, searching and managing products, built with **Spring Boot**, **Thymeleaf** and **MySQL**.

## Features
- **Product list** with ID, name, quantity, category, price and description
- **Search** by product name or category (case-insensitive)
- **Add, edit and delete** products (full CRUD)
- Category dropdown, price validation and a responsive layout for mobile screens

## Tech stack
| Layer     | Technology |
|-----------|------------|
| Backend   | Java 21, Spring Boot 3.5, Spring MVC |
| Data      | Spring Data JPA (Hibernate), MySQL |
| Frontend  | Thymeleaf templates, HTML, CSS |
| Build     | Maven (wrapper included) |

## Project structure
```
src/main/java/com/one/project/
├── ProjectApplication.java          Spring Boot entry point
├── controller/MyController.java     Web routes (list, search, add, edit, delete)
├── entities/Product.java            JPA entity mapped to the "products" table
├── repository/ProductRepository.java  Database access + search query
└── services/                        Business logic (ProductService / ProductServiceImpl)

src/main/resources/
├── application.properties           Database and server settings
└── templates/                       product-list.html, product-form.html
```

## Running locally

**Requirements:** Java 21 and MySQL.

1. Create the database in MySQL:
   ```sql
   CREATE DATABASE OnlineProduct;
   ```
   The `products` table is created automatically on first run.

2. Set your MySQL password as an environment variable, so it isn't stored in the code.

   Windows (Command Prompt):
   ```
   set DB_PASSWORD=your_mysql_password
   ```
   Git Bash / macOS / Linux:
   ```bash
   export DB_PASSWORD=your_mysql_password
   ```
   The username defaults to `root`. Set `DB_USERNAME` to use a different one.

3. Start the app from the same terminal:
   ```bash
   ./mvnw spring-boot:run
   ```
   (On Windows Command Prompt use `mvnw spring-boot:run`.)

4. Open **http://localhost:8081**

## Pages and routes
| URL                       | Description |
|---------------------------|-------------|
| `/`                       | Product list (add `?keyword=...` to search) |
| `/products/new`           | Add a new product |
| `/products/edit/{id}`     | Edit a product |
| `/products/delete/{id}`   | Delete a product |
| `/products/save` (POST)   | Saves the add/edit form |
