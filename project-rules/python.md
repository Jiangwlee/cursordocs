# Python Development Guidelines

## 1. Role Definition
- Python Development Expert
- FastAPI Development Expert
- Scalable API Development Expert

## 2. Core Principles
- Functional Programming First: Avoid unnecessary classes
- Type Safety: Utilize type annotations and Pydantic models
- Async-First: Use asynchronous operations for I/O
- Error Handling: Unified error responses with Pydantic validation
- Code Organization: Modular design, avoid duplication
- Naming Conventions: Descriptive names with auxiliary verbs

## 3. Technical Specifications
### 3.1 Error Handling
- Prioritize error and edge case handling
- Handle errors at the beginning of functions
- Use early returns to avoid deep nesting
- Place happy path at the end of functions
- Avoid unnecessary else statements
- Use guard clauses for preconditions and invalid states
- Implement proper error logging and user-friendly messages
- Use custom error types or error factories for consistent handling

```python
from fastapi import HTTPException
from pydantic import BaseModel
from typing import Optional

class ErrorResponse(BaseModel):
    code: int
    message: str
    details: Optional[dict] = None

async def handle_error(error: Exception) -> ErrorResponse:
    if isinstance(error, HTTPException):
        return ErrorResponse(
            code=error.status_code,
            message=error.detail
        )
    return ErrorResponse(
        code=500,
        message="Internal Server Error",
        details={"type": type(error).__name__}
    )
```

### 3.2 FastAPI Development
- Reference FastAPI documentation for Data Models, Path Operations, and Middleware best practices
- Use functional components (plain functions) and Pydantic models for input validation and response schemas
- Use declarative route definitions with explicit return type annotations
- Use `def` for synchronous operations and `async def` for asynchronous ones
- Minimize `@app.on_event("startup")` and `@app.on_event("shutdown")`; prefer lifespan context managers
- Use middleware for logging, error monitoring, and performance optimization
- Optimize I/O-bound tasks with async functions, caching strategies, and lazy loading
- Use HTTPException for expected errors and model them as specific HTTP responses
- Use middleware for handling unexpected errors, logging, and error monitoring
- Use Pydantic's BaseModel for consistent input/output validation and response schemas

Key Conventions:
1. Leverage FastAPI's dependency injection system for state and shared resource management
2. Prioritize API performance metrics (response time, latency, throughput)
3. Limit blocking operations in routes:
   - Favor asynchronous and non-blocking flows
   - Use dedicated async functions for database and external API operations
   - Structure routes and dependencies clearly for optimal readability and maintainability

### 3.3 Performance Optimization
- Minimize blocking I/O operations; use async operations for all database calls and external API requests
- Implement caching for static and frequently accessed data using Redis or in-memory stores
- Optimize data serialization and deserialization with Pydantic
- Use lazy loading techniques for large datasets and substantial API responses

## 4. Dependency Management
**MUST** read the LATEST library documents via context7 mcp server or cursor's @Docs.

### 4.1 Recommended Dependencies
- FastAPI >= 0.100.0
- Pydantic >= 2.0.0
- SQLAlchemy >= 2.0.0 (if using ORM features)
- asyncpg >= 0.27.0 or aiomysql (async database libraries)

### 4.2 Dependency Management Tools
- Use uv for dependency management
- Regular dependency version updates
- Manage dependencies via requirements.txt or pyproject.toml

## 5. Toolchain
### 5.1 Essential Tools
- Code Formatting: black
- Type Checking: mypy
- Testing: pytest

### 5.2 Base Configuration
```toml
# pyproject.toml
[tool.black]
line-length = 120
target-version = ['py312']

[tool.mypy]
python_version = "3.12"
strict = true
```

## 6. Iteration Plan
### Phase 1 (Current)
- Core principles
- Basic specifications
- Essential toolchain

### Phase 2
- Testing specifications
- Performance optimization
- Security guidelines

### Phase 3
- Deployment specifications
- Monitoring guidelines
- Documentation standards

## 7. Key Points
1. **Simplicity First**
   - Each specification has a clear purpose
   - Avoid over-engineering
   - Prioritize maintainability

2. **Progressive Enhancement**
   - Ensure basic specifications are implemented
   - Expand based on actual requirements
   - Regular review and optimization

3. **Practicality Priority**
   - Specifications serve actual development
   - Avoid formalism
   - Maintain flexibility

---
Last Updated: 2024-03-21
Version: 1.0.0