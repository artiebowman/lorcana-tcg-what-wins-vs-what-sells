# What Wins vs. What Sells: Knowledge Discovery in Disney Lorcana's Competitive and Collector Markets

**CIS 635 — Knowledge Discovery and Data Mining**
Grand Valley State University | Professor Jiaxin Du | April 2026

## Authors

Artie Bowman, Mohammad Aziz Boufaied, Kennedy Comstock, Nurudeen Showole

## Abstract

This study applies a Knowledge Discovery in Databases (KDD) pipeline to Disney Lorcana, a trading card game with a dual-market ecosystem driven by competitive strategy and Disney IP collector demand. Drawing on 2,065 unique cards, 753 post-rotation decklists across 21 tournaments (September 2025–March 2026), and 9 price snapshots covering 407 cards, we construct an integrated framework spanning TF-IDF text extraction, K-Means clustering, Random Forest and XGBoost classification with SHAP explainability, NetworkX graph analysis, FP-Growth association rules, Prophet forecasting, and a novel Sleeper Card Index (SCI).

**Central finding:** *What wins and what sells are fundamentally different.* SHAP identifies deck-level optimization features as Top-8 predictors, while the market prices Disney IP recognition and rarity rather than competitive traits.

## Repository Structure

```
├── README.md
├── Lorcana_KDD_Pipeline.ipynb    # Full analysis notebook (98 cells, runs in Google Colab)
├── paper/
│   ├── Lorcana_KDD_Paper_FINAL.md    # Paper source (Markdown)
│   └── Lorcana_KDD_Paper_FINAL.docx  # Paper (Word, formatted)
└── figures/
    ├── fig_06_clusters.png            # PCA deck clusters with Top-8 overlay
    ├── fig_08_card_centroids.png      # Card cluster centroid heatmap
    ├── fig_13_shap_comparison.png     # SHAP feature importance (RF vs XGBoost)
    ├── fig_14_dependence_plots.png    # SHAP dependence plots (top 4 features)
    ├── fig_17_trait_price_spearman.png # Trait-price Spearman correlations
    ├── fig_25_network.png             # Card co-occurrence network (4 communities)
    ├── fig_26_association_rules.png   # Association rules (support vs confidence)
    ├── fig_27_sci.png                 # Sleeper Card Index (under/overvalued)
    ├── fig_28_confusion_matrices.png  # Confusion matrices (RF vs XGBoost)
    └── fig_multimodel_comparison.png  # Multi-model comparison bar chart
```

## Key Results

| Metric | Value |
|--------|-------|
| Dataset | 753 decks, 21 tournaments, 12 countries |
| RF weighted F1 | 0.773 (AUC 0.549) |
| XGBoost weighted F1 | 0.765 (AUC 0.456) |
| Majority baseline F1 | 0.780 |
| Placement regression | R² = 0.007, ρ = 0.235, p = 0.003 |
| Ablation (full pipeline) | +85.7% RMSE improvement |
| Network | 152 nodes, 1,855 edges, 4 communities |
| Association rules | 889 itemsets, 1,112 rules |

## Methods

- **Data Sources:** Lorcana API (card attributes), inkdecks.com (tournament decklists), TCGPlayer (market prices)
- **Feature Engineering:** TF-IDF text extraction, derived efficiency metrics, K-Means archetype clustering
- **Classification:** Random Forest, XGBoost, Logistic Regression, Decision Tree (with balanced variants)
- **Explainability:** SHAP (TreeSHAP) for both RF and XGBoost
- **Network Analysis:** Weighted co-occurrence graph, Louvain community detection, PageRank centrality
- **Association Rules:** FP-Growth with support ≥ 0.05, confidence ≥ 0.5
- **Forecasting:** Prophet (exploratory, monthly snapshots)
- **Novel Contribution:** Sleeper Card Index (SCI) — identifies cards whose competitive value exceeds market price

## Running the Notebook

1. Open `Lorcana_KDD_Pipeline.ipynb` in Google Colab
2. Run Cell 2 (Setup & Imports) to install dependencies
3. Cells are designed to run sequentially; Section 15 verifies all paper numbers

## Acknowledgments

AI writing tools (Claude, Anthropic) were used to assist with drafting, editing, and code debugging. All data collection, analysis, interpretation, and domain expertise were performed by the authors.
