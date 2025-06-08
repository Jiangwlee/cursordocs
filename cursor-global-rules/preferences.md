# Cursor Development Preferences

## 1. Development Environment
- Operating System: Windows 11
- Editor: Cursor
- Terminal: PowerShell

## 2. Code Style Preferences
- Indentation: 4 spaces
- Line Endings: LF (Unix style)
- File Encoding: UTF-8
- Maximum Line Length: 120 characters

## 3. Language Preferences
### Backend Development: Python
- Package Manager: uv
- Best Practices:
  - Use type annotations
  - Follow PEP 8 guidelines
  - Use virtual environments
  - Prioritize asynchronous programming
  - Use dataclass or Pydantic models

### Frontend Development: TypeScript/JavaScript
- Framework Preferences: React, Next.js
- Package Manager: pnpm
- Code Formatter: Prettier
- Linting Tool: ESLint
- Best Practices:
  - Use functional components and Hooks
  - Enable TypeScript strict mode
  - Follow atomic design principles
  - Prioritize React Query for state management

### API Development: FastAPI
- Best Practices:
  - Use Pydantic model validation
  - Implement OpenAPI documentation
  - Apply dependency injection
  - Implement middleware and exception handling
  - Use asynchronous database operations

## 4. Documentation Preferences
- Format: Markdown
- Comment Language: Chinese
- Structure: Clear hierarchical organization
- Code Examples: Include complete runnable examples
- Documentation Standards:
  - Use Markdown extended syntax
  - Include table of contents
  - Add code highlighting
  - Use tables for configuration items

## 5. Version Control
- Version Control System: Git
- Commit Message Format: Follow Conventional Commits
- Security: Use .gitignore for sensitive data files
- Branch Strategy:
  - main: Production branch
  - develop: Development branch
  - feature/*: Feature branches
  - hotfix/*: Emergency fix branches

## 7. Testing Standards
- Unit Testing: pytest (Python), Jest (TypeScript)
- Test Coverage Requirement: > 80%
- Test Naming Convention: test_<feature>_<scenario>
- Test Data: Use fixtures and factories

## 8. Security Preferences
- Sensitive Information: Use environment variables
- API Keys: Use key management services
- Security Best Practices:
  - Use HTTPS
  - Implement CORS policies
  - Add rate limiting
  - Implement authentication and authorization
  - Regular dependency updates

## 9. Performance Optimization
- Code splitting
- Lazy loading
- Caching strategies
- Database indexing
- Asynchronous processing
- Resource compression

## 10. Deployment Standards
- Containerization: Docker
- CI/CD: GitHub Actions
- Environment Configuration:
  - Development environment
  - Testing environment
  - Staging environment
  - Production environment
- Monitoring and Alerting:
  - Performance monitoring
  - Error tracking
  - Log collection

## 11. Memory Management Preferences
- Default to mem0 mcp server as the long-term memory backend for Cursor.
- Always prioritize retrieving long-term memory from mem0.
- If mem0 is unavailable, use local cache temporarily and sync once restored.
- Ensure data security and access control when interacting with mem0.