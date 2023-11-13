# LinkClimate: An interoperable knowledge graph platfrom for climate data

2023-11-13, Finn Heydemann

## TOC

1. Introduction
2. Goals 
3. Workflow
4. Semantics Creation
5. Ontology Alignment 
6. Linkage to OpenStreetMap and Wikidata
7. SPARQL Query
8. Further Implementations
9. Knowledge Graph Evalutation
10. Web Interface
11. Conclusion and future works

## Introduction

- Climate Change is an urgent and pressing topic
- Historical climate data is needed to predict effects of climate change
- Data sources are often spread across many data silos across the web
- Time consuming task to gather data
- Link to geographical information useful
- Climate Knowledge Graph for multiple datasets (dynamically updated)

## Goals

* Online KG populated with climate data
* Integration of different climate data sources and linkage with geographic (OpenStreetMap) and encyclopedic (Wikidata) information
* Automated synchronization
* Easy access for researchers: Web Interface

## Workflow

![Workflow](https://ars.els-cdn.com/content/image/1-s2.0-S0098300422001649-gr1_lrg.jpg)

## Semantic Creation

![Semantic Creation](https://ars.els-cdn.com/content/image/1-s2.0-S0098300422001649-gr2_lrg.jpg)

## Ontology Alignment

* Goal integrative compatibility with large outside dataset (e.g. AEMET)
* Climate Analysis Ontology (NOAA) manually linked with vocabulary from W3C or other KG e.g. ca:Station → owl:sameAs → aemet: WeatherStation
* Conceptual linkages to AEMET KG 

## Linkage to OpenStreetMap and Wikidata

* Data from several domains needed for better climate models (e.g. urbanization)

* NOAA climate data, station with longitude and latitude → request geographical information from OpenStreetMap

* The results (e.g. country, city, code) are linked to the unique wikidata identifier

  ![Linkage to OpenStreetMap](https://ars.els-cdn.com/content/image/1-s2.0-S0098300422001649-gr3_lrg.jpg)

## SPARQL Query

![SPAQL Query](https://ars.els-cdn.com/content/image/1-s2.0-S0098300422001649-fx1_lrg.jpg)

## Further Implementations

* Collection Strategy
  * Dynamically updated data
  * Sliding windows download

* Publishing as Linked Data
  * SPARQL language
  * Step-by-step guide for users unfamiliar with SPARQL

## Knowledge Graph Evaluation

* Collection of questions proposed by group of domain stakeholders to evaluate system capacity

  1. Where are all the stations that are located in a particular administrative region?*

  2. Which station is the nearest to a certain station?
  3. Which stations fall inside a certain range of latitude and longitude coordinates?
  4. How can I group stations according to a particular observed *[climatic variable](https://www.sciencedirect.com/topics/computer-science/climatic-variable)?*
  5. How to find climate variables that are recorded by a particular station?
  6. How long has a certain climatic variable been monitored by a particular station?
  7. How can a time series for a single climatic variable be retrieved?
  8. How can a time series for a number of different climatic variables be retrieved?
  9. How can station observations be aggregated according to their temporal resolution?
  10. How can I determine the station’s geographical context?
  11. How to include extra environmental data into a station’s or set of  stations’ knowledge graph in order to do cross-domain data analysis?

* Result: Most questions answerable, but problems with
  geographical relationships

## Web Interface

![Web Interface](https://ars.els-cdn.com/content/image/1-s2.0-S0098300422001649-gr5_lrg.jpg)

* 31 user responses about their practice with the web-interface
* Well usable but should be more intuitive

## Conclusion and future work

* Dynamically fetches data from NOAA and stores it in a KG
* Weather stations are interconnected via longitude and latitude with OpenStreetMap and Wikidata-Codes
* More information about stations (e.g. mountains or water bodies)
* Include other climate-related data such as air pollution or ocean data
