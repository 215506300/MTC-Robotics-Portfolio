Creation of an AI Agent named ProgBot
Problem
The objective was to develop an interactive programming tutor chatbot, ProgBot, to assist beginners in learning fundamental programming concepts such as variables, loops, functions, data types, and languages like Python and JavaScript. Key challenges included providing accurate, context-aware responses, handling vague or unmatched queries, incorporating user feedback for dynamic improvement, and ensuring efficient retrieval from a knowledge base without relying on large language models.
Approach

Architecture: Built using a Retrieval-Augmented Generation (RAG) system with a SentenceTransformer model (all-MiniLM-L12-v2) for embedding generation and cosine similarity for matching user queries to a Q&A dataset or fallback context. The system includes data preprocessing (cleaning with NLTK and regex), a pandas DataFrame for storing Q&A pairs (50+ greetings and 40+ programming entries), and a segmented context file (rag_context.txt) for granular retrieval.
Dynamic Learning: Implemented feedback loops where users can correct responses, appending new entries to the dataset and retraining embeddings in real-time using torch.cat. Threshold optimization (0.4-0.9) balances precision/recall, with a lower threshold (0.6) for user-corrected responses.
Error Handling: Used try-except blocks for robustness against invalid inputs or file errors, with debug logging to JSON files for tracking retrieval scores and issues.
Training/Optimization: No traditional training loop; instead, embeddings are generated on-the-fly and updated via user interactions. Tested thresholds with sample queries to maximize accuracy.

Results

Metrics: Achieved 85% retrieval accuracy on 20 simulated queries, with average cosine similarity of 0.75 for matches. Retrieval latency averaged 0.5 seconds; retraining takes ~1 second for small updates. Feedback: 70% "yes" (helpful), 20% corrected, improving subsequent responses. Test cases (e.g., "what is a function") passed at threshold 0.6 after bidirectional substring matching.
Visuals: Cosine similarity plots (via matplotlib) show query-corpus alignments. For example, greetings like "hello" yield exact matches (score 1.0), while complex queries like "how to debug code" retrieve from RAG with scores ~0.7. (Refer to notebook for plotting code; no saved images in files, but visualizations confirm embedding quality during optimization.)
Observations: User corrections enhanced coverage for vague queries (e.g., "what is programming"). Failures (15%) triggered logging, reducing future unknowns.

How to Run
Requirements

Python 3.8+ (Default Google Colab Environment with minimum 8GB RAM recommended)
Libraries: sentence-transformers, nltk, torch, scikit-learn, pandas, numpy, matplotlib

Install dependencies:
textpip install -U sentence-transformers nltk torch scikit-learn pandas numpy matplotlib
For a full list, see Requirements.txt (basic Colab setup).
Commands

Open DL.ipynb in Google Colab or Jupyter Notebook.
Run all cells sequentially: Installs packages, imports libraries, downloads NLTK data, initializes embeddings, and starts the chat loop.
Interact via the chat function: Enter queries like "what is a variable?"; provide feedback when prompted.
To retrain: User corrections automatically update the dataset; call retrain_from_log() manually if needed.
Exit: Type "exit" in the chat prompt.

Monitor memory: Large logs may increase usage; clear variables if needed.
Data Access Notes

Q&A Dataset: Hardcoded in the notebook as a pandas DataFrame with columns like "Greeting", "Response", "Category". Includes ~90 entries for greetings and programming topics.
RAG Context: Stored in rag_context.txt (created in the notebook) with definitions for concepts like variables, loops, etc. Segmented into 55-word chunks for embedding; no external download needed.
Logs: Feedback and unknown queries saved to JSON files (e.g., unknown_log.json) in the working directory. Access via pd.read_json() or file I/O.
No External Data: All data is generated or hardcoded; no datasets like MNIST required.

What I Learned / Next Steps

Learnings: Understood the power of RAG for efficient, low-resource chatbots, including embedding techniques for similarity search and the importance of feedback loops for adaptability. Gained experience in threshold tuning to balance precision/recall, robust error handling with logs, and real-time retraining without full model reloads. Highlighted user experience issues like unnecessary prompts and how to streamline them.
Next Steps:
Implement batch retraining to handle large logs without performance hits.
Expand Q&A corpus with advanced topics (e.g., ML, databases) and multilingual support.
Enhance RAG with overlapping chunks or query rewriting for better vague input handling.
Integrate interactive visualizations (e.g., Chart.js) for similarity plots.
Add input validation for special characters and monitor retraining frequency via logs.
