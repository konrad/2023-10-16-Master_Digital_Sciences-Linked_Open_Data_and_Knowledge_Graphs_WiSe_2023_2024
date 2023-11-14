###### Anh Thu Bui
###### Matrikelnummer: 11266909

# Constructing knowledge graphs and their biomedical applications
## David N. Nicholson, Casey S. Green


### What is a Biomedical Knowledge Graph?
- *"a resource that integrates one or more expert-derived
sources of information into a graph where nodes represent
biomedical entities and edges represent relationships between
two entities"*
- Biomedical graphs serve diverse functions such as gene prioritization, drug repurposing, and identifying drug-target interactions...

<div style="text-align:center;">
  <img src="https://www.ncbi.nlm.nih.gov/pmc/articles/instance/7327409/bin/gr1.jpg" style="max-width:50%; height:auto;">
</div>

### Building biomedical knowledge graphs
- Biomedical knowledge graphs are often constructed using pre-existing databases
    - constructed by domain experts
    - manual curation
    - automated techniques (e.g. text mining)
      - rule-based extraction
      - unsupervised machine learning
      - supervised machine learning

#### Database Construction using Manual Curation
- database construction dates back to 1956
- ***Manual curation*** 
   - involves experts reading through text to detect sentences indicating relationships (relationship extraction)
  - **Downside**
     - low recall due to the high publication rate
- ***Semi-automatic methods***
  - automated systems to pre-filter text, saving time for curators 
  - **Downside** 
     - miss lesser-known relationships and struggle with ambigous sentences
- **Outlook**
  - improve semi-automatic methods to tackle ambiguity issue
  - while manual curation is precise, it results in low recall rates, emphasizing the need for a combination of automated methods and manual curation for future databases 


#### Rule-based relationship extraction
- identifying keywords and grammatical patterns to detect relationships
  - keywords established by expert knowledge or through pre-existing ontologies
  - grammatical patterns constructed via experts using parse trees (constituency parse trees and dependency parse trees)
- Grammatical patterns simplify sentences for easier extraction
     - **Downside**
          -  achieve high recall but low precision
- ***Pattern matching***
     - uses phrases or keywords to detect relationship-asserting sentences
     - phrases derived from constituency trees or dependency trees
- **Outlook**
     - rule-based relationship extraction provide a good basis
     - require significant amount of manual effort and expert knowledge
     - automation of pattern construction is a potential future direction for accelerating the process.

#### Unsupervised Machine Learning: Extracting relationships without labels
- ***Unsupervised extractors***
     - derive insights from text without the need of annotated labels by using forms of clustering or statistical calculations
- ***Co-occurence***
     - used to identify potential associations between two entities in a text
     - Examples: DISEASES and STRING databases were populated using co-occurence scoring method on PubMed abstracts
- ***Clustering***
     - extract different types of biomedical relationships simultaneously
     - **Downside**:
          - technical issues, where sentences not being captured by clustering algorithm
- **Outlook**
     - optimizing unsupervised methods by using full-text and not just abstracts
     - simplify sentences first before clustering to prevent downsides


#### Supervised Machine Learning: Extracting supervised relationships
- labeled sentences of pre-labeled publicly available datasets are used to train a classifier, which can distinguish between positive (sentences, that allude a relationship) and negative (sentences, that allude a relationship) sentences
- ***Support Vector Machines (SVM)*** are used for mapping textual input into high-dimensional space 
     - the use of ensembles of SVMs have also shown success
- Deep Learning methods using neural networks such as
     - Recurrent Neural Network (RNN)
     - Convolutional Neural Network (CNN)
     - Long-Short-Term Memory (LSTM)
     are gaining more popularity for sequential analysis and classification tasks
     - **Downside** 
          - to achieve high performance, datasets must at least contain tens of thousands of labeled data

##### Semi Supervised Learning and Weak Supervision
- techniques to construct large datasets for machine learning tasks
- semi-supervised learning
     - combines labeled and un-labeled data
     - **Downside**
          - difficult to find under-studied relationships
- weak supervision/distant supervision
     - uses noisy labels 
     - sentences are labeled based on their pair being mentioned in a database
     - **Downside**
          - generated noise is still difficult to remove

- **Outlook**
     -  combination of distant supervision with other labeling strategies provides various challenges and opportunities

### Applying knowledge graphs
- to solve biomedical challenges such as finding treatments for existing drugs or associations between diseases and molecules, knowledge graphs should be represented in low dimensional space (representational learning)
     - graphs are formed into a form of dense vectors for machine learning methods while retaining the local and/or global structure of the graph, which is relevant to the problem
- ***three methods:*** matrix factorization, translational distance models, neural network models

#### Matrix Factorization
- techniques, which use linear algebra to map high dimensional data into low dimensional space
- Isomap, Laplacian Eigenmaps or Singular Vector Decomposition (SVD)
- when applied, these methods decompose matrices into smaller rectangular matrices
- **Downside**
     - perform well on knowledge graphs with sparse numbers of edges, but struggle with more complex networks
- **Outlook**
     - adaption of these methods to handle dense networks

#### Translational Distance Models
- treat edges as linear transformations
- TransE or TransH are popular examples
- outlook: incorporation of other types of information such as edge confidence scores, textual information or edge type information 

#### Neural Networks
- commonly *word2vec-based* structures are used to project words onto low dimensional space while retaining semantic meaning
     - network architectures: skip-gram and continous bag of words (CBOW)
- ***DeepWalk, node2vec***
     - perform random walks on knowledge graph while using skip-gram models to create low dimensional representations
     - donwisde: ignore important information such as edge type or node type
          - approaches that fix that limitations have been developed, which incorporate node, edge and path types when representing knowledge graphs in a low dimensional space
- **Autoencoders**
     - autoencoders map input into a lower dimensional space and back while capturing the graph's connectivity structusre
          - **Downside**
               - high potential, but face scalability issues
- **Outlook**
     - development of hybrid models, which combine node2vec and autoencoders

### Applications

<div style="text-align:center;">
  <img src="https://www.csbj.org/cms/attachment/5c7ff096-f990-4573-a84a-5b26b9e7e9c6/gr5.jpg" >
</div>


### Multi-omic applications
- use knowledge graphs to establish connections between biological entities and diseases 
- techniques like collaborative filtering and node2vec are being used to 
     - find relations between genes and disease symptoms
     - predict protein-protein interactions
- outperform methods that do not use knowledge graphs
- **Downside**
     - manual curation of the literature, which makes validation difficult 
- **Outlook**
     - incorporation of mulitple sources of information such as compounds, anatomic locations to further improve specificity findings

### Pharmaceutical applications
- use knowledge graphs to discover new properties of drugs, how drugs are interacting with other drugs, new treatments for previously established drugs
- recommendation systems use collaborative filtering to find connections between drugs and diseases
- node2vec, autoencoders are being used to represent knowledge graphs into low dimensional space to predict drug-target connections
- **Downside**
     - recommendation systems are limited to the drugs and diseases, which are contained
     - graphs miss information about e.g. drug chemical structures, which are important for prediction performance
- **Outlook**
     - combination of neural network models and linear models
     - incorporation of entity-specific information (chemical structure etc.)


### Clinical Applications
- aim to improve patient care by analyzing electronic health records (EHR)
     - nodes represent patient, drugs and diseases
     - edges represent relationships
- translational models have been used to recommend safe drugs
- graph attention models for drug safety recommendations, patient diagnosis, likelihood for heart failure
- knowledge graphs have been showing promising results in clinical applications
- **Downside**
     - EHR data often miss important data, which is important for prediction
- **Outlook** development of algorithms to "fill that gap" or cope with the missing data


Paper: https://linkinghub.elsevier.com/retrieve/pii/S2001037020302804


