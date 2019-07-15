# Girvan-Newman Algorithm - Community Detection
This is an implementation exercise of the [Girvan-Newman algorithm](https://en.wikipedia.org/wiki/Girvan%E2%80%93Newman_algorithm). The goal is to find the optimal community clustering of a Yelp user network using the [Yelp dataset](https://www.yelp.com/dataset/challenge).

The general pipeline is as followed.
1. First, we have an input file (inputs/sample_data.csv) which contains a list of Yelp user and business pairs. The pairs represent each business review given by their customers.
2. We construct a graph of user network. Each pair of user is connected if and only if the number of times both users rated the same businesses exceeds the threshold value from the input.
3. We use this graph as the initial graph of the network and calculate betweenness value of the graph and save the output in a file.
4. Calculate [modularity](https://www.cs.cmu.edu/~ckingsf/bioinfo-lectures/modularity.pdf) of the clustering.
5. Remove edge(s) with highest betweenness, re-cluster, and calculate modularity once again.
6. Repeat this until there are no more edges left to remove and keep the community clustering with the highest modularity value.
7. Output the optimal clustering to a text file.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Python >= 3.6
Spark >= 2.3.3

### Installation

Download the project by cloning the repository.

```
git clone https://github.com/hsuanhauliu/girvan-newman-community-detection.git
```

### Usage

Follow the command below to run the program.

```
python3 main.py [threshold_value] [input_file] [betweenness_output_file] [community_output_file]
```

Example:
```
python3 main.py 7 inputs/sample_data.csv betweenness.txt community.txt
```
