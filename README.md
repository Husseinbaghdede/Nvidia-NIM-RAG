# NVIDIA NIM Demo - Document Q&A Application

## Overview
This Streamlit application demonstrates how to build a Document Question-Answering system using NVIDIA's AI endpoints and foundation models. The app allows users to upload PDF documents, process them, and ask questions about their content using LLaMA 3 70B model provided through NVIDIA's NIM platform.

## Features
- Load and process multiple PDF documents from a directory
- Create vector embeddings using NVIDIA's embedding models
- Generate semantic search using FAISS vector database
- Answer questions based on the document content using meta/llama3-70b-instruct model
- Interactive Streamlit interface for easy interaction

## Prerequisites
- Python 3.8+
- NVIDIA API Key (sign up at [NVIDIA Developer Portal](https://developer.nvidia.com/))

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/nvidia-nim-demo.git
cd nvidia-nim-demo
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. Create a `.env` file in the project root with your NVIDIA API key:
```
NVIDIA_API_KEY=your_nvidia_api_key_here
```

## Project Structure
```
nvidia-nim-demo/
├── finalapp.py        # Main Streamlit application file
├── .env               # Environment variables file (create this)
├── requirements.txt   # Package dependencies
├── data/              # Directory to store PDF documents
│   └── (your PDF files go here)
└── README.md          # This file
```

## Usage

1. Place your PDF documents in the `data/` directory.

2. Run the Streamlit app:
```bash
streamlit run finalapp.py
```

3. Open your browser and navigate to the provided URL (typically http://localhost:8501).

4. Click on "Document Embedding" to process the documents and create the vector store.

5. Enter your question in the text input field and receive answers based on the document content.

## How It Works

1. **Document Loading**: The application uses PyPDFDirectoryLoader to load all PDF documents from the data folder.

2. **Text Chunking**: The loaded documents are split into manageable chunks using RecursiveCharacterTextSplitter.

3. **Vector Embedding**: NVIDIA's embedding models convert text chunks into vector representations.

4. **Vector Database**: FAISS is used to create a vector database for efficient similarity search.

5. **Question Answering**: When a user asks a question, the system:
   - Retrieves relevant document chunks using semantic search
   - Passes these chunks along with the question to the LLaMA 3 70B model
   - Returns the generated answer based on the document content

## Performance Notes
- The application tracks and prints the response time for each query.
- Currently limited to processing the first 30 documents to manage memory usage.
- Chunk size is set to 700 characters with a 50-character overlap for optimal retrieval.

## Dependencies
- streamlit
- langchain
- langchain-community
- langchain-nvidia-ai-endpoints
- python-dotenv
- faiss-cpu
- PyPDF2

## License
[Specify your license here]

## Acknowledgements
- NVIDIA for providing AI endpoints
- Meta for the LLaMA 3 model
- LangChain for the document processing framework
