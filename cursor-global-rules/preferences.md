# Cursor Development Preferences

## 1. Development Environment
- OS: Windows 11
- Editor: Cursor
- Terminal: PowerShell

## 2. Code Style
- Indentation: 4 spaces
- Line Endings: LF (Unix)
- Encoding: UTF-8
- Max Line Length: 120 characters

## 3. Language Preferences

### Python (Backend)
- Package Manager: uv
- Best Practices:
    - Use type annotations
    - Follow PEP 8
    - Use virtual environments
    - Prefer asynchronous programming
    - Use dataclass or Pydantic models

### TypeScript/JavaScript (Frontend)
- Frameworks: React, Next.js
- Package Manager: pnpm
- Formatter: Prettier
- Linter: ESLint
- Best Practices:
    - Use functional components and Hooks
    - Enable TypeScript strict mode
    - Follow atomic design
    - Prefer React Query for state management

### FastAPI (API)
- Best Practices:
    - Use Pydantic for validation
    - Provide OpenAPI docs
    - Apply dependency injection
    - Implement middleware and exception handling
    - Use async DB operations

## 4. Documentation
- Format: Markdown
- Comments: Chinese
- Structure: Hierarchical
- Code Examples: Complete and runnable
- Standards:
    - Use extended Markdown
    - Include table of contents
    - Syntax highlighting
    - Use tables for configs

## 5. Version Control
- System: Git
- Commit Format: Conventional Commits
- Security: .gitignore for sensitive files
- Branching:
    - main: Production
    - develop: Development
    - feature/*: Features
    - hotfix/*: Hotfixes

## 6. Testing
- Python: pytest
- TypeScript: Jest
- Coverage: > 80%
- Naming: test_<feature>_<scenario>
- Data: Use fixtures/factories

## 7. Security
- Use environment variables for secrets
- Use key management for API keys
- Best Practices:
    - Enforce HTTPS
    - CORS policies
    - Rate limiting
    - AuthN & AuthZ
    - Regular dependency updates

## 8. Performance
- Code splitting
- Lazy loading
- Caching
- DB indexing
- Async processing
- Resource compression

## 9. Deployment
- Container: Docker
- CI/CD: GitHub Actions
- Environments: dev, test, staging, prod
- Monitoring:
    - Performance
    - Error tracking
    - Log collection

## 10. Memory Management
- Use mem0 mcp server for long-term memory
- Fallback to local cache if unavailable, sync when restored
- Ensure data security and access control

## 11. Library & Component Usage
- Always review documentation in the following priority before using any library or component:
    1. Cursor Docs
    2. Context7 mcp server
    3. Online official documentation
- Ensure all code references and implementations are up-to-date and follow current best practices.
- Avoid using deprecated or outdated APIs.
- Document any custom implementations or deviations for future reference.