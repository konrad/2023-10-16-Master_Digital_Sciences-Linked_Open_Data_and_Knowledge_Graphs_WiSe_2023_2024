# Knowledge Graph Embeddings


<img src="https://b2316719.smushcdn.com/2316719/wp-content/uploads/2022/06/image-1-1024x300.jpg?lossy=1&strip=1&webp=1" title="Knowledge Graph Embedding">

*Goal of a graph embedding. Image source: https://www.graphable.ai/blog/knowledge-graph-embeddings/* 


* used in context of machine learning 
* goal: 
    * simplify the structure of the triples of Knowledge Graph elements for different machine learning tasks
    * the models learn to represent the elements of the Knowledge Graph while preserving the semantic meaning (*entities & relations*)

## Usage and Area of application
- **Prediction tasks & Semantic similarity computations:** entity or triple classification, entity recognition, Link prediction
    - Completion of knowledge graphs (probabilistically inferring the missing arcs from the existing graph structure)
    - Chatbot - Answering questions
    - improving search engines (Google's Knowledge Graph)   
    - recommender systems (Product recommendation for e-commerce)

## How does the embedding work?

-> different approaches of models

###**Main categories of algorithms:**

#####1. random walk-based approach

**DeepWalk & node2vec**
* inspired by Word Embeddings (`Word2Vec`) - semantic of the words
* Representation of a Knowledge Graph element in a continuous vector space
* generates a series of nodes from a random walk of length k starting at a given node v and measures similarity via the most frequently visited nodes.
* these random walks are seen as a series of co-occurring elements, this collected data can easily be implemented in a skip-gram model
* similar nodes are close to each other in the vector space  


![Alt text](https://b2316719.smushcdn.com/2316719/wp-content/uploads/2022/06/image-8-768x257.jpg?lossy=1&strip=1&webp=1)
*Embedding with DeepWalk. Image source: https://www.graphable.ai/blog/knowledge-graph-embeddings/*



#####2. translational distance models
* based on a scoring function
* measure distances in vector space to determine the plausibility of a triple
* `TransE` - most used translational distance model
    * represents the entities and the relations as vectors in the same semantic space R of dimension d
    * relations are interpreted as a translation vector
        - the embedded entities subject and object can be connected by this translation vector (predicate) - short distance
        - vector computation: `h + r ≈ t` (head + relation ≈ tail)
    * goal: minimizing the scoring function
* there are some extensions of this method for improvements:
    * `TransH` - every relation is represented as a hyperplane
    * `TansR` - the relation vector space is separated from the entity space - more than 1:1-relations are possible

<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*2Do_skj8NxPkKzIu0sc8oQ.png">

*Comparison of the different models. Image source: https://towardsdatascience.com/knowledge-graph-embeddings-101-2cc1ca5db44f*

#####3. semantic matching models
* similarity-based scoring function 
* measures the plausibility of a triple by matching the semantics of the latent representations of entities and relations
* `RESCAL` - bilinear model
    * capture of latent semantics by association of entities with vectors
    * relations are presented as a matrix
    * the matrix models pairwise interactions between latent factors (entities)
    * score of a triple is defined by a bi-linear scoring function
    * goal: minimizing the scoring function through tensor factorization based on optimization technique.

<img src="https://data.dgl.ai/asset/image/ke/rescal.png"  width="20%" height="20%" title="entities and their relations as multi-dimensional tensor">

*The entities and their relations as multi-dimensional tensor. Image source: https://dglke.dgl.ai/doc/kg.html*


## Timeline
![Alt text](https://miro.medium.com/v2/resize:fit:640/format:webp/1*bdI4PTL0VSTGXyPvdVpuBA.png) 
*Timeline of some knowledge Graph Embedding Models. Image source: https://en.wikipedia.org/wiki/Knowledge_graph_embedding* 

## sources
https://towardsdatascience.com/knowledge-graph-embeddings-101-2cc1ca5db44f
https://dglke.dgl.ai/doc/kg.html
https://www.graphable.ai/blog/knowledge-graph-embeddings/
https://ahrefs.com/blog/google-knowledge-graph/
https://en.wikipedia.org/wiki/Knowledge_graph_embedding 

