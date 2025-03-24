# Boost GNN Performance
This project aims to evaluate different Graph Neural Network (GNN) architectures on various datasets while proposing innovative data augmentation techniques to enhance their performance. 
GNNs are a powerful tool for learning on graph-structured data, and this project explores the impact of data augmentation strategies on their performance across different tasks, including node classification, link prediction, and graph classification.

## Key Objectives

- **Evaluate GNN Architectures**: The project assesses the performance of several GNN architectures, including:
  - **GCN (Graph Convolutional Network)**
  - **GraphSAGE (Graph Sample and Aggregation)**
  - **GAT (Graph Attention Network)**

- **Data Augmentation Techniques**: I propose and implement topology-based data augmentation strategies to improve the learning capabilities of GNNs. These features are computed using `graph-tool` and include:
  - **In and Out Degree**: Measures of the number of edges entering and leaving a node.
  - **Local Clustering Coefficient**: A measure of the degree to which nodes in a graph tend to cluster together.
  - **Average Neighbor Degree**: The average degree of a node's neighbors, both incoming and outgoing.
  - **Centrality Measures**: Including Pagerank, Eigenvector, HITS (authority and hub), and Katz centralities.
  - **K-core Decomposition**: The k-core is a maximal set of vertices such that its induced subgraph only contains vertices with degree larger than or equal to k.

## Datasets

The project utilizes datasets from the Open Graph Benchmark (OGB), which are designed to facilitate the evaluation of GNNs on realistic graph datasets. The datasets include:

- **Node Classification**: Predicting the label of a node based on its features and the graph structure.
  - **ogbn-arxiv**: A citation network of arXiv papers.
  - **ogbn-proteins**: Protein-protein association networks.

- **Link Prediction**: Predicting the existence of an edge between two nodes.
  - **ogbl-ddi**: Drug-drug interaction networks.
  - **ogbl-collab**: A collaboration network.

- **Graph Classification**: Predicting the label of an entire graph.
  - **ogbg-molhiv**: Molecular property prediction.

## Results

The project includes a comprehensive evaluation of the proposed data augmentation techniques and GNN architectures across the aforementioned datasets. Below is a summary of the performance metrics:

| Dataset  | Task Type                 | Metric    |
|----------|---------------------------|-----------|
| arxiv    | Multi-class classification | Accuracy  |
| proteins | Binary classification      | ROC-AUC   |
| ddi      | Link prediction            | Hits@20   |
| collab   | Link prediction            | Hits@50   |
| molhiv   | Binary classification      | ROC-AUC   |


| Dataset       | Model      | Topology | Train | Val  | Test |
|---------------|------------|----------|-------|------|------|
| ogbg-molhiv   | GAT        | False    | 0.754 | 0.723| 0.740|
|               |            | True     | 0.746 | 0.701| 0.718|
|               | GCN        | False    | 0.738 | 0.727| 0.757|
|               |            | True     | 0.732 | 0.735| 0.733|
|               | GraphSAGE  | False    | 0.701 | 0.686| 0.704|
|               |            | True     | 0.722 | 0.697| 0.733|
| ogbl-collab   | GAT        | False    | 0.094 | 0.276| 0.259|
|               |            | True     | 0.137 | 0.422| 0.359|
|               | GCN        | False    | 0.143 | 0.304| 0.232|
|               |            | True     | 0.137 | 0.309| 0.267|
|               | GraphSAGE  | False    | 0.095 | 0.361| 0.291|
|               |            | True     | 0.136 | 0.359| 0.311|
| ogbl-ddi      | GAT        | False    | 0.000 | 0.000| 0.000|
|               |            | True     | 0.001 | 0.167| 0.124|
|               | GCN        | False    | 0.000 | 0.000| 0.000|
|               |            | True     | 0.001 | 0.041| 0.028|
|               | GraphSAGE  | False    | 0.000 | 0.000| 0.000|
|               |            | True     | 0.001 | 0.155| 0.169|
| ogbn-arxiv    | GAT        | False    | 0.581 | 0.625| 0.569|
|               |            | True     | 0.587 | 0.633| 0.587|
|               | GCN        | False    | 0.649 | 0.631| 0.571|
|               |            | True     | 0.650 | 0.644| 0.592|
|               | GraphSAGE  | False    | 0.669 | 0.631| 0.569|
|               |            | True     | 0.670 | 0.643| 0.580|
| ogbn-proteins | GAT        | False    | 0.499 | 0.500| 0.500|
|               |            | True     | 0.727 | 0.712| 0.652|
|               | GCN        | False    | 0.545 | 0.479| 0.449|
|               |            | True     | 0.749 | 0.687| 0.647|
|               | GraphSAGE  | False    | 0.578 | 0.500| 0.500|
|               |            | True     | 0.788 | 0.771| 0.721|
