# When to use?

Streamlit适合作为**MVP阶段**的技术选型，用于快速构建系统原型。

# Project structure

以下代码结构基于第一性原理和奥卡姆剃刀原则出发进行设计，作为**MVP阶段**的建议架构，同时考虑了系统的扩展性和未来演进方向（前后端分离、容器化部署）。

```text
project-root/
├── ui/                             # 前端（第一阶段是 Streamlit）
│   ├── app.py
│   ├── components/
│   ├── pages/
│   └── state.py

├── backend/
│   ├── api/                        # 接口层（FastAPI 等）
│   │   ├── routes/
│   │   └── deps.py
│   ├── agents/                     # 各类智能体（业务领域核心）
│   │   ├── base.py
│   │   ├── writer_agent.py
│   │   └── __init__.py
│   ├── prompts/                    # Prompt 模板，按 agent 分类
│   ├── services/                   # 应用服务层（编排 + 权限 + 状态）
│   │   ├── chat_service.py
│   │   ├── agent_orchestrator.py
│   │   └── file_service.py
│   ├── tools/                      # Agent 可用工具（函数调用封装）
│   │   ├── search_tool.py
│   │   ├── calculator.py
│   │   └── __init__.py
│   ├── infrastructure/            # 基础设施适配层
│   │   ├── db/
│   │   │   ├── models/
│   │   │   ├── crud/
│   │   │   └── session.py
│   │   ├── queue/
│   │   │   ├── producer.py
│   │   │   ├── consumer.py
│   │   │   └── config.py
│   │   └── llm_provider/           # 多模型适配（如 OpenAI, Claude, Llama）
│   │       ├── openai.py
│   │       ├── anthropic.py
│   │       └── llama_cpp.py
│   ├── scheduler/ (可选)           # 定时任务（Celery, APScheduler 等）
│   │   ├── tasks.py
│   │   └── celery_worker.py
│   ├── file_processors/ (可选)     # 文档解析模块（PDF, Word, Excel）
│   │   ├── pdf_reader.py
│   │   ├── docx_parser.py
│   │   └── excel_parser.py
│   ├── shared/                     # 工具、配置、异常、日志等
│   │   ├── config.py
│   │   ├── constants.py
│   │   ├── logger.py
│   │   ├── exceptions.py
│   │   └── helpers.py
│   └── tests/                      # 测试模块
│       ├── test_agents/
│       ├── test_services/
│       ├── test_api/
│       └── conftest.py
├── scripts/                        # 运维脚本、DB迁移、模型微调脚本等
├── data/                           # 初始样本、知识库、上传文件等
├── requirements.txt
├── .env
└── README.md
```