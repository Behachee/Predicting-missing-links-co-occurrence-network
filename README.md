# Predicting Missing Links In An Actor Co-occurrence Network

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Data](#data)
- [Models](#models)
- [Feature Engineering](#feature-engineering)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Introduction

This project focuses on link prediction methods applied to a graph representation of our dataset. The dataset at hand is composed of nodes that represent actors, and edges that indicate a case of co-occurrence between two actors. We define co-occurrence as the occurrence of the name of both actors on a wikipedia page, which stands as a proxy for their joint participation in a movie, or other type of relationship (level of fame, personal relationship…)

Given a pair of actors, we aim to predict if there is a co-occurrence between these two actors, classified with a label 1, or 0 if there isn’t any relationship. In order to determine the existence of a relationship, we are also given a dataset ‘node_information’ which represents information about each actor (each node) from its own wikipedia page, with keywords processed and encoded in 932 features. Our training set consists of 10,496 node pairs, with the associated label. Our test set consists of 3498 node pairs, with certain edges between the pairs that have been removed from the original graph. We conduct feature engineering and feature selection and utilize various models to classify the missing links in the test set. 


## Installation

To get started with this project, follow these steps:

1. Clone the repository:
```bash
git clone https://github.com/Behachee/Predicting-missing-links-co-occurrence-network.git
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```


## Usage

To use the code in this repository, follow these steps:

1. Navigate to the project directory:
```bash
cd Predicting-missing-links-co-occurrence-network
```

2. Run the desired scripts or notebooks for training models, evaluating results, etc.

## Data

The data used in this project is located in the `data` directory. It includes sample datasets for training and testing the models.
As well as `train_set_final` and `test_set_final`, the two files containing the training and test data augmented with feature engineering.

## Models

This repository contains implementations of the following models:


- Random Prediction
- Logistic Regression (Baseline Model)
- XGBoost
- Graph Neural Network
- Random Forest
- Node2Vec
- SVM
- CatBoost

Each model is contained in a separate notebook within the `models` directory.

## Feature Engineering

Feature engineering is a crucial aspect of building effective machine learning models. In this project, we perform the following feature engineering steps:

- **Degree**: The degree of a node in a network represents the number of connections it has to other nodes. In simple terms, it measures how connected a node is within the network.

- **Centrality**: Centrality measures the importance of a node within a network. There are different types of centrality measures, such as degree centrality, betweenness centrality, and closeness centrality, each capturing different aspects of node importance.

- **Community**: In the context of network analysis, a community refers to a group of nodes that are densely connected to each other but sparsely connected to nodes outside the group. Community detection algorithms aim to identify these groups within a network.

- **Jaccard Similarity**: Jaccard similarity measures the similarity between two sets by comparing the intersection and union of the sets. In the context of networks, it quantifies the similarity between two nodes based on the common neighbors they share.

- **Salton Similarity**: Salton similarity is a similarity measure in network analysis that calculates the cosine of the angle between the vectors representing two nodes in a network.

- **Sorenson Similarity**: Sorenson similarity, also known as Sørensen–Dice coefficient, is a similarity measure commonly used in network analysis. It is calculated as twice the number of common neighbors divided by the sum of the degrees of the two nodes being compared.

- **Hub Promoted Similarity**: Hub Promoted Similarity is a similarity measure that gives more weight to common neighbors that are hubs in the network. It considers the importance of shared neighbors in determining similarity.

- **Leicht-Holme-Newman Similarity**: Leicht-Holme-Newman similarity is a measure of similarity between two nodes in a network that accounts for the degree distribution of the network. It considers the likelihood of observing the shared neighbors by chance.

- **Adamic-Adar Similarity**: Adamic-Adar similarity is a measure of similarity between two nodes in a network that assigns higher weights to common neighbors with lower degrees. It penalizes the contribution of common neighbors with high degrees.

- **Resource Allocation Similarity**: Resource Allocation similarity is a measure of similarity between two nodes in a network that allocates resources (such as edges or connections) based on the common neighbors shared by the nodes.

- **Common Neighbors**: Common neighbors refer to the nodes that are directly connected to both of the nodes being considered. In other words, they are the nodes that share an edge with both target nodes in a network.

- **Cosine similarity**: Measures the cosine of the angle between two nodes’ features vectors used to determine how similar they are. It ranges from -1 (exactly opposite) to 1 (exactly the same), with 0 indicating orthogonality (no similarity).

- **Preferential Attachment**: Suggests that the probability that a new link connects to a node is proportional to the number of connections that node already has.

- **Same Community**: Denotes if the two nodes belong to the same community

- **Node_info Source**: This refers to information associated with the source node in a network

- **Node_info Target**: Similarly, this refers to information associated with the target node in a network.


The code for feature engineering can be found in the `Feature_Engineering.ipynb` file.

## Results

Prediction of different model can be found in the `submission` directory named `model_name_prediction.csv`

| Model             | Accuracy | AUC Score |
|-------------------|----------|-----------|
| Logistic Regression | 70.5%   |   0.749   |
| SVM               |    -     |     -     |
| Random Forest     |  72.9%   |   0.778   |
| CatBoost          |  71.9%   |   0.770   |
| XGBoost           |  82.3%   |   0.84   |
| GNN               |  60.2%   |   0.663   |

## Contributing

Contributions to this project are welcome. If you have ideas for improvements or new features, feel free to open an issue or submit a pull request.


## Contact

For questions or feedback regarding this project, please contact Théo Belen-Halimi, Victor De Chaisemartin, Joseph Panijel, Théo Sioufi or theo.belen-halimi@student-cs.fr.

# Reference et Lien Utile
- Hou, L., & Liu, K. (2017). [Common neighbour structure and similarity intensity in complex networks](https://doi.org/10.1016/j.physleta.2017.08.050). *Physics Letters A, 381*(39), 3377-3383.

- Nasuha Daud, N., Ab Hamid, S. H., Saadoon, M., Sahran, F., & Anuar, N. B. (2020). [Applications of link prediction in social networks: A review](https://doi.org/10.1016/j.jnca.2020.102716). *Journal of Network and Computer Applications, 166*, 102716.

- Zhang, Z., Cui, L., & Wu, J. (2021). [Exploring an edge convolution and normalization based approach for link prediction in complex networks](https://doi.org/10.1016/j.jnca.2021.103113). *Journal of Network and Computer Applications, 189*, 103113.

