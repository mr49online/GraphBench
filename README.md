# HSB-GDL: A Heterogeneous Subgraph Benchmark for Geometric Deep Learning
HSB-GDL is a curated benchmark dataset designed for evaluating subgraph spotting, classification, and robustness analysis in large heterogeneous graphs. It is constructed using the OGBN-MAG dataset as the base and incorporates both real-world and synthetic subgraph patterns. This dataset supports diverse research tasks including:

- Subgraph classification
- Query graph spotting

---

## Repository Structure 📁
```
HSB-GDL/
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
│   │   ├── ogbn_mag_stats.csv
│   │   ├── ogbn_mag_with_synthetic.gpickle                # Final heterogeneous graph
│   │   ├── labeled_subgraphs.jsonl                        # Real + synthetic subgraph labels
│   │   ├── synthetic_subgraphs.jsonl                      # Inserted synthetic patterns
│   │   ├── real_subgraphs_stats.csv                       # Real subgraphs statistics
│   │   └── hsb_gdl_stats.csv                              # HSB-GDL statistics
│   ├──📁queries/
│   │   ├── query_subgraphs.jsonl
│   │   ├── query_generation_log.csv
│   │   ├── query_easy.jsonl
│   │   ├── query_medium.jsonl
│   │   ├── query_hard.jsonl
│   │   ├── difficulty_distribution.png 
│   │   ├── strategy_distribution.png
│   │   ├── node_type_diversity.png
│   │   ├──📁visualizations
│   │   |   ├── query_types_grid.png
│   │   |   ├── query_statistics.csv
│   │   |   ├── query_synthetic_bidir_chain.png
│   │   |   ├── query_institution_star.png
│   │   |   ├── query_synthetic_chain.png
│   │   |   ├── query_field_cotopic.png
│   │   |   ├── query_synthetic_clique.png
│   │   |   ├── query_synthetic_ring.png
│   │   |   ├── query_synthetic_star.png
│   │   |   ├── query_synthetic_double_star.png
│   │   |   ├── query_author_coaffiliation.png
│   │   |   ├── query_author_ego.png
│   │   |   ├── query_paper_topic_chain.png
│   │   |   ├── query_real_star.png
│   │   |   ├── query_citation_chain.png
│   │   |   ├── query_paper_coauthor_star.png
│   │   |   ├── query_citation_triangle.png
│   │   |   ├── query_field_neighborhood.png
│   │   |   ├── query_hybrid_motif.png
│   │   |   ├── query_motif_clique.png
│   │   |   ├── query_ego_dense_2hop.png
│   │   |   ├──query_ego_dense.png
│   │   ├── spotted_queries.jsonl
│   │   ├── query_spotting_summary.csv
│   │   ├── query_spotting.log
│   │   ├── evaluation_report.csv
│   │   ├──📁evaluation_plots
│   │   |   ├── f1_vs_match_count.png
│   │   |   ├── f1_vs_node_types_by_difficulty.png
│   │   |   ├── f1_vs_query_size.png
│   │   |   ├── f1_vs_top_score.png
│   │   |   ├── match_quality_distribution.png
│   │   |   ├── node_type_bucket_heatmap.png
│   │   |   ├── precision_vs_recall_by_difficulty.png
│   │   |   ├── recall_vs_node_type.png
│   │   |   ├── recall_vs_query_density.png
│   │   |   ├── recall_vs_similarity_by_difficulty.png
│   │   ├──📁evaluation_plots_extended
│   │   |   ├── f1_by_difficulty_extended.png
│   │   |   ├── coverage_rate_barplot.png
│   │   |   ├── f1_by_heterogeneous_extended.png
│   │   |   ├── false_positive_rate_barplot.png
│   │   |   ├── match_count_boxplot.png
│   │   |   ├── correlation_matrix.png
│   │   |   ├── f1_score_boxplot.png
│   │   ├──📁summary
│   │   |   ├── aggregated_metrics_by_type.csv
│   │   |   ├── avg_metrics_per_type_heatmap.png
│   │   |   ├── difficulty_heatmap.png
│   │   |   ├── match_rate_per_type.png
│   │   |   ├── method_heatmap.png
│   │   |   ├── query_spotting_summary.txt
│   │   ├──
├──📁scripts/                                                      # Contains pipeline scripts
├──📁demo/
│   └── system_performance_while_query_generation_script_09.mp4    # Hardware performance video
├──📁utils/
│   └── query_generators/                                          # Query generators for spotting tasks
└── README.md
```
**📊 Dataset Summary**
| File                                | Description                                                     |
| ----------------------------------- | --------------------------------------------------------------- |
| `ogbn_mag_with_synthetic.gpickle`   | Full NetworkX graph: base + inserted synthetic subgraphs        |
| 'real_subgraphs.jsonl'              | Extracted real subgraphs                                        |
| `synthetic_subgraphs.jsonl'         | Injected synthetic subgraphs                                    |
| `labeled_subgraphs.json`            | Real-world subgraph labels (e.g., citation chains, author egos) |
| `query_subgraphs.jsonl`             | Full set of query subgraphs                                     |


**📌Key Subgraph Patterns**
Real:
    -Institution Stars, - Paper-Topic Citation Chains, Author Co-Affiliation Graphlets, Multi-hop Collaboration Chains, Paper Clusters, Field of Study Neighborhoods
Synthetic:
    Cliques, Stars, Chains Triangles, Field-based dense motifs (extended)

**⚙️System Requirements**
Python 3.9+, PyTorch Geometric, NetworkX, Scikit-learn, Matplotlib 
**Install dependencies:** 
pip install -r requirements.txt
