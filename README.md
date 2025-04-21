# X-Archive
 
 
# 📚 RAG-based Document Summarization and Evaluation with Ollama Mistral

This project implements a full **Retrieval-Augmented Generation (RAG)** pipeline that reads, cleans, chunks, embeds, summarizes, and evaluates multiple documents using:

- **Local Embeddings** via `SentenceTransformer`
- **Vector Search** with `ChromaDB`
- **Summarization** with **Mistral** (served locally via `Ollama`)
- **ROUGE Metrics** for evaluating summary quality

---

## 🚀 Features

### 📄 Document Processing

- Supports PDFs, DOCX, Excel, CSV
- Cleans text (removes tables, author info, numeric-heavy rows)
- Chunks text into \~500-token segments using `tiktoken`

### 🧠 Embeddings & Storage

- Uses `all-MiniLM-L6-v2` from `sentence-transformers`
- Embeds and stores each chunk in `ChromaDB`
- Tracks token throughput (tokens/second) for performance benchmarking

### 🔍 Retrieval-Augmented Generation (RAG)

- Retrieves relevant chunks using ChromaDB vector search
- Passes context + query to Mistral via Ollama
- Summarizes in academic, human-like tone

### 🧪 Evaluation

- Calculates ROUGE-1, ROUGE-2, and ROUGE-L scores
- Compares model-generated summary to a human reference summary

### 💬 Session Management

- Each interaction is stored using a `session_id`
- Entire chat history can be used as context for refined summarization

---

## 🧰 Technologies Used

- Python 3.10+
- [SentenceTransformers](https://www.sbert.net/)
- [ChromaDB](https://www.trychroma.com/)
- [Ollama](https://ollama.ai/) (for Mistral API)
- PyMuPDF, python-docx, pandas, openpyxl
- tqdm, tiktoken, rouge-score

---

## 📂 Folder Structure

```
.
├── main.py                      # Core pipeline logic
├── chroma_storage/             # ChromaDB persistent vector storage
├── saved_summaries/            # Summaries stored per session
├── performance_log.csv         # Embedding and generation performance metrics
├── all_chunked_text.csv        # All document chunks
├── README.md                   # Project documentation
```

---

## 🧪 How to Run

```bash
# Step 1: Setup environment
pip install -r requirements.txt

# Step 2: Run processing pipeline
python main.py

# Step 3: Summarize and evaluate
summarize_all_documents()
evaluate_summaries_with_rouge(generated_summaries, reference_summaries)
```

---

## 📈 Example ROUGE Output

```
ROUGE1     Precision: 0.2423     Recall: 0.3716     F1: 0.2933    
ROUGE2     Precision: 0.0310     Recall: 0.0476     F1: 0.0375    
ROUGEL     Precision: 0.1101     Recall: 0.1689     F1: 0.1333    
```

---

## 📌 TODO (Optional Enhancements)

-

---

## 👨‍💻 Author

Developed by **[Your Name]** — powered by open-source LLMs and vector databases.

Feel free to fork, extend, or contribute!
