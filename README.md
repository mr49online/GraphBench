# GraphBench: A Benchmark Dataset for Subgraph Spotting and Classification
GraphBench is a curated benchmark dataset designed for evaluating subgraph spotting, classification, and robustness analysis in large heterogeneous graphs. It is constructed using the OGBN-MAG dataset as the base and incorporates both real-world and synthetic subgraph patterns. This dataset supports diverse research tasks including:

- Subgraph classification
- Query graph spotting

---

## Repository Structure 📁
```
GraphBench/
├──📁data/
│   ├──📁raw/                                              # Original OGBN-MAG data
│   |   ├──📁ogbn_mag/
│   |   ├── ogbn_mag_raw.pkl                              
│   ├──📁processed/
│   │   ├── ogbn_mag.gpickle                               # Processed heterogeneous graph
│   │   ├── real_subgraphs_star.jsonl                        
│   │   ├── real_subgraphs_citation_chain.jsonl
│   │   ├── real_subgraphs_institution_star.jsonl
│   │   ├── real_subgraphs_paper_topic_chain.jsonl
│   │   ├── real_subgraphs_author_coaffiliation.jsonl
│   │   ├── real_subgraphs_field_neighborhood.jsonl
│   │   ├── real_subgraphs_author_ego.jsonl
│   │   ├── real_subgraphs_citation_triangle.jsonl
│   │   ├── real_subgraphs_field_cotopic.jsonl
│   │   ├── real_subgraphs_paper_coauthor_star.jsonl
│   │   ├── real_subgraphs.jsonl                           # Final real subgraphs (all combined) 
│   │   ├── ogbn_mag_graph_stats.csv
│   │   ├── ogbn_mag_with_synthetic.gpickle                # Final heterogeneous graph
│   │   ├── labeled_subgraphs.jsonl                        # Real + synthetic subgraph labels
│   │   ├── synthetic_subgraphs.jsonl                      # Inserted synthetic patterns
│   │   ├── real_subgraphs_stats.csv                       # Real subgraphs statistics
│   │   └── graphbench_stats.csv                           # GraphBench statistics
│   ├──📁queries/
│   │   ├── query_subgraphs.jsonl
│   │   ├── query_easy.jsonl
│   │   ├── query_medium.jsonl
│   │   ├── query_hard.jsonl
│   │   ├── query_generation_log.csv
│   │   ├── spotted_queries.jsonl
│   │   ├── query_spotting_summary.csv
│   │   ├── query_spotting.log
│   │   ├──📁evaluation_plots_extended
│   │   |   ├── 
│   │   ├──

├──📁scripts/                                             # Contains pipeline scripts
├──📁demo/
│   └── system_performance.mp4                 # Hardware performance video
├──📁utils/
│   └── query_generators/                      # Query generators for spotting tasks
└── README.md
```
**📊 Dataset Summary**
| File                                | Description                                                     |
| ----------------------------------- | --------------------------------------------------------------- |
| `dblp_graph_with_synthetic.gpickle` | Full NetworkX graph: base + inserted synthetic subgraphs        |
| `labeled_subgraphs.json`            | Real-world subgraph labels (e.g., citation chains, author egos) |
| `query_subgraphs.jsonl`             | Full set of query subgraphs                                     |
| `.csv`                              | Summary statistics                                              |

**📌Key Subgraph Patterns**
Real:
    -Institution Stars, - Paper-Topic Citation Chains, Author Co-Affiliation Graphlets, Multi-hop Collaboration Chains, Paper Clusters, Field of Study Neighborhoods
Synthetic:
    Cliques, Stars, Chains Triangles, Field-based dense motifs (extended)

**⚙️System Requirements**
Python 3.9+, PyTorch Geometric, NetworkX, Scikit-learn, Matplotlib 
**Install dependencies:** 
pip install -r requirements.txt
