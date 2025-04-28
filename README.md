# Multi-Modal Agentic AI Application

A conversational AI system that processes multiple data sources (text documents, PDFs, web content, and videos) to provide comprehensive responses to user queries.

## Overview

This application uses open-source tools to create an AI assistant that can:

- Process text documents and PDFs
- Search the web for relevant information
- Extract information from video content
- Synthesize results from all sources into coherent responses

## Architecture

The system consists of several components:

- **Orchestrator Agent**: Coordinates the other agents and synthesizes their results
- **Text/PDF Agent**: Processes and searches through document collections
- **Web Search Agent**: Retrieves and processes web content
- **Video Agent**: Extracts and transcribes information from video files
- **Streamlit Frontend**: Provides a user-friendly interface

## Technologies Used

- **LLM Integration**: Groq API with Llama3 models
- **RAG Pipeline**: ChromaDB for vector storage
- **Document Processing**: LangChain for document loading and processing
- **Web Search**: DuckDuckGo search via LangChain
- **Video Processing**: Whisper for transcription
- **Storage**: AWS S3 for file storage
- **Frontend**: Streamlit for UI
- **Orchestration**: phidata for deployment

## Prerequisites

- Python 3.10 or higher
- AWS account with S3 bucket
- Groq API key
- Docker (optional, for containerized deployment)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/multi-modal-agent.git
cd multi-modal-agent
```

2. Set up a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Configure environment variables:
```bash
cp .env.template .env
# Edit .env with your API keys and configuration
```

## Running the Application

### Using phidata:

```bash
# Start the application
phi start
```

### Using Docker:

```bash
# Build the Docker image
docker build -t multi-modal-agent .

# Run the container
docker run -p 8501:8501 --env-file .env multi-modal-agent
```

### Manual start:

```bash
# Start the Streamlit app
streamlit run app/frontend/streamlit_app.py
```

## Usage

1. **Upload Content**:
   - Use the sidebar to upload text files, PDFs, or MP4 videos
   - Click "Process Uploaded Files" to index content

2. **Ask Questions**:
   - Type your questions in the chat input
   - The system will search through documents, web content, and video transcriptions
   - Receive comprehensive responses combining all available information

## Project Structure

```
multi-modal-agent/
├── app/
│   ├── __init__.py
│   ├── main.py                 # Main application entry point
│   ├── agents/
│   │   ├── __init__.py
│   │   ├── orchestrator.py     # Orchestrator agent
│   │   ├── text_agent.py       # Text/PDF processing agent
│   │   ├── web_agent.py        # Web search agent
│   │   └── video_agent.py      # Video processing agent
│   ├── utils/
│   │   ├── __init__.py
│   │   ├── embedding.py        # Embedding utilities
│   │   ├── s3_utils.py         # S3 interaction utilities
│   │   └── video_processor.py  # Video processing utilities
│   └── frontend/
│       ├── __init__.py
│       └── streamlit_app.py    # Streamlit frontend
├── workspace/
│   ├── data/                   # Local data storage
│   └── chromadb/               # Vector database storage
├── requirements.txt
├── Dockerfile
├── .env.template
└── phi.yaml                    # phidata configuration
```

## Extending the Application

1. **Add New Agent Types**:
   - Create new agent modules following the pattern of existing agents
   - Update the orchestrator to incorporate the new agent

2. **Improve Processing Capabilities**:
   - Add image recognition capabilities for video frames
   - Implement advanced video scene segmentation
   - Add support for more document types

3. **Enhance UI Features**:
   - Add visualization of agent sources
   - Implement chat history persistence
   - Add user authentication

## Troubleshooting

1. **S3 Access Issues**:
   - Verify AWS credentials
   - Check bucket permissions
   - Ensure proper IAM roles

2. **Model Performance Issues**:
   - Try using different Groq models
   - Adjust chunk sizes for different content types
   - Optimize embedding models based on hardware capabilities

3. **Video Processing Issues**:
   - Check ffmpeg installation
   - Verify Whisper model installation
   - Try processing smaller video segments

## License

This project is licensed under the MIT License - see the LICENSE file for details.
