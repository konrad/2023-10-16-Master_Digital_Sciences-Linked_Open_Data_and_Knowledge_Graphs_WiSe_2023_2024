# Task‑driven knowledge graph filtering improves prioritizing drugs for repurposing
- Authors: Florin Ratajczak, Mitchell Joblin, Martin Ringsquandl and Marcel Hildebrandt

2023-11-13, Andreas Kruff

## TOC

- Introduction
- Paper Approach & Problem Statement
- Underlying datasets
- Paper Approach: Preprocessing
- Paper Approach: Task-driven metapath filtering
- Results & Evaluation
- Conclusion

## Introduction

### Example: Aspirin

Development of usecases for Aspirin can be divided into 4 phases

Phase 1 (1951-1960)
- Usecase
    - anti-inflammatory
    - antipyretic
Phase 2 (1961-1990)
- Usecase
    - antiplatelet effect
    - mechanism of inhibition of prostaglandin synthesis
    - acetylation of the cyclo-oxygenase enzyme
    - reduce the incidence of colorectal cancer
Phase 3 (1961-1990)
- Usecase
    - repurposing for cardiovascular diseases
Phase 4 (2001-2018)
- repurposing for other diseases published in
    - Cancer Management and Research
    - Drugs & Aging
    - World Neurosurgery

![Aspirin_Development](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7327595/bin/medinform_v8i6e16739_fig1.jpg)


### Historical Development of Drug Repurposing:

- Identification through casual observations or clinical use

New developments in Computer Science like Knowledge Graphs allow for

- Computational approaches recently allowed for systematic approaches

### Benefits of Drug Repurposing

- Cost of discovering new drugs steadily increases
- Shortening the timespan for Drug development
- Better scaling regarding the number of different drugs and diseases

## General Paper Approach:

- Preprocessing/Filtering of Knowledge Graph
- Training of Knowledge Graph Embeddings
- Identifying undiscovered triples with high probability
    - known as link prediction/ KG completion

### Main Goal:

Identifying triples of type (Compound, treats, Disease)

=> Prioritization compound-disease pairings for expert revision and clinical trials

## Problem Statement:

- Knowledge Graph Embeddings are optimizing predictions for all relations in the graph
- Only one specific relation of interest in the graph (Compound, treats, Disease)
    - typically an underrepresented relation in the graph

Problem: Using all relations of the KGE model might lead to underfitting the data on the relation of relevance

Solution:  Tailoring the KG to a specific task in order to improve model performance

## Used Knowlegde Graphs:

- Hetionet
- DRKG - Drug Repurposing Knowledge Graph
    - Including:
        - Drugbank
        - IntAct
        - GNBR
        - STRING
        - DGIdb
        - Hetionet




## Preprocessing Steps

1.  Removal of irrelevant relations (Compound -> Disease)
    - Including relations:
        - GNBR:
            - Pa (alleviates, reduces)
            - Sa (side effect, adverse event)
            - J (role in disease pathogenesis)
            - Mp (biomarkers of disease progression)
        - Hetionet:
            - palliates
2. Removal of contradictory triples  from Hetionet
3. Unifying non-ambiguous relations between Compound and Disease
    - Including relations:
     - GNBR:
       - C (inhibits cell growth)
       - Pr (prevents, suppresses)

4. Adding inverse relations to the KG

## Paper Approach: Task-driven metapath filtering

1. Defining desired metapaths m1, m2, ... , ml ∈ M with given metapaths m = (t1, t2, ... , tn−1, tn) of length n
2. Start at any entity e1 of type t1
    - Due to the usecase t1needs to be Compound
3. Sampling all entities of the type t2 in the neighbourhood N(e1) of e1
    - Example: Neighbourhood N(e1) = (disease, SideEffect, Gene) or Neighbourhood N(e1) = (stomach cancer, Agranulocytosis, LBR)
4. Selection one node at random
5. Sampling all entities of the type t3 in the neighbourhood N(e2) of e2

=> Process continues until one out of two Stop Conditions is met

### Stop Condition 1:

Reaching entity en of type tn

=> Entity type  tn is Disease

### Stop Condition 2:

Reaching entity ei that has no entity ei+1 of the required type type tn


## Temporary outcome:

Set of complete walks Wcomplete

=> Walker reached an entity en of type tn

Set of stopped walks Wstopped

=>  Walker stopped at an entity ei that has no required next node in N(ei)

Problem:

Procedure can lead to small disconnected graphs in Set Wcomplete

Solution:

Concatenating walks of Set Wcomplete with matching start and end entities

=> Similar to the dominos game

Concatentation Procedure:
Concatenating procedure repeated until concatenated walk reaches predefined length
Adding concatenated walks in Wconcatenateduntil predefined number of concatenated walks is reached

## Parameters used:

- Traversing metapaths in both directions
    - Starting from Compounds & Disease
- Number of Random Walk starts per Entity (Compound/Disease)
    - 1000 per metapath
- Length of concatenated walks: 100 entities
- Number of concatenated walks per metapath: 5000

## Results & Evaluation

### Result: KG Filtering

Hetionet:

- Reduction of up to 60 % of entites
- Reduction of 32 % of triples
- Increasing average degree by 65 %

- Increasing the relative amount of compounds by 127,9 %
- Increasing the relative amount of diseases by 133,2 %

DRKG:

- Reduction of 26 % of entites
- Reduction of 7 % of triples
- Increasing average degree by 26 %

- Increasing the relative amount of compounds by 13,1 %
- Increasing the relative amount of diseases by 30,7 %

## Evaluation

- Evaluating link prediction performance by triples of type

- Compound -> treats -> Disease

- Generating negative examples by permutating the tail
entity only with other Diseases

- Evaluating of the prediction performance by Mean Reciprocal Rank (MRR)

Hetionet:

- Increase of MRR by up to 40.8 % for ComplEx model

DRKG:

- Increase of MRR by up to 14.2 % for TransE model

## Conclusion

- Results demonstrate that the removed information is in fact counterproductive to learning embeddings for the specific task
    - up to 60% of a KG can be removed by this filtering method while simultaneously improving the performance in the task by up to 40%

=> Metapath-based approach is adaptable for tailoring KG’s for specific usecases


## Sources:

Li, X., Rousseau, J. F., Ding, Y., Song, M., & Lu, W. (2020). Understanding Drug Repurposing From the Perspective of Biomedical Entities and Their Evolution: Bibliographic Research Using Aspirin. JMIR medical informatics, 8(6), e16739. https://doi.org/10.2196/16739

Ratajczak, F., Joblin, M., Ringsquandl, M. et al. Task-driven knowledge graph filtering improves prioritizing drugs for repurposing. BMC Bioinformatics 23, 84 (2022). https://doi.org/10.1186/s12859-022-04608-y