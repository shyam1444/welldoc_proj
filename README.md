# AI Visionaries Code Guidelines Analyzer and Correction System

This project is an interactive Gradio application that allows users to upload a PDF containing coding guidelines and then use those guidelines to validate and correct code snippets. The system leverages machine learning components (via LangChain integrations) and a locally hosted language model (e.g., CodeLlama) to provide context-aware responses and code analysis.


## Features

- **PDF Processing**: 
  - Upload a PDF file containing coding guidelines.
  - Extracts text content from the PDF using PyMuPDF and splits it into manageable chunks.
  - Indexes the extracted guidelines in a FAISS vectorstore for efficient retrieval.

- **Chat Interface**: 
  - Ask questions related to the guidelines.
  - Retrieves context-relevant content from the processed PDF.
  - Uses a locally hosted language model to generate answers based on the guidelines.

- **Code Validation**:
  - Paste Java or C# code snippets into the interface.
  - Detects the programming language and compares the code against the uploaded guidelines.
  - Provides analysis, identifies guideline violations, suggests improvements, and offers a corrected version following best practices.

---

## Requirements

- Python 3.7 or higher
- [Gradio](https://gradio.app/)
- [Requests](https://docs.python-requests.org/)
- [PyMuPDF (fitz)](https://pymupdf.readthedocs.io/)
- LangChain Community packages:
  - `langchain_community.document_loaders`
  - `langchain.text_splitter`
  - `langchain_community.vectorstores`
- [HuggingFaceEmbeddings](https://huggingface.co/)
- Other standard libraries: `concurrent.futures`, `re`

---

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/ai-guidelines-analyzer.git
   cd ai-guidelines-analyzer
   ```

2. **Install required packages:**
   ```bash
   pip install gradio requests pymupdf langchain_community langchain_huggingface
   ```

3. **Set up your local language model API:**
   - Ensure that a language model endpoint (e.g., CodeLlama) is running locally on `http://localhost:11434/api/chat`.



## Usage

1. **Run the application:**
   ```bash
   python app.py
   ```
   (Make sure to update the file name if it differs from `app.py`.)

2. **Interface Overview:**
   - **Upload Guidelines PDF**: Use the file upload button to provide your guidelines PDF.
   - **Process Guidelines**: Click the "Process Guidelines" button to extract and index the guidelines.
   - **Ask Questions**: Use the chat interface to ask questions about the guidelines.
   - **Code Validation**: Paste your code snippet in the textbox and click "Enter" to validate the code against the guidelines.

---

## Notes

- **Local API Endpoint**: The system relies on a locally hosted language model API. Ensure the endpoint is available and correctly configured.
- **Language Detection**: The current implementation detects Java and C# based on simple heuristics. You may enhance this for additional languages.
- **Performance**: The processing of PDFs and code validation is done asynchronously to improve performance.

---

## License

This project is open-sourced under the MIT License. Feel free to contribute or modify it as needed.
