# 📚 Multilingual RAG System for Bangla–English PDFs

This project builds a Retrieval-Augmented Generation (RAG) system to answer Bangla and English textbook questions using OCR and semantic search. A REST API is provided for real-time querying, and evaluation metrics measure system quality.

---

## Submission Questions
1. What method or library did you use to extract the text, and why?
We used pytesseract for OCR, paired with pdf2image to render scanned PDF pages. This allowed effective Bangla text extraction. The challenge was that scanned PDFs often have blurry text, causing OCR misreads.

2. What chunking strategy did you choose and why?
We used recursive character-based chunking with 500-character windows and 50-character overlap. This ensures semantic continuity across chunks and balances chunk size for embedding quality and context relevance.

3. What embedding model did you use and why?
We used paraphrase-multilingual-MiniLM-L12-v2 from Hugging Face, as it supports both Bangla and English, provides fast performance, and captures semantic meaning across multilingual content.

4. How are you comparing the query with your stored chunks?
We use cosine similarity between query embedding and chunk embeddings. The top k=3 most relevant chunks are retrieved from the FAISS vector store. FAISS offers fast and efficient similarity search for dense vectors.

5. How do you ensure meaningful comparison between query and documents?
Both queries and chunks are encoded using the same multilingual embedding model. If the query is vague, the retrieval may fetch irrelevant chunks. This can be mitigated by improving query rewriting or using re-ranking.

6. Do the results seem relevant? If not, what might improve them?
