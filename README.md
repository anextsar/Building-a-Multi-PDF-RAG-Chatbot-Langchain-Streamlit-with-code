# Building-a-Multi-PDF-RAG-Chatbot-Langchain-Streamlit-with-code

Follow me on social media for updates and more content:

<div align="center">
  <a href="https://www.instagram.com/dhiraj7kr/" target="_blank">
    <img src="https://img.shields.io/badge/Instagram-Follow%20Me%20on%20Instagram-red?logo=instagram" alt="Instagram" />
  </a>
  <a href="https://x.com/Dhiraj7kr" target="_blank">
    <img src="https://img.shields.io/badge/Twitter-Follow%20Me%20on%20Twitter-blue?logo=twitter" alt="Twitter" />
  </a>
  <a href="https://github.com/dhiraj7kr" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-Follow%20Me%20on%20GitHub-lightgrey?logo=github" alt="GitHub" />
  </a>
  <a href="https://medium.com/@dhiraj7kr" target="_blank">
    <img src="https://img.shields.io/badge/Medium-Follow%20Me%20on%20Medium-black?logo=medium" alt="Medium" />
  </a>
  <a href="https://www.linkedin.com/in/dhiraj7kr/" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-Connect%20on%20LinkedIn-blue?logo=linkedin" alt="LinkedIn" />
  </a>
</div>

---

# Multi-PDF RAG Chatbot with Langchain & Streamlit

This project demonstrates how to build a **Multi-PDF RAG (Retrieval-Augmented Generation) Chatbot** using **Langchain**, **Streamlit**, **PyPDF2**, and **FAISS**. The application allows users to upload one or more PDF files, processes the content into text, splits it into chunks, and then enables users to interact with the extracted text via a conversational AI model powered by OpenAI.

Users can upload PDF documents, ask questions related to the content, and get responses based on the text extracted from the uploaded PDFs.

---

## Features

- **PDF Upload and Processing**: Allows users to upload multiple PDF files, which are read and processed to extract the text content.
- **Text Chunking**: Breaks down the extracted text into smaller, manageable chunks for efficient processing.
- **Searchable Database**: Converts the text into vector embeddings using **FAISS** and **SpacyEmbeddings**, enabling fast similarity-based searches.
- **Conversational AI**: Uses OpenAI's GPT models to answer questions based on the extracted text.
- **Streamlit Interface**: Provides an easy-to-use web interface for uploading PDFs and asking questions.

---

## Requirements

Before running this project, make sure you have the following:

- Python 3.7 or later
- Streamlit
- PyPDF2
- Langchain
- FAISS
- Spacy
- OpenAI API Key

---

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/anextsar/Building-a-Multi-PDF-RAG-Chatbot-Langchain-Streamlit-with-code.git
    cd multi-pdf-rag-chatbot
    ```

2. Create and activate a virtual environment (optional but recommended):

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. Install the required dependencies:

    ```bash
    pip install -r requirements.txt
    ```

4. You will also need to install **Spacy** and the English language model:

    ```bash
    python -m spacy download en_core_web_sm
    ```

5. Set up your **OpenAI API Key**:

    - You can get your API key from [OpenAI's platform](https://platform.openai.com/).
    - Create a `.env` file in the root directory and add your API key:

    ```bash
    OPENAI_API_KEY=your-openai-api-key
    ```

---

## Project Structure

```
multi-pdf-rag-chatbot/
│
├── app.py                # Main Streamlit app
├── requirements.txt      # Python dependencies
├── .env                  # Environment variables (API keys, etc.)
├── faiss_db/             # Directory for FAISS vector database
└── README.md             # Project documentation
```

---

## Usage

1. **Run the application**:

    After setting up your environment, run the Streamlit app:

    ```bash
    streamlit run app.py
    ```

2. **Upload PDF files**:

    - On the sidebar, click the **Upload PDF Files** button to upload one or more PDF files.
    - Once the files are uploaded, click **Submit & Process** to extract the text and store it in the vector database.

3. **Ask a question**:

    - After processing the PDFs, type your question related to the uploaded documents in the text input box and click **Enter**.
    - The app will process your question and retrieve relevant information from the PDFs, then display the response from the AI model.

4. **See the Response**:

    - The app will show the AI's response based on the extracted text.
    - If the information isn't found in the PDFs, the AI will respond with "answer is not available in the context."

---

## How It Works

### 1. **PDF Upload & Reading**:

   - The app reads the content from uploaded PDFs using `PyPDF2` and extracts the text from each page.
   - The text is merged into a single string, which is then split into smaller chunks for processing.

### 2. **Text Chunking**:

   - The extracted text is split into manageable chunks of 1000 characters with an overlap of 200 characters using Langchain’s `RecursiveCharacterTextSplitter`. This allows the model to effectively process large documents without running into memory issues.

### 3. **Vectorization with FAISS**:

   - The text chunks are converted into vector embeddings using the **Spacy Embeddings** model (`en_core_web_sm`), and these vectors are indexed using **FAISS** for efficient similarity search.
   - The vector store is saved locally, allowing the system to quickly search through the embeddings when answering queries.

### 4. **Conversational AI Setup**:

   - The AI model (OpenAI's `gpt-3.5-turbo`) is used to generate responses to user queries.
   - The Langchain library is used to create a **Retriever Tool**, which retrieves relevant chunks of text based on the question asked.
   - The retrieved text is then passed to the AI model to generate a detailed response.

### 5. **Streamlit Interface**:

   - The user interacts with the application through a simple web interface built with **Streamlit**. Users can upload PDF files and type in their questions to get answers from the documents.

---

## Example Interaction

1. Upload a PDF with the content of a book or a research paper.
2. Type in a question related to the document, such as:

    - "What is the main conclusion of the paper?"
    - "Can you summarize the introduction?"

3. The AI will process your question, search for relevant text from the uploaded PDFs, and generate an accurate answer based on the document content.

---

## Troubleshooting

- **FAISS errors**: Ensure that the vector store is saved correctly in the `faiss_db` directory. If you encounter errors loading the vector store, try re-uploading and processing the PDFs.
- **No response from the AI**: Double-check your OpenAI API key is correctly set in the `.env` file.

---

## Contributing

Contributions are welcome! If you have suggestions, improvements, or bug fixes, feel free to open an issue or submit a pull request.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

- **Langchain**: For providing a powerful framework for integrating language models and external tools.
- **PyPDF2**: For PDF text extraction.
- **FAISS**: For efficient vector search.
- **OpenAI**: For providing GPT models for natural language understanding.

---

## For More Details

For a more detailed explanation of how to build the Multi-PDF RAG Chatbot, visit the full blog post on [Medium](https://medium.com/@dhiraj7kr/building-a-multi-pdf-rag-chatbot-langchain-streamlit-with-code-0dcad2f4f069).
