# BasicBot 🤖

*A sophisticated Research Assistant powered by GraphRAG technology for analyzing documents and research data.*

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=flat&logo=python)](https://python.org)
[![Node.js](https://img.shields.io/badge/Node.js-16+-339933?style=flat&logo=node.js)](https://nodejs.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688?style=flat&logo=fastapi)](https://fastapi.tiangolo.com)
[![Next.js](https://img.shields.io/badge/Next.js-14+-000000?style=flat&logo=next.js)](https://nextjs.org)
[![Neo4j](https://img.shields.io/badge/Neo4j-5+-008CC1?style=flat&logo=neo4j)](https://neo4j.com)
[![Ollama](https://img.shields.io/badge/Ollama-Supported-000000?style=flat&logo=ollama)](https://ollama.ai)

## 🌟 Overview

BasicBot is an advanced research assistant that leverages **Graph Retrieval-Augmented Generation (GraphRAG)** to provide intelligent analysis of documents, research papers, and technical content. Built with modern AI stack, it combines local LLM inference with graph-based knowledge representation for superior document understanding and question answering.

### Key Technologies
- **FastAPI Backend** - High-performance async API server
- **Next.js Frontend** - Modern React-based user interface
- **Neo4j Graph Database** - Advanced graph data storage and querying
- **Ollama Integration** - Local LLM inference with Granite models
- **Vector Embeddings** - Semantic search and similarity matching
- **RLHF Adaptation** - Continuous learning from user interactions

## ✨ Features

### 🔍 Intelligent Research Analysis
- **Multi-modal Retrieval**: Hybrid search combining semantic vectors and graph relationships
- **Document Analysis**: Advanced processing of various document types
- **Context-Aware Responses**: Maintains conversation history and adapts to user needs
- **Citation Tracking**: Automatically cites document sources in responses

### 🏗️ Advanced Architecture
- **GraphRAG Implementation**: Leverages Neo4j's graph data science capabilities
- **Adaptive RLHF**: Learns and improves response quality over time
- **Plugin Architecture**: Extensible system for additional data sources and models
- **Real-time Evaluation**: Built-in performance metrics and quality grading

### 🎨 Modern User Experience
- **Responsive Web Interface**: Clean, intuitive design with dark mode
- **Real-time Chat**: Streaming responses with typing indicators
- **Document Management**: Upload and organize research materials
- **System Monitoring**: Comprehensive health checks and metrics

### 🔧 Developer Features
- **Comprehensive API**: RESTful endpoints with automatic documentation
- **Evaluation Framework**: Built-in testing and performance measurement
- **Modular Design**: Clean separation of concerns for easy maintenance
- **Docker Integration**: Containerized deployment with docker-compose

## 🏛️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Next.js       │    │    FastAPI       │    │     Neo4j       │
│   Frontend      │◄──►│    Backend       │◄──►│   Graph DB      │
│   (Port 3000)   │    │   (Port 8000)    │    │   (Port 7687)   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └──────────────────────►┌──────────────────────┘
                                 │     Ollama Models
                                 │  (Port 11434)
                                 └───────────────────────
```

### Core Components

1. **Frontend Layer**
   - React 19 with Next.js 14
   - TypeScript for type safety
   - Radix UI components
   - Tailwind CSS styling

2. **Backend Layer**
   - FastAPI with async support
   - Modular service architecture
   - Pydantic data validation
   - CORS-enabled for frontend integration

3. **Data Layer**
   - Neo4j graph database with GDS
   - Vector embeddings with similarity search
   - Schema-based data modeling
   - Redis for caching and sessions

4. **AI/ML Layer**
   - Ollama integration for local inference
   - Granite4 micro model for efficiency
   - MXBAI embeddings for semantic search
   - Adaptive RLHF learning system

## 📋 Prerequisites

- **Python 3.9+** with pip package manager
- **Node.js 16+** with npm package manager
- **Docker Desktop** for containerized services
- **Ollama** for local LLM inference
- **4GB+ RAM** recommended for optimal performance

### System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| RAM | 8GB | 16GB+ |
| CPU | 4 cores | 8+ cores |
| Storage | 20GB | 50GB+ |
| Network | Stable internet | High-speed |

## 🚀 Quick Start

### 1. Clone and Setup

```bash
git clone https://github.com/kliewerdaniel/basicbot.git
cd basicbot
```

### 2. Initial Setup

```bash
# Run comprehensive setup script
./setup.sh
```

This script will:
- Create Python virtual environment
- Install all dependencies
- Setup Docker containers (Neo4j, Redis)
- Pull required Ollama models
- Create database schema and indexes
- Perform initial data ingestion if files are present

### 3. Start the Application

```bash
# Start all services
./start.sh
```

### 4. Access the Application

- **Web Interface**: http://localhost:3000
- **API Documentation**: http://localhost:8000/docs
- **Neo4j Browser**: http://localhost:7474
- **API Health Check**: http://localhost:8000/api/health

## 📖 Usage

### Web Interface

1. **Navigate to the web interface**
2. **Upload documents** through the document management panel
3. **Ask questions** in the chat interface
4. **Review responses** with source citations and relevance scores

### API Usage

#### Chat Endpoint
```bash
curl -X POST http://localhost:8000/api/chat \
  -H "Content-Type: application/json" \
  -d '{
    "query": "What are the main approaches to neural network optimization?",
    "chat_history": [],
    "session_id": "optional-session-id"
  }'
```

#### Document Search
```bash
curl "http://localhost:8000/api/search?q=neural%20network%20optimization&limit=10"
```

#### System Health
```bash
curl http://localhost:8000/api/health
```

### Data Ingestion

#### CSV Data Files
```bash
# Ingest CSV data files
python3 scripts/ingest_data.py --csv data/your_data.csv --create-indexes
```

#### Research Papers
```bash
# Ingest PDF research papers
python3 scripts/ingest_research_data.py --directory data/research_papers/
```

## 🔧 Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `NEO4J_URI` | `bolt://localhost:7687` | Neo4j connection URI |
| `NEO4J_USERNAME` | `neo4j` | Neo4j username |
| `NEO4J_PASSWORD` | `research2025` | Neo4j password |
| `REDIS_URL` | `redis://localhost:6379` | Redis connection URL |
| `OLLAMA_HOST` | `localhost:11434` | Ollama server address |
| `PORT` | `8000` | FastAPI server port |

### Model Configuration

Models are configured in `data/persona.json`:

```json
{
  "name": "Research Assistant",
  "ollama_model": "granite4:micro-h",
  "rlhf_thresholds": {
    "retrieval_required": 0.6,
    "citation_requirement": 0.8,
    "formality_level": 0.7
  }
}
```

## 🧪 Evaluation & Testing

### Running Evaluations

```bash
# Run comprehensive evaluation suite
python3 evaluation/run_evaluation.py
```

### Performance Metrics

The system provides several evaluation metrics:

- **Retrieval Quality**: Precision and recall of document retrieval
- **Response Accuracy**: Alignment with ground truth answers
- **Context Relevance**: Usefulness of retrieved documents
- **Response Quality**: Readability and completeness scores

### Test Datasets

Evaluation datasets are located in `evaluation/datasets/`:
- `research_assistant_v1.json` - General research questions
- `stress_tests.json` - Edge cases and performance limits

## 🏗️ Development

### Project Structure

```
basicbot/
├── frontend/                 # Next.js application
│   ├── src/
│   │   ├── app/             # Next.js app router
│   │   ├── components/      # React components
│   │   └── lib/             # Utilities and configurations
│   └── package.json
├── scripts/                  # Python core logic
│   ├── eps_reasoning_agent.py
│   ├── eps_retriever.py
│   ├── graph_schema.py
│   └── ingest_*.py
├── evaluation/               # Testing and metrics
│   ├── run_evaluation.py
│   ├── metrics.py
│   └── datasets/
├── data/                     # Sample data and configurations
├── test_*.py                 # Test scripts
├── main.py                   # FastAPI application
├── requirements.txt          # Python dependencies
├── docker-compose.yml        # Container orchestration
└── README.md
```

### Setting up Development Environment

```bash
# Backend development
cd basicbot
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
pip install -r requirements-dev.txt  # If available

# Frontend development
cd frontend
npm install
npm run dev

# Database development (in separate terminal)
docker-compose up neo4j redis
```

### Running Tests

```bash
# Backend tests
python3 -m pytest

# Frontend tests
cd frontend
npm test

# Integration tests
./test.sh
```

## 📚 API Reference

### Core Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/chat` | POST | Main chat interface with GraphRAG |
| `/api/search` | GET | Direct document search |
| `/api/health` | GET | System health check |
| `/api/status` | GET | Detailed system status |
| `/api/ingest` | POST | Trigger data ingestion |
| `/api/evaluate` | POST | Run evaluation suite |

### Request/Response Examples

#### POST /api/chat
**Request:**
```json
{
  "query": "What are the benefits of using convolutional neural networks?",
  "chat_history": [
    {
      "role": "user",
      "content": "How do neural networks work?"
    },
    {
      "role": "assistant",
      "content": "Neural networks are computational models..."
    }
  ],
  "session_id": "session-123"
}
```

**Response:**
```json
{
  "response": "Convolutional neural networks offer several key benefits...",
  "context_used": [...],
  "quality_grade": 0.85,
  "retrieval_method": "hybrid",
  "retrieval_performed": true,
  "sources": [...],
  "session_id": "session-123"
}
```

## 🤝 Contributing

We welcome contributions to BasicBot! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/your-feature`
3. **Make your changes** following our coding standards
4. **Add tests** for new functionality
5. **Run evaluation suite** to ensure performance
6. **Submit a pull request**

### Development Guidelines

- **Code Style**: Follow PEP 8 for Python, ESLint for JavaScript
- **Documentation**: Update README and docstrings for new features
- **Testing**: Maintain test coverage above 80%
- **Performance**: Ensure changes don't degrade system performance

### Adding New Features

1. **Discuss** the feature in an issue first
2. **Design** the API changes required
3. **Implement** following established patterns
4. **Test thoroughly** with the evaluation framework
5. **Document** the new functionality

## 📊 Performance & Benchmarks

### Typical Performance

- **Query Response Time**: 2-5 seconds for complex questions
- **Document Ingestion**: ~1000 documents/hour
- **Memory Usage**: 4-8GB during normal operation
- **Concurrent Users**: 10-20 simultaneous sessions

### Scaling Considerations

- **Database**: Neo4j can handle millions of documents
- **LLM**: Ollama supports multiple concurrent requests
- **Frontend**: Next.js handles high traffic efficiently
- **Caching**: Redis layer improves response times for repeated queries

## 🔒 Security & Privacy

- **Local AI**: All processing happens locally using Ollama
- **No Data Transmission**: Documents stay on your system
- **Container Isolation**: Services run in isolated Docker containers
- **Input Sanitization**: All inputs are validated and sanitized
- **Session Management**: Secure session handling with UUIDs

## 🐛 Troubleshooting

### Common Issues

**Application won't start**
```bash
# Check Docker services
docker-compose ps

# Check Ollama status
ollama list

# Verify ports are available
lsof -i :8000,3000,7474,7687
```

**Poor response quality**
```bash
# Check data ingestion
python3 -c "from scripts.retriever import Retriever; r=Retriever(); print(len(r.retrieve_context('test',1)))"

# Review RLHF thresholds
cat data/persona.json
```

**Database connection errors**
```bash
# Verify Neo4j is running
curl http://localhost:7474

# Check connection settings
docker-compose logs neo4j
```

### Getting Help

- **Check the Health Endpoint**: `/api/health` for system status
- **Review Logs**: Check container logs with `docker-compose logs`
- **Run Diagnostics**: Execute `./test.sh` for system diagnostics

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Neo4j** for graph database technology
- **Ollama** for local LLM capabilities
- **FastAPI** for excellent Python web framework
- **Next.js** for modern React development
- **Open Source Community** for development tools and libraries

## 🔗 Links

- [Neo4j Documentation](https://neo4j.com/docs/)
- [Ollama Models](https://ollama.ai/library)
- [FastAPI Guide](https://fastapi.tiangolo.com/)
- [Next.js Documentation](https://nextjs.org/docs)

---

*BasicBot - Transforming research analysis with GraphRAG technology* 🚀
