
Natalie Hußfeldt 
------


# Sparsity and Noise: Where Knowledge Graph Embeddings Fall Short

Authors: Jay Pujara, Eriq Augustine and Lise Getoor
Department of Computer Science at the University of California

Conference on Empirical Methods in Natural Language Processing in September 2017


Empirical Methods in Natural Language Processing (EMNLP): 
- leading conference in the field of natural language processing
- one of the two major high-impact conferences for natural language processing research


## Research Problem
- **Challenge:** 
   - KG embedding methods perfect in benchmark datasets 
   - but struggle with real-world KGs

- **Issues:** 
  - Real KGs have sparse entities and noisy data due to diverse sources

- **Evaluation:** 
   - evaluates popular embedding approaches on KGs with sparse entities and unreliable data
   - aiming to understand their limitations and successes in such conditions


## Importance of the Study
- **Crucial Focus:** 
  - Addressing sparsity and noise challenges is vital for KG embeddings

- **Real-World Scenario:** 
     - are innately sparse and noisy due to their diverse sources

- **Significance:** 
  - Understanding the limitations and conditions for embedding success will direct future research and enhancements in constructing knowledge graphs


## Background and Motivation

### Introduction to Sparsity and Noise

- **Sparsity Definition:** Datasets with numerous zero values, indicating incomplete information.
- **Sparsity in Knowledge Graphs:** Entities have few observable connections, creating data gaps.

  
- **Noise Definition:** Unwanted behaviors in data, lowering signal-to-noise ratio (data = signal + noise).
- **Noise in Knowledge Graphs:** Incorrect or unreliable data from flawed collection techniques or errors.


### Challenges in Knowledge Graph Embeddings

- **Sparsity Challenge:** Limited entity connections hinder learning, leading to incomplete knowledge representations.
- **Issue:** Embeddings struggle to infer accurate relationships due to sparse observations.

- **Noise Challenge:** Incorrect or irrelevant data introduces uncertainty, distorting knowledge representations.
- **Problem:** Learning algorithms can be misled, resulting in unreliable predictions.


Overcoming sparsity and noise issues is fundamental. It's about having a complete and accurate picture to base important decisions on.

## Methodology and Approach

### Knowledge Base Strategies
- **Approaches Considered:** Manual ontologies, community-driven efforts, and extraction from textual sources.
- **Key Distinction:** Highlighting differences between human-verified facts and those from textual data.

### Research Focus
- **Primary Objective:** Evaluate well-known Knowledge Graph (KG) embedding methods.
- **Data Characteristics:** Investigate KGs with sparse entities and unreliable facts, understanding the associated challenges.

### Methodology
- **Embedding Techniques:** Various methods applied to extracted KG data.
- **Data Modifications:** Benchmarks altered to create varied sparsity and reliability scenarios for training embedding models.

### Findings
- **Success Scenarios:** Identifies specific instances where embedding methods perform well.
- **Complexities Revealed:** Explores conditions leading to reduced accuracy, shedding light on KG embeddings' intricacies in sparse and unreliable data settings.

### Contributions
- **Insights:** Enhances existing embedding models, providing solutions for sparse entities and unreliable facts.
- **Recommendations:** Offers valuable suggestions for addressing challenges.
- **Future Directions:** Identifies potential research areas and improvements in knowledge graph embeddings.

### Focus of the Paper
- **Comparison:** Contrasts human-vetted facts with knowledge graphs extracted from textual data.
- **Introduced KGs:**
  - **Freebase:** Largest KG curated by humans, rich in entities and relationships.
  - **WordNet:** NLP-focused, with limited relationships.
  - **NELL:** Dynamically extracted from web text, offering diverse data.
- **Benchmark Datasets:**
  - **NELL:** Largest dataset with 1 million facts.
  - **FB15K:** Sampled subset around 15,000 entities.
  - **WN18:** Limited to 18 specific relations.
  - **NELL165:** Comprehensive, providing comparative insights.


|   Dataset   |  Triples  |    E    |   R   |  EE  |  RE  |  ED  |   RD   | prec |
|:-----------:|:---------:|:------:|:-----:|:---:|:---:|:---:|:------:|:----:|
|  Freebase   |    1B     |  124M  | 15K   |  14 | 3.2 |  16 |   68k  |   1  |
|  WordNet    |   380K    |  116K  |  27   |  21 | 2.3 |   7 |   21k  |   1  |
|  NELL1000   |    92M    |  4.8M  | 435   |  21 | 4.9 |  19 |  210k  | 0.45 |
|   FB15K     |   592K    |  15K   | 1.3K  |  16 | 5.1 |  79 |   440  |   1  |
|    WN18     |   151K    |   40K  |  18   |  19 | 2.1 |   7 |  8.4k  |   1  |
|   NELL165   |    1M     |  820K  |  221  |  25 | 1.5 |   3 |  4.7k  | 0.35 |


- each row presents a different dataset
- Columns:
  - Triples: Number of individual facts in the knowledge graph.
  - kE: Unique entities in the knowledge graph.
  - k: Represents a specific attribute of the dataset.
  - kRk: Unique relations in the knowledge graph.
  - EE: Measure of entropy.
  -  RE: Another measure of entropy.
  - ED: Measure of entity density.
  - RD: Measure of relational density.
  - prec: Precision of triples.   

## Sparsity Measurement

### Factual Variation
- **KG Diversity:** Entities and relations vary in factual information across KGs.
- **Sparsity Metric:** Information density, calculated as average triples per entity or relation.
- **Formal Metrics:**
  - **RD (Relational Density):** Measure of relationships' density.
  - **ED (Entity Density):** Measure of entities' density.
  
### Dataset Comparisons
- **Entity Density (ED):** Most datasets exhibit similar entity density.
- **Exceptions:**
  - **FB15K:** High entity density.
  - **NELL165:** Low entity density.
- **Relational Density (RD):**
  - **NELL1000:** Highest due to focus on a specific set of relations.
  - **FB15K:** Lower RD, higher ED influenced by sampling approach.

## Reliability in Embedding Approaches

### Importance of Reliable Facts
- **Embedding Accuracy:** Relies on accurate and reliable facts.
- **Human-Curated KGs:** Ensure high precision due to meticulous oversight.

### Challenges with Extracted KGs
- **Noisier Data:** Extracted KGs contain erroneous relationships.
- **Evaluation Challenges:**
  - Small, manually-labeled sets used for precision estimation.
  
### NELL Evaluation Example
- **Precision Evaluation:** NELL facts assessed using 11K annotations.
- **Results:**
  - **Confident Extractions:** Precision ranged from 0.75-0.85.
  - **Broader Extractions:** Precision varied from 0.35-0.45.

- **Evaluation Methods:**
  - Investigated embedding performance using sparse and unreliable data.
  - Examined four embedding techniques: TransE, TransH, HolE, and STransE.
  - These methods employ advanced learning methods for entity and relation representation.

- **Learning Process:**
  - Used public implementations for learning embeddings from the chosen methods.
  - Conducted four experiments to evaluate embedding methods' effectiveness.

- **Experiment Categories:**
  - **First Set:** Tested embeddings on the NELL165 KG dataset.
  - **Second Set:** Altered FB15K benchmark to analyze sparsity's impact on embedding quality.
  - **Third Set:** Reduced FB15K's reliability to observe performance decline.
  - **Final Experiments:** Explored sparsity and reliability tradeoff, starting with a sparse training set and gradually adding unreliable triples at varying noise levels.

<div style="display: flex;">
    <img src="Table2.png" style="width: 50%;" alt="Table2">
    <img src="Fig1.png" style="width: 50%;" alt="Fig1">
</div>

<div style="display: flex;">
    <img src="Fig2.png" style="width: 50%;" alt="Table2">
    <img src="Fig3.png" style="width: 50%;" alt="Fig1">
</div>


## Results and Findings:

- **Focus on NELL165 Dataset:**
  - NELL165 is sparse with fewer facts per relation/entity compared to FB15K benchmarks.
  - Candidate facts in NELL165 have lower precision than benchmark datasets.

- **Evaluation Methods:**
  - Tested four advanced embedding techniques under challenging conditions.
  - Used 4.5K manually-labeled facts for evaluation.
  - Metrics: Area under the precision-recall curve (AUPRC) and F1 score.

- **Baseline and Comparison:**
  - Compared embedding methods against baseline methods and a probabilistic model.
  - Embedding approaches performed poorly, lagging behind baseline methods and significantly behind the probabilistic model.

### Objective of Subsequent Experiments:

- **Impact of Sparsity:**
  - Investigated the influence of dataset sparsity on embedding quality.
  - Used two methods to evaluate sparsity: Sparse (randomly removed triples) and Stable (removed specific relation triples).
  - Performance consistently decreased as the training set size reduced, with sparse treatment leading to faster deterioration than stable treatment.

- **Unreliable Candidate Facts:**
  - Explored the impact of unreliable facts on embedding techniques.
  - Introduced noise by corrupting existing triples in the dataset.
  - Removing training data was more effective than providing incorrect data. The difference in performance between sparse (removed) and corrupt (incorrect) data remained relatively stable across all embedding methods.

- **Sensitivity to Data Unreliability:**
  - Investigated the impact of unreliable candidate facts on embeddings.
  - Introduced noise by "corrupting" triples, replacing true entities or relations with replacements.
  - Removing training data performed better than providing incorrect data for all methods. The performance gap between sparse and corrupt remained consistent across embeddings.

- **Tradeoff Between Sparsity and Noise:**
  - Real-world KG construction involves balancing sparsity and noise.
  - Adding unreliable facts might not always benefit embeddings.
  - Removing some triples and adding unreliable ones at varying noise levels impacted embedding performance. Low noise led to steady improvement, while high noise caused plateauing or reduced performance.
  - Surprising finding: Even with 90% noise, embeddings showed a small improvement, suggesting a large, unreliable corpus might be better than an extremely sparse, high-quality one.


## Conclusion:

- **Sensitivity to Data Quality:**
  - KG embeddings are highly affected by sparse and unreliable data, particularly in KGs extracted from text sources.

- **Future Research Directions:**
  - **Revising Assumptions:** Reconsider closed-world assumptions in KG embeddings to improve their robustness.
  - **Integration with Probabilistic Models:** Explore integration of embeddings with collective probabilistic models for enhanced accuracy.
  - **Optimizing Embeddings:** Focus on optimizing embeddings using confidence information derived from knowledge extraction systems for better results.


[https://aclanthology.org/D17-1184.pdf](https://aclanthology.org/D17-1184.pdf)