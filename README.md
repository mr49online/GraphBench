**# GraphBench: A Benchmark Dataset for Subgraph Spotting and Classification **
GraphBench is a curated benchmark dataset designed for evaluating subgraph spotting, classification, and robustness analysis in large heterogeneous graphs. It is constructed using the OGBN-MAG dataset as the base and incorporates both real-world and synthetic subgraph patterns. This dataset supports diverse research tasks including:

- Subgraph classification
- Query graph spotting

---

**📁 Repository Structure**
GraphBench/
├── data/
│   ├── raw/                      # Original OGBN-MAG data
│   ├── processed/
│   │   ├── dblp_graph_with_synthetic.gpickle  # Final heterogeneous graph
│   │   ├── labeled_subgraphs.json             # Real + synthetic subgraph labels
│   │   ├── synthetic_subgraphs.jsonl          # Inserted synthetic patterns
│   │   └── validation_report.csv              # Graph statistics
├── scripts/
│   ├── 01_load_dblp.py
│   ├── 02_build_graph.py
│   ├── 03_extract_real_subgraphs.py
│   ├── 04_insert_synthetic_subgraphs.py
│   ├── 05_label_and_export.py
│   ├── 06_visualize.py
│   ├── 07_train_classifiers.py
│   ├── 09_generate_query_subgraphs.py
│   ├── 10_visualize_query_subgraphs.py
│   ├── 11_spot_query_subgraphs.py
│   ├── 12_evaluate_spotted_queries.py
│   ├── 14_visualize_query_within_source.py
│   ├── 15_summarize_query_evaluation.py
│   ├── 16_visualize_top_and_skipped_queries
│   └── 17_analyze_homo_vs_hetero_queries
├── demo/
│   └── system_performance.mp4                 # Hardware performance video
├── utils/
│   └── query_generators/                      # Query generators for spotting tasks
└── README.md

**📊 Dataset Summary**
| File                                | Description                                                     |
| ----------------------------------- | --------------------------------------------------------------- |
| `dblp_graph_with_synthetic.gpickle` | Full NetworkX graph: base + inserted synthetic subgraphs        |
| `labeled_subgraphs.json`            | Real-world subgraph labels (e.g., citation chains, author egos) |
| `synthetic_subgraphs.jsonl`         | Inserted synthetic cliques, stars, chains, and more             |
| `validation_report.csv`             | Summary statistics (nodes, edges, type distribution)            |

**📌 Key Subgraph Patterns**
Real:
    Institution Stars, Paper-Topic Citation Chains, Author Co-Affiliation Graphlets, Multi-hop Collaboration Chains, Paper Clusters, Field of Study Neighborhoods
Synthetic:
    Cliques, Stars, Chains Triangles, Field-based dense motifs (extended)

**⚙️ System Requirements**
Python 3.9+, PyTorch Geometric, NetworkX, Scikit-learn, Matplotlib 
**Install dependencies:** 
pip install -r requirements.txt
