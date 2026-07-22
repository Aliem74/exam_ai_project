# Exam AI Project 🎓

An intelligent, adaptive learning system that uses AI agents to generate exam questions and analyze student responses based on course objectives. The system extracts learning materials from university websites, creates targeted assessments, and provides personalized feedback to identify knowledge gaps.

## 🚀 Overview

This project builds a multi-agent AI system that:

- **Extracts course objectives** from university websites (student.chalmers.se)
- **Scrapes past exam questions** and answers from academic sources (ftek.se, etc.)
- **Generates targeted exam questions** aligned with course objectives
- **Analyzes student answers** to assess understanding levels
- **Identifies knowledge gaps** and creates personalized follow-up questions
- **Supports bilingual operation** (Swedish and English)

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        ORCHESTRATOR AGENT                            │
│            (Coordinates all agents, manages user session)            │
└───────┬──────────────┬──────────────┬──────────────┬────────────────┘
        │              │              │              │
        ▼              ▼              ▼              ▼
┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────────┐
│  SCRAPER     │ │  QUESTION    │ │  EVALUATOR   │ │  ADAPTIVE        │
│  AGENT       │ │  GENERATOR   │ │  AGENT       │ │  LEARNING AGENT  │
│              │ │  AGENT       │ │              │ │                  │
│ • Course     │ │ • Creates    │ │ • Analyzes   │ │ • Tracks weak    │
│   objectives │ │   questions  │ │   student    │ │   areas          │
│ • Past exams │ │   aligned to │ │   answers    │ │ • Adjusts        │
│ • Syllabi    │ │   objectives │ │ • Grades     │ │   difficulty     │
│              │ │ • Varies     │ │   responses  │ │ • Generates      │
│              │ │   difficulty │ │ • Identifies │ │   targeted Qs    │
│              │ │              │ │   gaps       │ │                  │
└──────────────┘ └──────────────┘ └──────────────┘ └──────────────────┘
        │              │              │              │
        ▼              ▼              ▼              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                     KNOWLEDGE BASE (Vector DB)                       │
│  • Course objectives (structured)                                   │
│  • Past exam questions + model answers                              │
│  • Student performance history                                      │
│  • Bloom's taxonomy mappings                                        │
└─────────────────────────────────────────────────────────────────────┘
```

## 🤖 AI Models & Infrastructure

### Recommended Free LLM Models

| Model | Use Case | Why |
|-------|----------|-----|
| **Llama 3.1 70B** (via Groq/Together.ai) | Question generation & evaluation | Excellent multilingual, strong reasoning |
| **Mistral Large / Mixtral 8x22B** (via Mistral API) | Complex answer analysis | Good structured output, Swedish support |
| **Qwen2.5 72B** (via Together.ai) | Bilingual tasks | Strong multilingual including Nordic languages |
| **GPT4All / Llama 3.1 8B** (local) | Lightweight tasks, fallback | Runs locally, no API limits |

### Embedding Models
- **multilingual-e5-large**: Excellent Swedish + English embedding model (free via HuggingFace)

### Free API Access
- **Groq**: Free tier with generous rate limits (Llama 3.1, Mixtral)
- **Together.ai**: Free credits on signup, many open models
- **HuggingFace Inference API**: Free tier for most open models
- **Ollama**: Run any model locally, no limits

## 🌍 Bilingual Design

The system supports both Swedish and English through:

1. **Language Detection**: Automatic detection of source content language
2. **Source Language Processing**: Content processed in original language (no translation)
3. **Native Question Generation**: Questions generated in course material's language
4. **Multilingual Embeddings**: Single vector space for both languages using multilingual-e5

## 📋 Key Features

### 🎯 Adaptive Learning
- Maps questions to Bloom's Taxonomy levels:
  - **Remember**: Define, List
  - **Understand**: Explain, Compare  
  - **Apply**: Calculate, Solve
  - **Analyze**: Differentiate, Examine

### 🔍 Smart Content Extraction
- Course objectives from student.chalmers.se
- Past exams from ftek.se and similar academic sources
- PDF parsing for exam documents
- Web scraping for online content

### 📊 Performance Analytics
- Real-time answer evaluation
- Knowledge gap identification
- Personalized question targeting
- Learning progress tracking

## 🛠️ Technology Stack

- **Framework**: LangChain or LlamaIndex for agent orchestration
- **Vector Database**: ChromaDB (local) or Qdrant
- **Web Scraping**: BeautifulSoup + Selenium
- **PDF Processing**: PyMuPDF or pdfplumber
- **Frontend**: Streamlit (rapid prototyping) or FastAPI + React
- **Language Detection**: langdetect or LLM-based

## 🚦 Data Flow

1. **Course Selection**: User selects target course
2. **Content Scraping**: Fetch objectives from student.chalmers.se
3. **Exam Collection**: Retrieve past exams from ftek.se and other sources
4. **Knowledge Base**: Content chunked, embedded, and stored
5. **Question Generation**: AI creates questions mapped to learning objectives
6. **Assessment**: User answers generated questions
7. **Evaluation**: AI analyzes answers against objectives
8. **Adaptation**: System identifies weak areas and generates targeted follow-ups

## 📁 Project Structure

```
exam_ai_project/
├── course_scraping_agent     # Extracts course objectives
├── exam_scraping_agent       # Collects past exam materials
├── knowledge_builder_agent   # Builds and manages knowledge base
├── RAG_impl                  # Retrieval-Augmented Generation implementation
├── .gitignore
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- API keys for chosen LLM providers
- Internet connection for web scraping

### Installation
```bash
git clone https://github.com/Aliem74/exam_ai_project.git
cd exam_ai_project
pip install -r requirements.txt
```

### Configuration
1. Set up API keys in environment variables
2. Configure target university websites
3. Initialize vector database
4. Run the system

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 📧 Contact

For questions or collaboration opportunities, please reach out via GitHub issues or email.

---

*Building the future of adaptive learning with AI* 🤖📚