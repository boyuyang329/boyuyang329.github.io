---
layout: page
title: Pathway-informed proteomics model
description: Proteins as nodes, pathways as hyperedges, disease as the label
importance: 2
---

I built disease classifiers on plasma proteomics data in which each protein is a node and each Gene Ontology biological process pathway is a hyperedge connecting the proteins in it. Protein levels are combined with protein language model (ESM-2) embeddings, information is passed between proteins and pathways, and each pathway produces a score that feeds the final prediction.

On a public ALS plasma proteomics dataset (Olink, about 2,900 proteins), the model reached a test AUC of about 0.91 and produced a pathway ranking consistent with known ALS biology, including complement activation, proteostasis, and muscle and axonal pathways.

**What I learned**

- **Model capacity has to match the data.** With fewer than 500 training samples, adding high-dimensional protein embeddings first made the model worse. Pruning the graph to a disease-focused set of pathways turned the same features from the worst configuration into the best one and cut the variance across random seeds in half.
- **Ablations matter more than headline numbers.** Replacing real pathways with random groupings changed accuracy only slightly, so the main value of the pathway structure here is interpretability rather than prediction.
- **Attention weights are not explanations.** Attention scores were nearly uniform across pathways, so I used a direct discriminative analysis of each pathway instead.
