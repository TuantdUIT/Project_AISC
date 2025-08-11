# 📚 RAG ChatBot in E-commerce

# My Team
![image alt](https://github.com/TuantdUIT/Project_AISC/blob/e34ce0ba5fb25b025aecff0c2319725ed2cd586f/DSC_3255.JPG)
---
# Link demo: https://www.youtube.com/watch?v=21EZ339xix8
---
## 1. Project Overview
This project implements a **Retrieval-Augmented Generation (RAG) chatbot** that can answer user queries by combining **semantic search** with a **large language model**.  
The system retrieves the most relevant document chunks from a PDF knowledge base and uses a generative AI model to produce context-aware answers.

The pipeline includes:
- Extracting text from PDF files.
- Splitting the text into manageable chunks.
- Creating vector embeddings for semantic similarity search.
- Using FAISS to store and query these embeddings efficiently.
- Providing the retrieved context to a large language model for answer generation.

---

## 2. Motivation
- **Provide accurate information** to customers when making online purchases.  
- **Reduce time and cost** of customer support operations.  
- **Allow fine-tuning** of the LLM for specific business needs, enabling greater personalization.

---
## 3. Technologies Used

### **Programming Language**
- Python 3

### **Core Libraries**
| Library | Purpose |
|---------|---------|
| **transformers** | Load and use the `google/gemma-2-2b-it` model for text generation. |
| **faiss-cpu** | Vector database for fast nearest neighbor search. |
| **PyPDF2** | Extract text from PDF documents. |
| **nltk** | Sentence tokenization. |
| **pandas** | Data handling and storage of chunks + embeddings. |
| **numpy** | Vector manipulation. |
| **gradio** | Graphic user interface. |
### **Environment**
- Google Colab (with GPU support).
- Google Drive (for storing and loading PDFs).
- Hugging Face model access via personal token.

---

## 4. How It Works

1. **Data Loading**
   - PDF files are loaded from Google Drive.
   - Text is extracted using `PyPDF2`.

2. **Text Splitting**
   - Documents are split into sentence-based chunks using `nltk.sent_tokenize`.
   - Each chunk size is limited to ~1000 characters for better processing.

3. **Embedding Creation**
   - Each chunk is converted into a dense vector embedding using the `all-MiniLM-L6-v2` model from SentenceTransformers.

4. **Indexing with FAISS**
   - All embeddings are stored in a FAISS `IndexFlatL2` index for similarity search.

5. **Retrieval**
   - When a user asks a question, the query is embedded and matched to the top `k` most similar chunks.

6. **Generation**
   - The retrieved chunks are passed as context to the `google/gemma-2-2b-it` model.
   - The model generates a final, context-aware answer

---


