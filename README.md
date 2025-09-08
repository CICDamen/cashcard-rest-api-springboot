# Cash Card REST API

A Spring Boot REST API for managing Family Cash Cards. This application provides endpoints for retrieving cash card information.

## Overview

The Cash Card service allows family members to manage digital cash cards. Currently, the application supports retrieving cash card details by ID.

## Technologies Used

- **Java 17** - Programming language
- **Spring Boot 3.5.5** - Web framework and application framework
- **Spring Web** - REST API framework
- **Gradle 8.14.3** - Build tool and dependency management
- **JUnit 5** - Testing framework
- **AssertJ** - Assertion library for tests
- **JSONPath** - JSON processing for tests

## Prerequisites

- Java 17 or higher
- No need to install Gradle (project includes Gradle Wrapper)

## Getting Started

### Building the Project

```bash
# On Unix/Linux/macOS
./gradlew build

# On Windows
gradlew.bat build
```

### Running the Application

```bash
# On Unix/Linux/macOS
./gradlew bootRun

# On Windows
gradlew.bat bootRun
```

The application will start on `http://localhost:8080`.

### Running Tests

```bash
# Run all tests
./gradlew test

# Run tests with detailed output
./gradlew test --info
```

## API Endpoints

### Get Cash Card by ID

- **URL**: `/cashcards/{id}`
- **Method**: `GET`
- **Path Parameter**: `id` - The cash card ID
- **Success Response**: 
  - **Code**: 200 OK
  - **Content**: 
    ```json
    {
      "id": 99,
      "amount": 123.45
    }
    ```
- **Error Response**:
  - **Code**: 404 NOT FOUND
  - **Content**: Empty

### Example Usage

```bash
# Get cash card with ID 99
curl http://localhost:8080/cashcards/99

# Response:
# {"id":99,"amount":123.45}

# Get non-existent cash card
curl http://localhost:8080/cashcards/1000

# Response: 404 Not Found
```

## Project Structure

```
src/
├── main/
│   ├── java/
│   │   └── example/
│   │       └── cashcard/
│   │           ├── CashcardApplication.java    # Main Spring Boot application
│   │           ├── CashCard.java               # Cash card data model
│   │           └── CashCardController.java     # REST controller
│   └── resources/
└── test/
    ├── java/
    │   └── example/
    │       └── cashcard/
    │           ├── CashcardApplicationTests.java  # Integration tests
    │           └── CashCardJsonTest.java          # JSON serialization tests
    └── resources/
```

## Development

### Data Model

The `CashCard` is a simple record class with two fields:
- `id` (long) - Unique identifier for the cash card
- `amount` (double) - Current balance on the cash card

### Current Implementation

Currently, the application has a hardcoded cash card with ID 99 and amount 123.45. This is a basic implementation suitable for learning and demonstration purposes.

### Testing

The project includes comprehensive tests:

1. **Integration Tests** (`CashcardApplicationTests.java`):
   - Tests the full HTTP request/response cycle
   - Verifies correct JSON responses
   - Tests both success (200) and not found (404) scenarios

2. **JSON Tests** (`CashCardJsonTest.java`):
   - Tests JSON serialization and deserialization
   - Ensures proper JSON structure and field mapping

## Gradle Wrapper

This project includes the Gradle Wrapper (`gradle-wrapper.jar`) which is a best practice for Java projects because it:

- Ensures consistent Gradle versions across different development environments
- Allows building the project without requiring Gradle to be installed locally
- Provides reproducible builds
- Simplifies CI/CD pipeline setup

The wrapper JAR is intentionally included in version control (see `.gitignore` line: `!gradle/wrapper/gradle-wrapper.jar`).

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Ensure all tests pass: `./gradlew test`
6. Submit a pull request

## Future Enhancements

Potential improvements for this project could include:

- Database integration for persistent storage
- CRUD operations (Create, Update, Delete)
- User authentication and authorization
- Multiple cash card support per user
- Transaction history
- Balance management operations

## License

This project is for educational and demonstration purposes.