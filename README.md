# End-to-End RAG (Retrieval-Augmented Generation) System

[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-2.3.3-green.svg)](https://flask.palletsprojects.com/)
[![LangChain](https://img.shields.io/badge/LangChain-0.0.267-orange.svg)](https://langchain.com/)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--3.5--turbo-purple.svg)](https://openai.com/)
[![AWS](https://img.shields.io/badge/AWS-S3-orange.svg)](https://aws.amazon.com/)
[![Docker](https://img.shields.io/badge/Docker-Containerized-blue.svg)](https://docker.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 🚀 Project Overview

A comprehensive **Retrieval-Augmented Generation (RAG)** system designed to handle large-scale document processing and intelligent question-answering capabilities. Built with production-ready architecture and AWS cloud integration, this system efficiently processes large PDFs (2000+ pages) and provides accurate, context-aware responses through advanced semantic similarity search and conversational AI.

### 🎯 Key Features

- **Large Document Processing**: Optimized for handling massive PDFs (2000+ pages) with efficient chunking strategies
- **Production-Ready Architecture**: Built with AWS cloud services and CI/CD best practices
- **Semantic Similarity Search**: ChromaDB-powered vector storage for intelligent document retrieval
- **Scalable Cloud Storage**: AWS S3 integration for unlimited document storage capacity
- **Conversational AI**: OpenAI GPT-3.5-turbo powered chat interface with conversation memory
- **Modern Web Interface**: Clean, responsive Flask-based web application
- **Containerized Deployment**: Docker support for seamless scaling and production deployment

## 🏗️ Architecture

### System Components

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Web Frontend  │    │   Flask Backend │    │   Vector Store  │
│   (HTML/CSS/JS) │◄──►│   (Python)      │◄──►│   (ChromaDB)    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                                │
                                ▼
                       ┌─────────────────┐
                       │   AWS S3        │
                       │   (File Storage) │
                       └─────────────────┘
                                │
                                ▼
                       ┌─────────────────┐
                       │   OpenAI API    │
                       │   (LLM Service) │
                       └─────────────────┘
```

### Technology Stack

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Frontend** | HTML5, CSS3, JavaScript | User interface and interaction |
| **Backend** | Flask 2.3.3, Python 3.11 | Web server and API endpoints |
| **Vector Database** | ChromaDB | Document embeddings and similarity search |
| **Cloud Storage** | AWS S3 | Scalable document storage |
| **LLM Integration** | OpenAI GPT-3.5-turbo | Natural language processing |
| **Document Processing** | LangChain, PyPDF | Text extraction and chunking |
| **Containerization** | Docker | Deployment and scaling |

## 📁 Project Structure

```
End-to-End-RAG-system/
├── app/
│   ├── __init__.py              # Flask application initialization
│   ├── main.py                  # Main application entry point
│   ├── config.py                # Configuration management
│   ├── models/
│   │   ├── __init__.py
│   │   └── vector_store.py      # ChromaDB vector store implementation
│   ├── services/
│   │   ├── __init__.py
│   │   ├── llm_service.py       # OpenAI LLM integration
│   │   └── storage_service.py   # AWS S3 storage service
│   ├── static/
│   │   └── style.css            # Frontend styling
│   └── templates/
│       └── index.html           # Main web interface
├── Dockerfile                   # Container configuration
├── requirements.txt             # Python dependencies
├── LICENSE                      # MIT License
└── README.md                    # Project documentation
```

## 🔧 Technical Implementation

### Core Services

#### 1. Vector Store Service (`app/models/vector_store.py`)
- **ChromaDB Integration**: Persistent vector storage with OpenAI embeddings
- **Similarity Search**: Efficient document retrieval using cosine similarity
- **Document Management**: Add and query document chunks with configurable parameters

#### 2. LLM Service (`app/services/llm_service.py`)
- **Conversational AI**: GPT-3.5-turbo integration with conversation memory
- **Retrieval Chain**: LangChain ConversationalRetrievalChain for context-aware responses
- **Memory Management**: ConversationBufferMemory for maintaining chat history

#### 3. Storage Service (`app/services/storage_service.py`)
- **AWS S3 Integration**: Scalable cloud storage for uploaded documents
- **File Management**: Upload and retrieval operations with error handling
- **Security**: Secure credential management through environment variables

#### 4. Document Processing Pipeline
- **Multi-format Support**: PDF and TXT file processing
- **Intelligent Chunking**: RecursiveCharacterTextSplitter with 1000-character chunks
- **Overlap Strategy**: 200-character overlap for context preservation

### API Endpoints

| Endpoint | Method | Description | Parameters |
|----------|--------|-------------|------------|
| `/` | GET | Main application interface | - |
| `/upload` | POST | Document upload and processing | `file` (multipart/form-data) |
| `/query` | POST | Question-answering endpoint | `question` (JSON) |

## 🚀 Getting Started

### Prerequisites

- Python 3.11+
- Docker (optional)
- AWS Account with S3 access
- OpenAI API key

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/End-to-End-RAG-system.git
   cd End-to-End-RAG-system
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Environment Configuration**
   Create a `.env` file in the project root:
   ```env
   OPENAI_API_KEY=your_openai_api_key
   AWS_ACCESS_KEY=your_aws_access_key
   AWS_SECRET_KEY=your_aws_secret_key
   AWS_BUCKET_NAME=your_s3_bucket_name
   ```

4. **Run the application**
   ```bash
   python app/main.py
   ```

5. **Access the application**
   Open your browser and navigate to `http://localhost:8080`

### Docker Deployment

```bash
# Build the Docker image
docker build -t rag-system .

# Run the container
docker run -p 8080:8080 --env-file .env rag-system
```

## 📊 Performance Features

- **Large Document Handling**: Optimized for processing PDFs with 2000+ pages efficiently
- **Intelligent Chunking**: Advanced text splitting strategies for maintaining context across large documents
- **Semantic Search**: ChromaDB-powered vector similarity search for accurate document retrieval
- **Memory Management**: Conversation memory for contextual responses across multiple queries
- **Production Error Handling**: Comprehensive error handling and logging for production stability
- **Cloud Scalability**: AWS S3 integration for unlimited document storage and EC2 deployment readiness

## 🔒 Security Features

- **Environment Variables**: Secure credential management
- **File Validation**: Type checking for uploaded documents
- **Error Sanitization**: Safe error message handling
- **Temporary File Cleanup**: Automatic cleanup of processed files

## 🧪 Usage Examples

### Document Upload
```javascript
// Upload multiple documents
const formData = new FormData();
formData.append('file', documentFile);
fetch('/upload', {
    method: 'POST',
    body: formData
});
```

### Query Processing
```javascript
// Ask questions about uploaded documents
fetch('/query', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ question: "What is the main topic?" })
});
```

## 🛠️ Development

### Key Dependencies

```txt
flask==2.3.3              # Web framework
langchain==0.0.267         # LLM framework
openai==0.28.0            # OpenAI API client
chromadb                  # Vector database
boto3==1.28.0             # AWS SDK
pypdf==3.9.0              # PDF processing
tiktoken                  # Token counting
unstructured==0.10.30     # Document processing
```

### Configuration Options

- **Chunk Size**: Configurable text chunk size (default: 1000 characters)
- **Chunk Overlap**: Overlap between chunks (default: 200 characters)
- **Similarity Search**: Number of relevant documents retrieved (default: 4)
- **LLM Temperature**: Response creativity control (default: 0.7)

## 🎯 Use Cases

- **Large Document Analysis**: Processing and querying massive PDFs (2000+ pages) for research and analysis
- **Enterprise Knowledge Management**: Corporate knowledge base with AI-powered search across extensive documentation
- **Academic Research**: Handling large research papers, theses, and academic documents
- **Legal Document Processing**: Analyzing extensive legal documents and contracts
- **Technical Documentation**: Processing large technical manuals and documentation sets
- **Customer Support**: Automated responses based on comprehensive documentation libraries

## 🔮 Future Enhancements

- [ ] **React Frontend**: Modern UI/UX with React.js for enhanced user experience
- [ ] **Advanced Chunking**: Semantic chunking strategies for better context preservation
- [ ] **CI/CD Pipeline**: Automated deployment with GitHub Actions or AWS CodePipeline
- [ ] **Performance Metrics**: Comprehensive monitoring and analytics dashboard
- [ ] **Multi-language Support**: Internationalization for global document processing
- [ ] **User Authentication**: Secure access control and user management
- [ ] **Real-time Processing**: WebSocket integration for live document processing
- [ ] **Batch Processing**: Bulk document upload and processing capabilities
- [ ] **Additional File Formats**: Support for DOCX, HTML, Markdown, and more

## 🧠 Key Technical Challenges Solved

### Large Document Processing
- **Challenge**: Handling massive PDFs with 2000+ pages efficiently
- **Solution**: Implemented intelligent chunking strategies with RecursiveCharacterTextSplitter
- **Result**: Optimized text splitting with 1000-character chunks and 200-character overlap for context preservation

### Production-Ready Architecture
- **Challenge**: Building a system that won't fail in production environments
- **Solution**: Implemented comprehensive error handling, logging, and AWS cloud integration
- **Result**: Robust system ready for AWS EC2 deployment with scalable S3 storage

### Semantic Search Optimization
- **Challenge**: Efficient document retrieval from large document collections
- **Solution**: ChromaDB integration with OpenAI embeddings for vector similarity search
- **Result**: Fast and accurate document retrieval using semantic understanding

## 🎓 Technologies & Skills Mastered

### Cloud & DevOps
- **AWS Services**: S3 storage, EC2 deployment, cloud architecture design
- **Docker**: Containerization and deployment strategies
- **CI/CD**: Production deployment best practices and pipeline design

### AI/ML & Data Processing
- **LangChain**: Advanced LLM framework for conversational AI
- **ChromaDB**: Vector database management and semantic similarity search
- **OpenAI API**: GPT-3.5-turbo integration and prompt engineering
- **Document Processing**: Large-scale PDF processing and text chunking strategies

### Backend Development
- **Flask**: Web framework and API development
- **Python**: Advanced Python programming and service architecture
- **Vector Embeddings**: Semantic search and similarity algorithms

## 📈 Technical Achievements

- **Large Document Processing**: Successfully implemented efficient chunking for 2000+ page PDFs
- **Production-Ready Architecture**: Built with AWS cloud services and production best practices
- **Semantic Search Implementation**: ChromaDB integration for advanced vector similarity search
- **Modular Service Design**: Clean separation of concerns with scalable service-oriented architecture
- **Cloud-Native Development**: AWS S3 integration with EC2 deployment readiness
- **Modern AI Integration**: LangChain framework with OpenAI GPT-3.5-turbo for conversational AI
- **Containerized Deployment**: Docker support for seamless scaling and production deployment
- **Error Handling Excellence**: Comprehensive error handling and logging for production stability

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Dhruv Gour**
- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [Your LinkedIn Profile](https://linkedin.com/in/yourprofile)

## 🙏 Acknowledgments

- OpenAI for providing the GPT-3.5-turbo API
- LangChain team for the comprehensive LLM framework
- ChromaDB for the efficient vector storage solution
- AWS for scalable cloud storage services

---

**⭐ If you found this project helpful, please give it a star!**
