## Wikipedia Semantic Speedrunner

A high-performance pathfinding agent that navigates the Wikipedia knowledge graph using Sentence-BERT (SBERT) and heuristic-based search. Instead of a blind search (BFS), this agent understands the semantic relationship between topics to find the most efficient path between any two articles.

## Performance Benchmarks
The system was stress-tested across 300+ automated trials in various environments. The Academic mode, characterized by high conceptual density, achieved a near-perfect success rate.

Benchmark Results

Mode | Success Rate | Avg. Time (sec) | Search Depth 

 Academic - %93.67 - 9.36s - High semantic density with academic topics 

 Vital - %83.33 - 18.90s - Top 10,000th wikipedia articles 

 Deep - %75.00 - 20.45s - Niche topics / Low semantic density 

## Technical Architecture
The technical architecture of the Wikipedia Speedrunner centers on a Semantic Priority Search that leverages the Sentence-BERT (all-MiniLM-L6-v2) model to transform the traditional graph traversal problem into a vector-space optimization task. By encoding Wikipedia article titles into 384-dimensional embeddings, the system calculates the Cosine Similarity between current outgoing links and the target destination, effectively steering the agent toward conceptually related topics rather than relying on brute-force exploration. This core logic is augmented by a multi-layered heuristic scoring system—including lexical pre-filtering with regex, keyword boosting, and depth penalties to prevent "semantic drift"—all managed within a Priority Queue (heapq) to ensure that the most promising paths are always expanded first.

## Tech Stack
NLP: Sentence-Transformers (BERT), PyTorch.

Core Logic: Python, heapq (Priority Queues), re (Lexical Analysis).

Data Handling: Pandas, NumPy.

API: Wikipedia-API.

## Test Case Result
Start: Homological algebra

Target: Business English

Status: ✅ Success | Steps: 12

Route: Homological algebra ➜ Chess ➜ Business chess ➜ Business game ➜ Business schools ➜ Business administration ➜ Business development ➜ Business organizations ➜ Doing business as ➜ English language ➜ American English ➜ International English ➜ Business English
