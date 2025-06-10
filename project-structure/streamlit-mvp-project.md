# When to use?

Streamlit is suitable as a technical choice for the **MVP phase**, used for rapid system prototyping.

# Project structure

This structure is based on industry best practices, taking into account frontend-backend decoupling, scalability, automated testing, CI/CD, and containerized deployment. It is suitable for the MVP phase and future evolution.

**Important: System Directory Design and Optimization Principles**
1. Separate frontend and backend to facilitate future frontend architecture replacement (e.g., React/Vue)
2. Separate configuration from code to support multi-environment switching
3. Decouple business logic from infrastructure to improve maintainability
4. Preset directories for testing, CI/CD, documentation, and containerization to support team collaboration and automation
5. Follow First Principles and Occam's Razor for a simple and extensible structure

**Recommended Project Structure Example**

```text
project-root/
├── frontend/                      # Frontend (Streamlit in the first phase, can be switched to React/Vue later)
│   ├── app.py
│   ├── components/
│   ├── pages/
│   └── state.py
│
├── backend/                       # Backend
│   ├── api/                       # API layer (FastAPI, etc.)
│   │   ├── routes/
│   │   └── deps.py
│   ├── agents/                    # Various agents (core business logic)
│   │   ├── base.py
│   │   ├── writer_agent.py
│   │   └── __init__.py
│   ├── prompts/                   # Prompt templates, categorized by agent
│   ├── services/                  # Application service layer (orchestration + permissions + state)
│   │   ├── chat_service.py
│   │   ├── agent_orchestrator.py
│   │   └── file_service.py
│   ├── tools/                     # Tools available to agents (function call wrappers)
│   │   ├── search_tool.py
│   │   ├── calculator.py
│   │   └── __init__.py
│   ├── infrastructure/            # Infrastructure adaptation layer
│   │   ├── db/
│   │   │   ├── models/
│   │   │   ├── crud/
│   │   │   └── session.py
│   │   ├── queue/
│   │   │   ├── producer.py
│   │   │   ├── consumer.py
│   │   │   └── config.py
│   │   └── llm_provider/          # Multi-model adaptation (e.g., OpenAI, Claude, Llama)
│   │       ├── openai.py
│   │       ├── anthropic.py
│   │       └── llama_cpp.py
│   ├── common/                    # Common modules (config, constants, logger, exceptions, helpers, etc.)
│   │   ├── config.py
│   │   ├── constants.py
│   │   ├── logger.py
│   │   ├── exceptions.py
│   │   └── helpers.py
│   └── tests/                     # Test modules
│       ├── test_agents/
│       ├── test_services/
│       ├── test_api/
│       └── conftest.py
│
├── scripts/                       # Ops scripts, DB migration, model fine-tuning scripts, etc.
├── data/                          # Initial samples, knowledge base, uploaded files, etc.
│   ├── raw/
│   ├── processed/
│   └── external/
├── config/                        # Configuration files (split by environment/function)
│   ├── config_dev.py
│   ├── config_prod.py
│   └── ...
├── docs/                          # Design docs, API docs, architecture diagrams, etc.
├── .github/
│   └── workflows/                 # CI/CD pipeline configuration (e.g., GitHub Actions)
├── Dockerfile                     # Containerized deployment
├── docker-compose.yml             # Multi-service orchestration
├── requirements.txt               # Python dependencies
├── .env                           # Environment variables
└── README.md                      # Project documentation
```

---

## Directory Optimization Notes

- frontend/: Frontend directory, initially Streamlit, can be smoothly migrated to React/Vue and other frameworks later.
- backend/: Main backend directory, clear layering for easy extension and maintenance.
- common/: Common modules, including config, constants, logger, exceptions, helpers, etc.
- config/: Configuration directory, supports splitting by environment and function.
- docs/: Documentation directory, facilitates team collaboration and knowledge accumulation.
- .github/workflows/: CI/CD configuration, recommended to preset automated testing, build, and deployment workflows.
- Dockerfile & docker-compose.yml: Support one-click deployment locally and in the cloud.
- data/: Data directory, divided into raw, processed, and external data for better data governance.
- scripts/: Script directory, subdivided into migration/, maintenance/, finetune/, etc.

---

## Technology Stack Recommendations

Below are some recommended technology stacks for each layer of the project. Choose according to your team expertise, project requirements, and scalability needs.

**Frontend**
- Streamlit (MVP): Ideal for rapid prototyping and quick iteration.
- React, Next.js, Vue, Vite: Suitable for production environments and building complex, interactive UIs.

**Backend**
- FastAPI: Recommended for asynchronous, modern Python APIs; excellent performance and OpenAPI support.
- Django: Suitable for full-stack web applications with built-in admin and ORM.
- Flask: Lightweight microservices or simple backend APIs.

**API Framework**
- FastAPI (Python): Best for Python-based projects needing async and OpenAPI.
- Express.js (Node.js): Popular for JavaScript/TypeScript backends.
- Spring Boot (Java): Enterprise-level, robust Java backend services.

**Documentation**
- MkDocs, Sphinx, Docusaurus: For project and developer documentation.
- Swagger/OpenAPI: For auto-generating and visualizing API documentation.

**Database**
- PostgreSQL: Recommended for most use cases, strong features and reliability.
- MySQL: Widely used, good for traditional web applications.
- SQLite: Lightweight, best for local development or small-scale MVPs.
- MongoDB: NoSQL, suitable for flexible schema or document-based storage.

**ORM/ODM**
- SQLAlchemy, Tortoise ORM, Django ORM: For Python projects, enabling database abstraction and migrations.
- Prisma (Node.js): Type-safe ORM for JavaScript/TypeScript.
- Mongoose (MongoDB): ODM for MongoDB in Node.js.

**CI/CD**
- GitHub Actions: Easy integration with GitHub repositories, supports automated testing, build, and deployment.
- GitLab CI, Jenkins: Alternatives for more complex or self-hosted pipelines.

**Containerization**
- Docker: For packaging applications and dependencies.
- Docker Compose: For orchestrating multi-service local development.
- Kubernetes: For large-scale, production-grade container orchestration.

**Testing**
- pytest (Python): Recommended for Python unit and integration testing.
- Jest (JS/TS): For JavaScript/TypeScript testing.
- unittest: Built-in Python testing framework.
- Playwright, Cypress: For end-to-end (E2E) testing of web applications.

**Note:**
- For MVP, prioritize rapid development and iteration. Streamlit + FastAPI + SQLite/PostgreSQL is a common, efficient stack.
- For production, consider scalability, maintainability, and team familiarity with the stack.
- Always document your technology choices and rationale in the docs/ directory.