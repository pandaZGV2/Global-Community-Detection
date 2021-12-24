# Global Community Detection Algorithms

The jupyter notebook implements the global community detection algorithms of [this paper](http://leonidzhukov.net/hse/2011/seminar/papers/Inferring-WSDM.pdf).

## The Algorithm

We define betweeness centrality as follows:

The betweenness centrality for an edge is the number of shortest paths that contain that edge divided by the number of all possible shortest paths.

The algorithm proceed by iteratively remocing edges with the highest betweenness centrality until the graph is partitioned. 

The intuition behind this algorithm is simple. If we assume that the social network is divided into densely connected communities, the betweenness centrality metric looks for links that bridge communities. Since communities are, by definition, more dense than the graph as a whole, these bridging links will naturally have a higher betweenness centrality. Once they are removed from the graph, the underlying community structure emerges.

## The Dataset

We use the books and the character relations of the Song of Ice and Fire series as our dataset. We first form edges for each character relation in the book. Then we aggregate the edges and assign weights to them. We then sort them in decreasing order of edges and reindex them. We then precompute the betweenness centrality for each edge.

We then apply the algorithm, removing 5, 6, 7, 8, and 9 edges. We observe that we can start to see the graph being partioned into communities.

## Requirements

- Matplotlib
- Networkx
- Numpy
- Pandas