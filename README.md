# Social Network Analysis of the European Football Transfer Market

> 🇪🇸 [Versión en español](README.es.md)

Social Media Mining project — Data Science MSc, University of Granada.

This project models the European football transfer market as a directed, weighted network and analyses it using social network analysis techniques in **Gephi**: global metrics, actor centrality, and community detection.

## The network

Nodes are clubs; a directed, weighted edge from club A to club B means A sold or loaned players to B, weighted by the number of players. The data covers transfers across the **seven main European leagues** (LaLiga, Ligue 1, Liga Portugal, Serie A, Premier League, Bundesliga, Eredivisie) over five seasons (2017/18–2021/22). Clubs outside these leagues are grouped into regional nodes (e.g. *free agents*, *UK*, *South America*).

The network has **309 nodes and 3,488 edges**, forming a single giant component that contains the entire graph.

## What was analysed

**1. Global structure.** The network is very sparse (density 0.037) but exhibits a clear small-world effect: average distance is just 2.86 with a diameter of 6, so any two clubs are linked through fewer than three intermediaries on average. The degree distribution is heavily right-skewed (power-law-like), revealing a few dominant hubs among many low-degree clubs.

**2. Actor centrality** (four measures):
- **Degree** — dominated by regional/free-agent nodes; among individual clubs, **AS Monaco** leads with the most balanced in/out profile, acting as the market's main mover.
- **Betweenness** — dominated by Portuguese clubs (Benfica, Porto, Sporting), confirming their role as *bridges* funnelling talent (notably from South America) toward the elite leagues.
- **Closeness** — several nodes reach the maximum, evidence of a strongly connected market with no isolated islands.
- **Eigenvector** — AS Roma, Fiorentina, Genoa, Sevilla and Monaco rank top, identifying a closed circle of high-prestige clubs that trade mostly among themselves.

**3. Community detection.** Both **Louvain** and **Leiden** were run across resolution values, assessing modularity robustness and semantic coherence. The two methods agree on a large Portugal–Netherlands–South America bridge community. They differ on England and Germany: Louvain keeps each league as its own community, while Leiden merges them. The **Louvain partition at resolution 0.9 (6 communities)** was selected as the final one, as it best balances structural quality with interpretability — each major league maps cleanly to a community.

## Repository structure

```
.
├── README.md          # This file (English)
├── README.es.md       # Spanish version
├── practica.gephi     # Gephi project (network, layout, metrics, partitions)
├── data/
│   ├── nodes.csv      # Node list (clubs and regional labels)
│   └── edges.csv      # Edge list (directed, weighted transfers)
└── docs/
    └── informe.pdf    # Full report with figures and interpretation
```

## Tools & methods

[Gephi](https://gephi.org/) — Force Atlas 2 layout, degree/betweenness/closeness/eigenvector centrality, and the Louvain and Leiden community-detection algorithms.

## Author

Pablo González Gómez — [LinkedIn](https://www.linkedin.com/in/pablo-gonzalez-gomez)
