# Wikipedia Semantic Speedrunner

A high-performance pathfinding agent that navigates the Wikipedia knowledge graph using Sentence-BERT (SBERT) and heuristic-based search. Instead of a blind search (BFS), this agent understands the semantic relationship between topics to find the most efficient path between any two articles.

# Performance Benchmarks
The system was stress-tested across 300+ automated trials in various environments. The Academic mode, characterized by high conceptual density, achieved a near-perfect success rate.
## Benchmark Results

| Mode | Success Rate | Avg. Time (sec) | Search Depth |
| **Academic** | %93.67 | 9.36s | High semantic density with academic topics |
| **Vital** | %83.33 | 18.90s | Top 10,000th wikipedia articles |
| **Deep** | %75.00 | 20.45s | Niche topics / Low semantic density |

# Technical Architecture
The engine utilizes the all-MiniLM-L6-v2 transformer model to encode Wikipedia titles into a 384-dimensional vector space, calculating conceptual proximity in real-time.

## Semantic Decision Engine
The bot performs a Semantic Priority Search. For every page, it extracts all outgoing links and scores them based on their Cosine Similarity to the target. This transforms the "Wikipedia Game" from a random click-fest into a calculated vector-space navigation.

## Multi-Layer Heuristics
To handle the "Semantic Drift" (getting stuck in niche sub-topics), the following optimizations were implemented:

Keyword Boosting: Prioritizes links containing target keywords for higher lexical alignment.

Strategic Positioning: Gives a weight bonus to links found in the introduction of an article (statistically more relevant).

Depth Penalty: A cost function that discourages aimless wandering, forcing the agent to find shorter paths.

Fast Pre-Filtering: A regex-based lexical scanner that prunes the search space before expensive transformer encoding.

## Data Engineering & Robustness
Rate-Limit Management: Adaptive sleep cycles (0.04s) to respect Wikipedia's infrastructure.

Automated Benchmarking: Built-in suites for 'Vital', 'Academic', and 'Deep' content pools.

Interim Logging: Checkpointed CSV logging every 10 iterations to ensure data persistence during long runs.

# Tech Stack
NLP: Sentence-Transformers (BERT), PyTorch.

Core Logic: Python, heapq (Priority Queues), re (Lexical Analysis).

Data Handling: Pandas, NumPy.

API: Wikipedia-API.

# Real-World Result
Start: Homological algebra

Target: Business English

Status: ✅ Success | Steps: 12

Route: Homological algebra ➜ Chess ➜ Business chess ➜ Business game ➜ Business schools ➜ Business administration ➜ Business development ➜ Business organizations ➜ Doing business as ➜ English language ➜ American English ➜ International English ➜ Business English
