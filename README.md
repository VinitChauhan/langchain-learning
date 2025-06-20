# LangChain Learning Project

A comprehensive learning project for LangChain, featuring chat models, environment variable management, and practical examples.

## 🚀 Features

- **Chat Models Integration**: Learn to use OpenAI and other chat models with LangChain
- **Environment Variable Management**: Secure API key handling with `.env` files
- **Jupyter Notebooks**: Interactive learning with step-by-step examples
- **Error Handling**: Common issues and their solutions
- **Best Practices**: LangChain usage patterns and recommendations

## 📋 Prerequisites

- Python 3.8 or higher
- OpenAI API key
- pip (Python package installer)

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd langchain-learning
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirement.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the project root:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   ```

## 📚 Project Structure

```
langchain-learning/
├── chat-models/
│   └── lession-1.ipynb          # Chat models tutorial
├── main.py                      # Main application file
├── requirement.txt              # Python dependencies
├── pyproject.toml              # Project configuration
├── .env                        # Environment variables (create this)
└── README.md                   # This file
```

## 🎯 Quick Start

### 1. Environment Variables Setup

Create a `.env` file in your project root:

```env
# API Keys
OPENAI_API_KEY=your_openai_api_key_here

# Application Settings
DEBUG=True
ENVIRONMENT=development

# Model Configuration
MODEL_NAME=gpt-4o-mini
MAX_TOKENS=1000
TEMPERATURE=0.7
```

### 2. Load Environment Variables in Jupyter

```python
# In your Jupyter notebook
import os
from dotenv import load_dotenv

# Load environment variables
load_dotenv()

# Access variables
api_key = os.getenv('OPENAI_API_KEY')
print(f"API Key loaded: {'Yes' if api_key else 'No'}")
```

### 3. Initialize Chat Model

```python
from langchain_openai import ChatOpenAI

model = ChatOpenAI(
    model="gpt-4o-mini",
    api_key=os.getenv("OPENAI_API_KEY"),
    temperature=0.7
)

print(f"Model initialized: {model.model_name}")
```

### 4. Use Chat Prompt Templates

```python
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser

# Create prompt template
prompt = ChatPromptTemplate.from_messages([
    ("system", "You are a helpful assistant."),
    ("user", "{input}")
])

# Create chain
chain = prompt | model | StrOutputParser()

# Use the chain
response = chain.invoke({"input": "Hello, how are you?"})
print(response)
```

## 📖 Tutorial: Chat Models

### Lesson 1: Basic Chat Model Setup

Open `chat-models/lession-1.ipynb` to learn:

1. **Environment Variable Loading**
   - Using `python-dotenv`
   - Secure API key management
   - Error handling

2. **Model Initialization**
   - OpenAI chat models
   - Parameter configuration
   - Model selection

3. **Prompt Templates**
   - Creating ChatPromptTemplate
   - Formatting prompts
   - Chain creation

4. **Common Errors & Solutions**
   - Import errors
   - ValueError fixes
   - Best practices

### 3. Environment Variables Not Loading

**Problem**: `.env` file not found or not loaded.

**Solution**: Check file location and loading:
```python
import os
from dotenv import load_dotenv

# Load from current directory
load_dotenv()

# Check if loaded
api_key = os.getenv('OPENAI_API_KEY')
if not api_key:
    print("❌ API key not found. Check your .env file")
```

## 📦 Dependencies

Key packages used in this project:

- `langchain`: Core LangChain functionality
- `langchain-openai`: OpenAI model integration
- `langchain-community`: Community model providers
- `langchain-core`: Core LangChain components
- `python-dotenv`: Environment variable management
- `jupyter`: Interactive notebooks
- `openai`: OpenAI API client

## 🎓 Learning Resources

- [LangChain Documentation](https://python.langchain.com/)
- [OpenAI API Documentation](https://platform.openai.com/docs)
- [Jupyter Notebook Tutorial](https://jupyter.org/try)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

If you encounter any issues:

1. Check the [Common Issues](#common-issues--solutions) section
2. Review the LangChain documentation
3. Open an issue with detailed error information

## 🔄 Updates

Stay updated with the latest LangChain changes:

```bash
pip install --upgrade langchain langchain-openai langchain-community
```

---

**Happy Learning! 🚀**