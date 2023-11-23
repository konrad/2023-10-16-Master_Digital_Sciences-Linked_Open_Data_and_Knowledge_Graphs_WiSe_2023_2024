Anh Thu Bui , Natalie Hußfeldt 
---------


# The Clinical Knowledge Graph


## Challenges in Precision Medicine/ Understanding Diseases: 


- Precision medicine needs to combine different types of data like 
  - clinical records
  - lab results
  - genetics
  - electronic health records (EHRs)

- Data is spread across various sources and is often complex 
  - making it hard to get a clear picture.

- Valuable scientific information is buried in many unorganized research papers
  - making it difficult to extract useful data

- Genetics alone can't tell us everything about diseases
  - need to look at various aspects, including proteins (proteomics)

  - Proteomics, a study of proteins, provides deep insights into biological processes
     - advanced technology helps analyze complex samples
     - but understanding the results is still a challenge


## The Need for Clinical Knowledge Graph (CKG):


### Challenges in Current Proteomics Workflows:

- Handling increasing data volumes
- Time-consuming result interpretation studies


### What CKG Does:

- Integrates millions of protein-related data pieces
- Combines information from diverse biological areas and medical databases

### Importance of CKG:

- helps researchers ask important questions about diseases and treatments
- Facilitates data analysis, visual representations, and faster information retrieval
- Enhances research reliability
- Enables efficient repetition of past experiments and discovery of new insights

### CKG Solution:

- Represents connected data in a knowledge graph
- Allows quick adaptation of complex data through relationships
- Utilizes inherent inter-connectivity for network analysis
- Discovers hidden patterns and infers new knowledge


## Clinical Knowledge Graph (CKG) Overview:

### Platform Details:

- **Open Source:** More than 16 million nodes, 220 million relationships
- **Database:** Neo4j Community Edition (Scalable native graph database)
- **Query Language:** Cypher (Neo4j)
- built on Python libraries, which makes platform
  - reliable
  - maintainable
  - continuously improving
- interactive Jupyter Notebook-based exploration and visualization
- **Ontologies:** Defines nodes and relationships using biomedical ontologies
- **Integration:** Concepts integrated directly into the knowledge graph
- incorporates latest statistical and machine learning algorithms
- accelerates analysis and interpretation of typical proteomics workflows
- enables repeatable, reproducible and transparent analysis
- provides clinically meaningful queries 



### Data Sources:

-    **Experimental Data:** Relevant experimental data
-    **Biomedical Databases:** Integration of 26 biomedical databases
-    **Scientific Texts:** Information extracted from 7 million+ articles
-    **Redundancy:** Ensures robustness by assessing overlap between databases

### Relationships:

- **Publication Nodes:** Over 50 million relationships
- **Connection:** Scientific papers linked to proteins, drugs, diseases, etc.
- **Extraction:** Extracted from text mining processes
- **Biomedical Knowledge:** Captures extensive biomedical insights

### Example databases: 

| **Database** | **Website**                                       	| **Content**                                              	|
|-------------|-------------------------------------------------------|--------------------------------------------------------------|
| UniProt	| [https://www.uniprot.org/](https://www.uniprot.org/) | Provides comprehensive information about proteins.        	|
| TISSUES	| [https://tissues.jensenlab.org/](https://tissues.jensenlab.org/) | Offers data on tissue interactions and expressions.     	|
| STRING 	| [https://string-db.org/](https://string-db.org/)   	| Enables analysis of protein-protein interactions.        	|
| STITCH 	| [http://stitch.embl.de/](http://stitch.embl.de/)   	| Provides information on chemical compounds.               	|
| …| | | 




### Graph Structure:

- Nodes: Represent entities like diseases, symptoms, and patient information.
- Edges: Define relationships between nodes, indicating how entities are connected

<div style="text-align: center;">
    <img src="https://lh4.googleusercontent.com/bv4_idWhod5LpgC7E7REVgBRiq0ybAJtOKsvkeF89Q1WGU1IWjfTUPcDyYq0FdaB50z7rwF0qnqbeqNhl24Ou9KzLQhgGFwgbOYZLMwMPTwGxTbv5ebuHBrdqJTirJjERnHHUx-FJGWgNRmvHbngpb03RRYDL0dqp66LYSOr5hI7qnrAgM-igNCd1w" ,alt="Graph Structure" style="max-width: 50%; height: auto;">
</div>
	
[Source](https://lh4.googleusercontent.com/bv4_idWhod5LpgC7E7REVgBRiq0ybAJtOKsvkeF89Q1WGU1IWjfTUPcDyYq0FdaB50z7rwF0qnqbeqNhl24Ou9KzLQhgGFwgbOYZLMwMPTwGxTbv5ebuHBrdqJTirJjERnHHUx-FJGWgNRmvHbngpb03RRYDL0dqp66LYSOr5hI7qnrAgM-igNCd1w)

## Patient Profiles and Disease Mapping:

- Detailed Profiles: Enable in-depth patient understanding.
- Disease Mapping: Relate patients to known diseases via symptoms.
- Optimal Treatments: Facilitate proposing effective, low-risk treatments


## Advantages of Clinical Knowledge Graphs:
### Data Integration and Connectivity:

-  Enhanced data integration and connectivity
-  Easily scalable, accommodating new data sources

### Support in Medical Decision-Making:

-  Supports clinical decision-making
-  Promotes personalized medicine and patient-centered care

### Acceleration of Research:

- Accelerates medical research and discoveries
- Easy integration of new ontologies, databases, and experiments

### Addressing Reproducibility Concerns:

-  Tackles concerns about scientific reproducibility
-  Open source algorithms for transparency and accessibility
-  Version-controlled databases ensure accurate record-keeping
-  Detailed documentation for clear understanding of methods
-  Utilizes Jupyter notebooks for reproducible analysis pipelines


## Challenges and Solutions:

### Data Quality and Privacy Concerns:

- Address data quality and privacy concerns effectively

### Regulatory and Ethical Issues:

- Integrating electronic patient records (EHRs) into CKG demands resolution of regulatory and ethical challenges
-  Diverse database systems and formats across medical institutions require efficient data harmonization.


## Application Examples:

### Non-alcoholic Fatty Liver Disease Study:
- Demonstrated how CKG accelerates and extends data analysis and interpretation
- Automatic analysis in CKG compared to previous manual study
- Default CKG pipeline used for proteomics study of Non-Alcoholic Fatty Liver Disease (NAFLD)
- Discovered new markers (e.g., ALDOB, APOM) associated with liver disease progression

<div style="text-align: center;">
    <img src="https://www.embopress.org/cms/asset/dc1f065e-23b5-4114-8f22-40282367cb35/msb188793-abs-0001-m.jpg" ,alt="Example" style="max-width: 50%; height: auto;">
</div>
[Source](https://www.embopress.org/cms/asset/dc1f065e-23b5-4114-8f22-40282367cb35/msb188793-abs-0001-m.jpg)

**Experimental Approach**:
- Researchers studied liver diseases, particularly NAFLD (Non-Alcoholic Fatty Liver Disease), using advanced techniques to analyze blood proteins


**Identified Proteins:**
- Using these techniques, scientists found specific proteins in the blood that are related to NAFLD. Two of these proteins are called PIGR and ALDOB.

**Potential Biomarkers**
- Scientists discovered proteins like DPP4, ANPEP, PIGR, APOE, and TGFBI that could potentially serve as markers for liver diseases.
- These proteins were found to be closely linked with certain liver enzymes (AST, ALT, GGT, and ALP), which are indicators of liver health


### Clinical Data Analysis:
- Examined patients' health data across different groups (healthy, diabetes, liver diseases)
- Identified connections between liver health, blood pressure, and various health conditions

### Proteomics Data Exploration:
- Detailed summary of proteins and their modifications
- Checked data quality, identified unusual data points, and visualized protein characteristics
- Automated identification of proteins connected to diseases using specific search queries (Cypher)

### Data Analysis and Visualization:
- Simplified complex data for better understanding (Feature Reduction)
- Applied advanced math to find important proteins (Statistical Analysis)
- Visualized relationships between different proteins, identifying patterns (Network Analysis)

### Multiomics Integration:
- Explored relationships between proteins and patients' health data (Correlation Analysis)
- Identified groups of related proteins linked to specific health indicators (WGCNA)

### Results Summarization:
- Visualized connections between proteins, health data, diseases, and scientific literature (Sankey Plot)
- CKG's automated analysis provides detailed insights within minutes, significantly faster than manual processes
- Key Benefits: Accelerates understanding of complex biological data, saving time, improving accuracy, and uncovering new discoveries


## Summary and Future Outlook:

### Next Steps:
- **Establish Local Versions:** Safeguard healthcare data privacy through local CKG versions
- **Cross-Platform Analysis:** Facilitate secure cross-platform analysis with local versions
- **New Approaches:** Explore differential privacy and federated learning for iterative model training without direct sensitive data access
- **Integration of EHRs:** Bridge the gap between research and direct patient care by integrating electronic patient records

### Challenges:
- **Regulatory and Ethical Hurdles:** Navigate through various regulatory and ethical concerns
- **Data Harmonization:** Address difficulties arising from diverse database systems; consider implementing standards like Fast Healthcare Interoperability Resources (FHIR)

### Future Development:
- **Continued Progress:** Expect ongoing advancements in Clinical Knowledge Graphs for transformative impacts on medical research and practice.


## Sources 

[https://ckg.readthedocs.io/en/latest/INTRO.html](https://ckg.readthedocs.io/en/latest/INTRO.html)
[https://ckg.readthedocs.io/en/latest/](https://ckg.readthedocs.io/en/latest/)
[Clinical Knowledge Graph Integrates Proteomics Data into Clinical Decision-Making](https://www.biorxiv.org/content/10.1101/2020.05.09.084897v1)
