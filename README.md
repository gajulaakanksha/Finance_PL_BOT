# Finance_PL_BOT

# It is a Financial Question & Answering Bot

This repository contains a Streamlit application for answering financial queries using context from uploaded financial documents (e.g., Profit and Loss statements in PDF format). The application uses Hugging Face embeddings for vector-based document search and the Groq LLM (Llama3-8b-8192) for answering questions based on the retrieved context.

## Features
- **PDF Document Upload**: Upload financial documents (e.g., P&L statements) in PDF format.
- **Document Embedding**: Generate vector embeddings from the uploaded document using Hugging Face's `sentence-transformers/all-MiniLM-L6-v2` model.
- **Contextual Retrieval**: Retrieve relevant sections of the document based on user queries using FAISS (Facebook AI Similarity Search).
- **Question Answering**: Generate accurate answers to financial questions using Groq's Llama3-8b-8192 model.
- **Document Similarity Search**: View the specific sections of the document that contributed to the generated answer.

---

## Approach

### Part 1: Retrieval-Augmented Generation (RAG) Model for QA Bot on P&L Data

**Problem Statement**:
To develop a Retrieval-Augmented Generation (RAG) model for a Question Answering (QA) bot that can process financial terms and insights from a Profit & Loss (P&L) table extracted from PDF documents. The QA bot retrieves relevant information related to income, expenses, profit margins, and other key financial metrics and generates accurate responses.

**Implementation Steps**:
1. **Loading and Preprocessing**:
   - Load financial data from P&L tables in PDFs.
   - Parse P&L data into a structured format (e.g., tables or key-value pairs).
2. **Embedding Financial Terms**:
   - Use vectorization techniques (e.g., Hugging Face embeddings) to create document embeddings.
   - Store embeddings in a vector database (e.g., FAISS or Pinecone).
3. **Retrieval-Augmented Generation**:
   - Implement a RAG model to retrieve relevant document chunks.
   - Use Groq's LLM to generate responses based on retrieved context.

---

### Part 2: Interactive QA Bot Interface for Financial Data

**Problem Statement**:
Develop an interactive interface for the QA bot, allowing users to upload PDF documents containing P&L tables and ask questions about the financial data in real time. The interface should display retrieved financial data segments alongside generated answers.

**Implementation Steps**:
1. **Frontend Interface**:
   - Use Streamlit to build a user-friendly interface.
   - Allow users to upload PDF documents and input financial queries.
2. **Backend Integration**:
   - Process uploaded PDFs to extract and preprocess P&L data into structured formats.
   - Store document embeddings in a vector database for efficient retrieval.
   - Use the RAG model to provide real-time answers.
3. **Display Retrieved Data**:
   - Show retrieved financial data segments (e.g., rows or cells from the P&L table) alongside generated answers.
4. **Performance Optimization**:
   - Ensure the system handles large documents and multiple queries efficiently.

---

## Deployment Instructions

### Prerequisites
Ensure you have the following installed:
- Python 3.10+
- pip
- Install necessary libraries such as langchain_groq, langchain_community, PyPDF

### Installation
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. Create a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the root folder and add your Groq API key:
   ```env
   GROQ_API_KEY=<your_groq_api_key>
   ```

### Running the Application
To run streamlit in vscode:
1. Start the Streamlit server:
   ```bash
   streamlit run app.py
   ```

2. Open the application in your browser (usually at `http://localhost:8501`).

To run streamlit in google colab using localtunnel:
1. Install Streamlit
   ```bash
   ! pip install streamlit -q
   ```

2. Retrieves external IP address using the wget command
   ```
   !wget -q -O - ipv4.icanhazip.com
   ```
   After running this cell a password is generated 

3. Runs the Streamlit app in the background & expose the locally running Streamlit app to the internet
   ```
   !streamlit run main.py & npx localtunnel --port 8501
   ```
   click on (your URL) it opens a page where the above password is uploaded then it opens the Finance QA Bot
   
### Using the Application
1. **Upload a PDF**:
   - Click on the file uploader to upload a financial document in PDF format.
2. **Create Document Embeddings**:
   - After uploading the PDF, click the "Create Document Embeddings" button to process the document and generate vector embeddings.
3. **Ask a Question**:
   - Enter your financial query (e.g., "What is the total revenue for the year?") in the text input box and press Enter.
4. **View Results**:
   - The application displays the generated answer.
   - Expand the "Document Similarity Search" section to view retrieved document chunks.

---

## Example Queries and Outputs
- "What is the gross profit for Q3 2024?"
  - **Answer**: $X
  - **Retrieved Data**: Row containing Q3 2024 gross profit.
- "How do net income and operating expenses compare for Q1 2024?"
  - **Answer**: Net income was $Y, and operating expenses were $Z.
  - **Retrieved Data**: Rows containing Q1 2024 net income and operating expenses.
 
  4. **Testing**:
   - Test the model with financial queries such as:
     - "What is the gross profit for Q3 2024?"
     - "How do the net income and operating expenses compare for Q1 2024?"

---

## General Guidelines
- **Containerization**:
  - Use Docker to containerize the application for seamless deployment.
- **Code Quality**:
  - Modular and scalable code with best practices for frontend and backend development.
- **Performance**:
  - Optimize the pipeline to handle large documents and multiple queries without latency issues.
  - Ensure accurate parsing and retrieval of P&L terms for precise question answering.

---

## Future Enhancements
- Add support for other document formats (e.g., Excel, Word).
- Implement additional filtering or ranking mechanisms for retrieved document chunks.
- Optimize embedding creation and retrieval for faster response times.
- Add a feature for downloading answers and retrieved context.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

