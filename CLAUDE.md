# CLAUDE.md - AI Assistant Guide for auto-trader

This document provides essential context for AI assistants working on the auto-trader codebase.

## Project Overview

**auto-trader** is an automated trading system project. The repository is currently in its initial setup phase.

- **License**: MIT License
- **Primary Language**: Java (based on .gitignore configuration)
- **Author**: kyongmin.noh

## Repository Structure

```
auto-trader/
├── .gitignore          # Java-specific ignore patterns
├── LICENSE             # MIT License
├── README.md           # Project documentation
└── CLAUDE.md           # This file - AI assistant guide
```

### Planned Directory Structure (To Be Implemented)

When developing this project, follow standard Java/Maven or Gradle project conventions:

```
auto-trader/
├── src/
│   ├── main/
│   │   ├── java/           # Main application source code
│   │   └── resources/      # Configuration files, properties
│   └── test/
│       ├── java/           # Unit and integration tests
│       └── resources/      # Test resources
├── pom.xml or build.gradle # Build configuration
├── config/                  # External configuration (gitignored)
└── docs/                    # Additional documentation
```

## Development Guidelines

### Build System

- **Recommended**: Maven or Gradle for dependency management
- Run tests before committing: `mvn test` or `./gradlew test`
- Build artifacts: `mvn package` or `./gradlew build`

### Code Style Conventions

- Follow standard Java naming conventions (camelCase for methods/variables, PascalCase for classes)
- Use meaningful variable and method names
- Keep methods focused and single-purpose
- Add Javadoc comments for public APIs

### Security Considerations (Critical for Trading Systems)

1. **Credentials Management**
   - NEVER commit API keys, secrets, or credentials to the repository
   - Use environment variables or external configuration files (add to .gitignore)
   - Consider using a secrets manager for production

2. **Input Validation**
   - Validate all external inputs (API responses, user inputs)
   - Sanitize data before processing

3. **Error Handling**
   - Implement robust error handling for network failures
   - Log errors appropriately without exposing sensitive data
   - Implement circuit breakers for external API calls

4. **Financial Calculations**
   - Use `BigDecimal` for all monetary calculations (never `float` or `double`)
   - Be explicit about rounding modes
   - Validate calculation results

### Testing Requirements

- Write unit tests for all trading logic
- Mock external API calls in tests
- Test edge cases: zero values, negative numbers, API failures
- Consider paper trading/simulation modes for integration testing

## Common Commands

```bash
# Build the project (once build system is configured)
mvn clean install
# or
./gradlew clean build

# Run tests
mvn test
# or
./gradlew test

# Run the application (adjust main class as needed)
mvn exec:java -Dexec.mainClass="com.example.AutoTrader"
# or
./gradlew run
```

## Git Workflow

- Create feature branches from main: `git checkout -b feature/your-feature`
- Write clear, descriptive commit messages
- Keep commits atomic and focused
- Push to feature branches: `git push -u origin feature/your-feature`

## Key Files to Watch

| File/Directory | Purpose |
|----------------|---------|
| `src/main/java/` | Main application code |
| `src/test/java/` | Test files |
| `pom.xml` / `build.gradle` | Build configuration and dependencies |
| `application.properties` | Application configuration |
| `.env` (gitignored) | Environment-specific secrets |

## AI Assistant Instructions

When working on this codebase:

1. **Read First**: Always read existing code before making modifications
2. **Security Focus**: Pay extra attention to security given the financial nature of this application
3. **Test Coverage**: Ensure new features have corresponding tests
4. **Minimize Changes**: Make focused, minimal changes that address the specific request
5. **No Hardcoded Secrets**: Never hardcode API keys, tokens, or credentials
6. **BigDecimal for Money**: Always use `BigDecimal` for financial calculations
7. **Logging**: Add appropriate logging but never log sensitive data
8. **Error Handling**: Implement proper error handling for all external calls

## Dependencies (Recommended)

When setting up the project, consider these libraries:

- **HTTP Client**: OkHttp, Apache HttpClient, or Java 11+ HttpClient
- **JSON Processing**: Jackson or Gson
- **Testing**: JUnit 5, Mockito
- **Logging**: SLF4J with Logback
- **Configuration**: Spring Boot Config or Apache Commons Configuration

## Notes

- This is a new repository in its initial setup phase
- The .gitignore is configured for Java development
- Future updates to this file should reflect actual project structure as it evolves
