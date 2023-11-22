# OpenAlex

2023-11-06, Leon Munz & Andreas Kruff

## TOC

- What is OpenAlex
- The Relevance of Open-Source
- How does it work
- Third Party Tools
---
## What is OpenAlex

### General Information

- Created by OurResearch
    - (Non-profit organisation)

 ![logo_ourresearch](https://upload.wikimedia.org/wikipedia/commons/d/d9/Ourresearch_logo.png)


- Named after the ancient library of Alexandria
- Launched January 1st 2022
- Unofficial successor of MAG (Microsoft Academic Graph)
- Public commitment to Principles of Open Scholarly Infrastructure
- Financially supported by Arcadia
    - charitable fund by Lisbet Rausing & Peter Baldwin
---
### USP

- Big database with
    - High coverage
    - Strong emphasis on non-english works and content from global south

- Easy to use services
    - fast
    - modern
    - easy

"OpenAlex offers an open replacement for industry-standard scientific knowledge bases like Elsevier's Scopus and Clarivate's Web of Science. Compared to these paywalled services, OpenAlex offers significant advantages in terms of inclusivity, affordability, and availability."

<iframediv data-v-1fe1ba8a="" class="v-data-table theme--light" id="comparisonTable"><div class="v-data-table__wrapper"><table><thead data-v-1fe1ba8a=""><tr data-v-1fe1ba8a=""><th data-v-1fe1ba8a="" class="text-left"></th><th data-v-1fe1ba8a="" class="text-left"> Number of works </th><th data-v-1fe1ba8a="" class="text-left"> Open Access works </th><th data-v-1fe1ba8a="" class="text-left"> Citations </th><th data-v-1fe1ba8a="" class="text-left"> Price </th><th data-v-1fe1ba8a="" class="text-left"> Data Openness </th><th data-v-1fe1ba8a="" class="text-left"> Org structure </th></tr></thead><tbody data-v-1fe1ba8a=""><tr data-v-1fe1ba8a=""><td data-v-1fe1ba8a="" class="text-h6"><a data-v-1fe1ba8a="" href="https://openalex.org/" target="_blank" rel="noopener noreferrer">OpenAlex</a></td><td data-v-1fe1ba8a="">243M</td><td data-v-1fe1ba8a="">48M</td><td data-v-1fe1ba8a="">1.9B</td><td data-v-1fe1ba8a="">Freemium</td><td data-v-1fe1ba8a="">Fully open, CC0 license</td><td data-v-1fe1ba8a="">Non-profit</td></tr><tr data-v-1fe1ba8a=""><td data-v-1fe1ba8a="" class="text-h6"><a data-v-1fe1ba8a="" href="https://www.elsevier.com/solutions/scopus" target="_blank" rel="noopener noreferrer">Scopus</a></td><td data-v-1fe1ba8a="">87M</td><td data-v-1fe1ba8a="">20.5M (<a href="https://blog.scopus.com/posts/scopus-now-includes-90-million-content-records" target="_blank" rel="noopener noreferrer">ref</a>)</td><td data-v-1fe1ba8a="">1.8B</td><td data-v-1fe1ba8a="">Subscription</td><td data-v-1fe1ba8a="">Closed</td><td data-v-1fe1ba8a="">For Profit</td></tr><tr data-v-1fe1ba8a=""><td data-v-1fe1ba8a="" class="text-h6"><a data-v-1fe1ba8a="" href="https://clarivate.com/webofsciencegroup/solutions/web-of-science" target="_blank" rel="noopener noreferrer">Web of Science (core)</a></td><td data-v-1fe1ba8a="">87M (<a href="https://clarivate.libguides.com/librarianresources/coverage" target="_blank" rel="noopener noreferrer">ref</a>)</td><td data-v-1fe1ba8a="">12M (<a href="https://clarivate.com/webofsciencegroup/solutions/open-access/" target="_blank" rel="noopener noreferrer">ref</a>)</td><td data-v-1fe1ba8a="">1.8B</td><td data-v-1fe1ba8a="">Subscription</td><td data-v-1fe1ba8a="">Closed</td><td data-v-1fe1ba8a="">For Profit</td></tr><tr data-v-1fe1ba8a=""><td data-v-1fe1ba8a="" class="text-h6"><a data-v-1fe1ba8a="" href="https://www.dimensions.ai/" target="_blank" rel="noopener noreferrer">Dimensions</a></td><td data-v-1fe1ba8a="">135M</td><td data-v-1fe1ba8a="">29M (<a href="https://www.dimensions.ai/resources/evaluate-your-universitys-oa-status/" target="_blank" rel="noopener noreferrer">ref</a>)</td><td data-v-1fe1ba8a="">1.7B</td><td data-v-1fe1ba8a="">Freemium</td><td data-v-1fe1ba8a="">Partly open, personal use</td><td data-v-1fe1ba8a="">For Profit</td></tr><tr data-v-1fe1ba8a=""><td data-v-1fe1ba8a="" class="text-h6"><a data-v-1fe1ba8a="" href="https://scholar.google.com/" target="_blank" rel="noopener noreferrer">Google Scholar</a></td><td data-v-1fe1ba8a="">389M (<a href="https://doi.org/10.1007/s11192-018-2958-5" target="_blank" rel="noopener noreferrer">estimated</a>)</td><td data-v-1fe1ba8a="">?</td><td data-v-1fe1ba8a="">?</td><td data-v-1fe1ba8a="">Free</td><td data-v-1fe1ba8a="">Closed</td><td data-v-1fe1ba8a="">For Profit</td></tr><tr data-v-1fe1ba8a=""><td data-v-1fe1ba8a="" class="text-h6"><a data-v-1fe1ba8a="" href="https://www.crossref.org/" target="_blank" rel="noopener noreferrer">Crossref</a></td><td data-v-1fe1ba8a="">145M</td><td data-v-1fe1ba8a="">20M</td><td data-v-1fe1ba8a="">1.45B</td><td data-v-1fe1ba8a="">Free</td><td data-v-1fe1ba8a="">Fully open, CC0 license</td><td data-v-1fe1ba8a="">Non-profit</td></tr></tbody></table></div></div></iframe>
---
### Fremium Concept

- API is completly free to use
- Premium service offered to achieve sustainability

<iframediv data-v-125aaf2a="" class="tg-wrap"><table data-v-125aaf2a="" class="tg"><thead data-v-125aaf2a=""><tr data-v-125aaf2a=""><th data-v-125aaf2a="" class="tg-g1fv"></th><th data-v-125aaf2a="" class="tg-9ase">Free<br data-v-125aaf2a=""></th><th data-v-125aaf2a="" class="tg-9ase">Premium</th></tr></thead><tbody data-v-125aaf2a=""><tr data-v-125aaf2a=""><td data-v-125aaf2a="" class="tg-0pky">Update frequency</td><td data-v-125aaf2a="" class="tg-9etm">Monthly (via data dump)</td><td data-v-125aaf2a="" class="tg-pgpg">Hourly (via API)<br data-v-125aaf2a=""></td></tr><tr data-v-125aaf2a=""><td data-v-125aaf2a="" class="tg-0pky">API limit</td><td data-v-125aaf2a="" class="tg-9etm">100k/day, max 10/second</td><td data-v-125aaf2a="" class="tg-pgpg">As needed</td></tr><tr data-v-125aaf2a=""><td data-v-125aaf2a="" class="tg-0pky">Support</td><td data-v-125aaf2a="" class="tg-9etm">Best effort</td><td data-v-125aaf2a="" class="tg-pgpg">Priority</td></tr></tbody></table></div>  </iframe>
---
### Data Sources

- Microsoft Academic Graph (MAG)
- Crossref
- Web-Crawls
- Subject and institutional repositories

Furthermore:
- ORCID
- DOAJ
- ISSN
- ROR
- PubMed & Pubmed Central
- Unpaywall
- Internet Archive
---
### License

Data is published under CC0 (Creative Commons Zero)

“No rights reserved”

Allows waiving all their copyright and related rights in their works to the fullest extent allowed by law

Including:
- Surrender of copyright
- Surrender of neighboring and related rights
- Surrender of publicity rights
- Surrender of privacy rights
- Waiving rights in some jurisdictions
- Moral rights and unknown rights

---
## The Relevance of Open-Source

Principles of Open Scholarly Infrastructure (POSI)
---
### Core Principles:
- Openness and Accessibility:
  - Infrastructure should be freely accessible and supportive of open research.

- Interoperability:
  - Systems should be compatible and capable of data exchange.

- Sustainability and Governance:
  - Long-term funding and responsible management are critical.

- Community Engagement:
  - Involvement of the scholarly community in development and operation.
---
### Key Aspects in Detail:

####  Governance:

- Coverage across the research enterprise
- Stakeholder Governed
- Non-discriminatory membership
- Transparent operations
- Cannot lobby
- Living will
- Formal incentives to fulfil mission & wind-down

####  Sustainability:

- Time-limited funds are used only for time-limited activities
- Goal to generate surplus
- Goal to create contingency fund to support operations for 12 months
- Mission-consistent revenue generation
- Revenue based on services, not data

#### Insurance:

- Open source
- Open data
- Available data (within constraints of privacy laws)
- Patent non-assertion

### Other adopters of POSI:

- Crossref
- CORE
- DataCite
- DOAJ
- Dryad
- Europe PMC
- JOSS
- Liberate Science
- OAPEN & DOAB
- OA Switchboard
- OpenAIRE
- OpenCitations
- OurResearch
- ROR
- Sciety


---
## How does it Work?

### Entities:

- Works: Scholarly documents like journal articles, books, datasets, and theses
- Authors: People who create works
- Sources: Where works are hosted
- Institutions: Universities and other organizations
- Concepts: Topics assigned to works
- Publishers: Companies and organizations that distribute works
- Founders: Organizations that fund research
- Geo: Where things are in the world

### Conception:

- The OpenAlex dataset describes scholarly entities.
- Together, they form a vast web
- This network comprises hundreds of millions of entities
- There are billions of connections among these entities

![Conceptioon](https://2520693015-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FpHVuV3Ib5KXeBKft4Kcl%2Fuploads%2F9s4yv1wQ2CnLzeWaheP1%2Fentities.png?alt=media&token=0827488f-f289-4a9a-9273-18781f676d09)

### Accessing the Data:

- Full data dump available, updated every two weeks
- REST API provided for daily, up-to-date access.
- A user-friendly web-based GUI built on the OpenAlex REST API for easy data retrieval and exploration.

### Identification of Resources:

- Entities are assigned a persistent
- OpenAlex ID
- Expressed as URL
- Can be resolved as human readable Webpage or Json object representation
- Additional assignments of ID’s from external system to improve interoperability

#### Additional Canonical External IDs:

- Works: DOI
- Authors: ORCID
- Sources: ISSN-L
- Institutions: ROR ID
- Concepts: Wikidata ID
- Publishers: Wikidata ID
---
## Third Party Tools

Policy allows for usage of multiple third party tools
- VOSviewer allows for interactively discover OpenAlex Data

![VosViewer](https://2520693015-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FpHVuV3Ib5KXeBKft4Kcl%2Fuploads%2FUnMEyckJdmAKOd3selgl%2FScreenshot%20by%20Dropbox%20Capture.png?alt=media&token=2277fb73-73d8-44b5-9945-140815a18389)

---
- SemOpenAlex offering a RDF representation of OpenAlex Data
<img src="https://media.springernature.com/lw685/springer-static/image/chp%3A10.1007%2F978-3-031-47243-5_6/MediaObjects/554987_1_En_6_Fig1_HTML.png" alt="Alt-Text" style="transform: rotate(90deg); width:300px; height:auto;">


- SemOpenAlex is a project that provides RDF (Resource Description Framework) representations of OpenAlex data.
The world's most extensive scholarly knowledge graph with over 30 billion RDF triples

By offering RDF representations of OpenAlex data, SemOpenAlex allows users to access and work with OpenAlex data in a format that is conducive to semantic web applications, knowledge graph construction, and data integration with other linked data sources

---

### Additional API Implementations:

- R (openalexR)
- Kotlin (KtAlex)
- Python (PyAlex)
- Python (diophila)
- Python (OpenAlexAPI)

This flexibility in tool usage and the availability of API implementations in different languages make OpenAlex a valuable resource for researchers and developers working with diverse data sources.


---
## Literature:

Bilder, Geoffrey; Lin, Jennifer; Neylon, Cameron (2015). Principles for Open Scholarly Infrastructures-v1. figshare. Journal contribution. https://doi.org/10.6084/m9.figshare.1314859.v1

Färber, M., Lamprecht, D., Krause, J., Aung, L., & Haase, P. (2023). SemOpenAlex: The Scientific Landscape in 26 Billion RDF Triples. arXiv preprint, arXiv:2308.03671.

Priem, J., Piwowar, H., & Orr, R. (2022). OpenAlex: A fully-open index of scholarly works, authors, venues, institutions, and concepts. arXiv preprint, arXiv:2205.01833.
