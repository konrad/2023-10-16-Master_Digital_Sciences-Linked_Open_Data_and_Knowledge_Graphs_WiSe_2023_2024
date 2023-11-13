# SPARQL and Cypher 

Imagine working with an RDF dataset containing valuable information about music albums and artists. 

Let's consider a few statements:

- The Beatles created the album **"Help"**.
- The Beatles also produced **"Abbey Road"** and **"Let it be"**.
- The Beatles included band member **Paul McCartney**.
- Another band, Wings, released **"Band on the run"** and **"London Town"**.
- Wings also featured band member **Paul McCartney**.
- The Rolling Stones contributed to **"Hot Rocks"**.


## Exploring WH-Questions in RDF

Imagine various queries that a music portal can run over such a dataset. 

Various WH-questions (such as "who," "what," "where") can be posed. For instance:

- **Who made the album "Help"?** 
- **Which albums did The Beatles create?** 

These questions translate into SPARQL queries using RDF triples and variables. For instance:

- Give me all values of X such that X made the album "Help".
- Give me all values of X such that the Beatles made X.

In general, these queries seek values of X and Y where X created Y.

This is like asking a question with two WH-words, such as **"Which bands made which albums?"**.

The answer is not a list of values, as before, but a list of X-Y pairs that could be conveniently presented in a table:

### Resulting Table:

<center>

| X                 | Y                |
| ----------------- | ---------------- |
| The Beatles       | "Help"           |
| The Beatles       | "Abbey Road"     |
| The Beatles       | "Let it be"      |
| Wings             | "Band on the run"|
| Wings             | "London Town"    |
| The Rolling Stones| "Hot Rocks"

</center>


## Constructing Complex Queries

Complex queries can involve multiple statements. For example, finding values of X and Y where: 
- (a) X made Y, and 
- (b) X includes band member Paul McCartney.

The answer would be the first five pairs from the previous answer. 


# SPARQL: Querying RDF Data

**SPARQL** stands for *SPARQL Protocol And RDF Query Language*:

- **Developed by:** The **World Wide Web Consortium (W3C)**
- **Standardized:** Became a W3C standard in January 2008
- **Purpose:** Used to retrieve and manipulate data stored in **RDF format**
- **Suitability:** Well-suited for querying **linked data** and **semantic web applications**
- **Functionality:** Allows execution of complex queries on **RDF data**


## SPARQL Query Example

To answer the question **"Which albums did the Beatles make?"**, the following SPARQL query can be used:

```
PREFIX dbpedia: <http://dbpedia.org/resource/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX mo: <http://purl.org/ontology/mo/>

SELECT ?album
WHERE { 
    dbpedia:The_Beatles foaf:made ?album .
    ?album a mo:SignalGroup
} 
```

This query retrieves all albums (?album) made by The Beatles, using appropriate RDF prefixes and properties.

By utilizing RDF data and SPARQL queries, complex questions about relationships between entities and their properties can be effectively explored and answered.


## Understanding the Components of a SPARQL Query

### 1. PREFIX Statements
- **Definition:** Provide abbreviations for namespaces.
- **Usage:** Used to shorten URIs in the query for better readability.

### 2. Variable Definition
- **Definition:** SELECT line introduces a variable (denoted by a question mark '?'), similar to variables like X and Y in previous examples.
- **Usage:** Variables are used to represent unknown values in the query results.

### 3. Triple Patterns in WHERE Clause
- **Definition:** The WHERE clause contains RDF triple patterns, similar to RDF triples but with variables.
- **Usage:** Triple patterns are used to match specific data patterns in the RDF dataset.

### 4. Example Query Patterns
- **Definition:** Consists of triple patterns that define specific conditions in the query.
- **Example:**
  - One pattern identifies resources created by the Beatles.
  - Another pattern specifies that these resources must belong to the 'mo:SignalGroup' class, differentiating albums from individual tracks.

## Structure of a SPARQL Query 

<div style="text-align: center;">
    <img src="https://kbpedia.org/cwpk-files/sparql-query-parts.png" ,alt="Query Structure" style="max-width: 50%; height: auto;">
</div>

https://kbpedia.org/cwpk-files/sparql-query-parts.png


The response to a query is computed by a process known as graph matching:


<div style="text-align: center;">
    <img src="https://euclid-project.eu/sites/default/files/images/matching.png",alt="test" style="max-width: 50%; height: auto;">
</div>

https://euclid-project.eu/sites/default/files/images/matching.png


# Cypher: Querying Graph Databases

**Cypher** is a query language developed by **Neo4j** in 2011. It is a:

- **Declarative Graph Query Language:** An SQL-equivalent language for graph databases.
- **Focus:** Concentrates on what to retrieve from the graph rather than how to retrieve it.
- **Visual Representation:** Provides a visual way of matching patterns and relationships using ASCII-art:
  - Example: `where (nodes)-[:ARE_CONNECTED_TO]->(otherNodes)`
- **Intuitive:** Highly intuitive language to both read and write.
- **Schema Flexibility:** Nodes and relationships in Neo4j do not require specific properties, allowing for schema evolution.
- **Sharing Properties:** Nodes/relationships can share properties without strict schema rules.


# RDF Graphs vs. Property Graphs

|                     | **RDF Graphs**                                   | **Property Graphs**                                   |
|---------------------|---------------------------------------------------|-------------------------------------------------------|
| **Database Type**   | Designed for RDF data                            | Designed for graph systems like Neo4j                |
| **Representation**  | Stores data in triples (subject, predicate, object) | Data stored as nodes and edges (Nodes = entities; edges = relationships) |
| **Querying Languages**| Uses SPARQL, a standard language                  | No fixed standard; each organization creates custom query languages |
| **Internal Structure**| Entities and relationships in RDF lack internal structures, only recognized by their URIs | Nodes and edges contain properties, providing detailed info |
| **Focus**           | Focuses on standardization and compatibility      | Focuses on optimizing storage and quick querying       |
| **Advantages**      | Ensures consistent data representation and querying | Offers detailed insights through relationships and properties |
|                     | Allows flexible data addition without reconstruction | Simple setup and user-friendly for beginners           |
| **Disadvantages**   | Complex deep searches due to intricate relationships | Limited interoperability, unique identifiers local to each graph |
|| RDF's triple format limits connections to two objects at a time| 


# Queries 

## Basic SPARQL queries 

| **Query Type** | **Description** |
| -------------- | --------------- |
| **ASK**        | Tests if there are resources in the dataset matching specified conditions. Response: True or False. |
| **SELECT**     | Returns a table with columns as variables and rows as variable bindings satisfying specified conditions. |
| **CONSTRUCT**  | returns an RDF graph (i.e., set of triples) matching a template, using variable bindings obtained from the dataset using a search pattern|
| **DESCRIBE**   | Extracts an RDF graph providing all available information about a specified resource(s) in the dataset. |



# Basic Cypher Queries

In Neo4j graph databases:

- Data entities are nodes, referenced in Cypher using parenthesis `( )`.
- Relationships connect nodes in a graph and have a start node, an end node, and a single type.

### Example Cypher Query:

```cypher
MATCH (n:Person {name:'Anna'})
RETURN n.born AS birthYear
```

Node Details:

- Node labeled as "Person." Labels enable specific node queries.
- Contains a "name" property set to "Anna" within curly braces {}.
- Utilizes a variable, "n," for referencing nodes in subsequent clauses.

## Query Explanation:

- **MATCH Clause:** The MATCH clause is used to specify the search pattern. In this case, it finds all nodes labeled as "Person" with the "name" property set to "Anna" and binds them to the variable "n."
- **RETURN Clause:** The RETURN clause formats and organizes the output of the query results. It returns the value of a different property ("born"), belonging to the same node referenced by the variable "n."

## Relationship Details:

- **Start and End Nodes:** Relationships connect nodes in a graph and have a start node, an end node, and a single type.
- **Representation:** In Cypher, relationships are represented with arrows (e.g., `-->`), indicating the direction of the relationship.

These details are crucial when constructing and understanding Cypher queries for graph databases.
  


| **Keyword** | **Description** |
| ----------- | --------------- |
| **MATCH**   | Specifies the search pattern for finding nodes, relationships, or combinations of nodes and relationships together. |
| **WHERE**  | Adds additional constraints to patterns and filters out unwanted patterns. |
| **RETURN**  | Formats and organizes the output of query results. Allows specifying properties, lists, ordering, and more for the output. |
| **CREATE**  | Creates nodes and relationships in the database. |
| **DELETE**  | Removes nodes, relationships, and properties from the database. Nodes can be deleted only if they have no other existing relationships. |
| **SET**     | Modifies property values and adds labels on nodes. |
| **REMOVE**  | Removes property values and labels from nodes. |
| **MERGE**   | Creates nodes uniquely without duplicates. |



# Simplifying RDF IRI's for Readability

- **Abbreviation in Angle Brackets:** RDF IRI's (Internationalized Resource Identifiers) can be abbreviated to local names enclosed in angle brackets. For example, `<john> <age> 11`.

- **Handling Namespace:** If there is a specific namespace (like a category or domain) for the identifiers, it should be incorporated into the IRI. For instance, `<http://neo.org/movies#john>` is a valid IRI where `http://neo.org/movies#` is the namespace and `john` is the specific identifier within that namespace.




# Basic Queries 

<div style="text-align: center;">
    <img src="https://dz2cdn1.dzone.com/storage/temp/10936669-table1.png" alt="Basic Queries" style="max-width: 50%; height: auto;">
</div>
https://dz2cdn1.dzone.com/storage/temp/10936669-table1.png



# Cypher CREATE and SPARQL INSERT

Create a person named Emil from Sweden with klout 99.


SPARQL 

```
INSERT DATA {
    <ee> a <Person>;
    <name> "Emil";
    <from> "Sweden";
    <klout> 99
}
```


Cypher 

```
CREATE (ee:Person {
    name: "Emil",
    country: "Sweden",
    klout: 99
})
```


# Creating Nodes and Relationships

<div style="text-align: center;">
    <img src="https://dz2cdn1.dzone.com/storage/temp/10812092-figure4.png" alt="Creating nodes" style="max-width: 50%; height: auto;">
</div>

https://dz2cdn1.dzone.com/storage/temp/10812092-figure4.png

#

<center>

| ID  | Name    | From       | Hobby   | Pet   | Title  |
| --- | ------- | ---------- | ------- | ----- | ------ |
| 1   | Emil    | -          | -       | -     | -      |
| 2   | Johan   | Sweden     | -       | Orval | author |
| 3   | Ian     | England    | -       | -     | -      |
| 4   | Rik     | Belgium    | -       | -     | -      |
| 5   | Allison | California | surfing | -     | -      |

</center>



# Relationships:

- Emil knows Johan since 2001 and rates their relationship 5 stars.
- Emil knows Ian.
- Johan knows Ian.
- Johan knows Rik.
- Ian knows Allison.
- Ian knows Ally.
- Rik knows Ally.



# Cypher MATCH and SPARQL WHERE

Finding nodes find the node representing Emil:  

SPARQL 

```
SELECT ?ee
WHERE { ?ee a <Person>;<name> ?name.
 FILTER (?name="Emil")}
```

```
SELECT ?ee
WHERE { ?ee a <Person>;<name> "Emil"}
```


Cypher 

```
MATCH (ee:Person) 
WHERE ee.name = "Emil"
RETURN ee; 
```

            

# Pattern Matching

Finding Emil's friends

SPARQL 

```
SELECT ?ee ?friends
WHERE { ?ee a <Person>;
            <name> "Emil";
            <knows> ?friends}

```


Cypher 

```
MATCH (ee:Person)-[:KNOWS]-(friends)
WHERE ee.name = "Emil"
RETURN ee, friends
```

# Recommendations

Johan is learning to surf, so he may want to find a new friend who already does:

SPARQL 

```
SELECT DISTINCT ?surfer
WHERE { ?js a <Person>;
            <name> "Johan";
            <knows>/<knows> ?surfer;
            ?surfer <hobby> "surfing".}

```      


Cypher 

```
MATCH (js:Person)-[:KNOWS]-()-:[KNOWS]-(surfer)
WHERE js.name = "Johan" AND surfer.hobby = "surfing"
RETURN DISTINCT surfer
```


# Movie Graph Example

<div style="text-align: center;">
    <img src="https://dz2cdn1.dzone.com/storage/temp/10812277-figure7.png" alt="Creating nodes movie graph" style="max-width: 50%; height: auto;">
</div>

https://dz2cdn1.dzone.com/storage/temp/10812277-figure7.png

#

### Movies

<center>

| ID        | Title      | Released | Tagline                    |
|-----------|-------------|----------|-----------------------------|
| TheMatrix | The Matrix | 1999     | Welcome to the Real World |
</center>


### People

<center>

| ID      | Name              | Born |
|---------|--------------------|------|
| Keanu   | Keanu Reeves      | 1964 |
| Carrie  | Carrie-Anne Moss   | 1967 |
| Laurence| Laurence Fishburne| 1961 |
| Hugo    | Hugo Weaving       | 1960 |
| AndyW   | Andy Wachowski     | 1967 |
| LanaW   | Lana Wachowski     | 1965 |
| JoelS   | Joel Silver        | 1952 |

</center>

### Relationships

<center>

| Relationship | From    | To         | Roles        |
|--------------|---------|------------|--------------|
| ACTED_IN     | Keanu   | TheMatrix  | Neo          |
| ACTED_IN     | Carrie  | TheMatrix  | Trinity      |
| ACTED_IN     | Laurence| TheMatrix  | Morpheus     |
| ACTED_IN     | Hugo    | TheMatrix  | Agent Smith  |
| DIRECTED     | AndyW   | TheMatrix  | -            |
| DIRECTED     | LanaW   | TheMatrix  | -            |
| PRODUCED     | JoelS   | TheMatrix  | -            |

</center>

Finding Actors in the Movie Graph:
- Find the actor named "Tom Hanks."

SPARQL 

``` SELECT ?tom 
WHERE {?tom < name> "Tom Hanks"} 
```

Cypher 

``` 
MATCH (tom {name: "Tom Hanks"}) 
RETURN tom 
```

Finding Specific Movies:
- Find the movie with the title "Cloud Atlas."

SPARQL 
```
SELECT ?cloudAtlas 
WHERE {?cloudAtlas < title> "Cloud Atlas"}
```

Cypher
```
MATCH (cloudAtlas (title: "Cloud Atlas") 
RETURN cloudAtlas
```
        
Finding Multiple People:
- Find 10 people.

SPARQL 
```
SELECT ?паme 
WHERE {?people a < Person>; < name> ?name.} 
LIMIT 10
```

Cypher 
```
MATCH (people:Person) RETURN people.name LIMIT 10]
```

Finding Movies Released in the 1990s:
- Find movies released in the 1990s.

SPARQL
```
SELECT ?title 
WHERE (nineties a < Movie>; <released> ?released; < title> ?title. 
FILTER(?released > 1990 && ?released < 2000)
```

Cypher 

```
MATCH (nineties:Movie) 
WHERE nineties.released > 1990 AND nineties.released < 2000 
RETURN nineties.title
```

Finding Patterns Within the Movie Graph

1. Actors are people who acted in movies

2. Directors are people who directed a movie

3. What other relationships exist?

List all Tom Hanks movies

SPARQL 
```
SELECT ?tom ?tomHanksMovies 
WHERE{Ptom a ‹Person>;<name> "Tom Hanks"; <ACTED_IN> ?tomHanksMovies}
```

Cypher 

```
MATCH (tom:Person {name: "Tom Hanks"})-[ACTED _IN]->(tomHanksMovies) 
RETURN tom,tomHanksMovies
```

Who directed "Cloud Atlas"?

SPARQL 
```
SELECT ?name 
WHERE {?cloudAtlas <title> "Cloud Atlas" ;^<DIRECTED> ?directors ?directors < name> ?name}
```


Cypher 
```
MATCH (cloudAtlas {title: "Cloud Atlas"})<-[:DIRECTED]-(directors) 
RETURN directors.name
```

How people are related to "Cloud Atlas"

SPARQL 
```
SELECT ?name ?relatedTo 
WHERE {?people a <Person>. ?people PrelatedTo ?movie. ?movie <title> "Cloud Atlas". }
```

Cypher
```
MATCH (people: Person)-[relatedTo]-(:Movie {title: "Cloud Atlas"}) 
RETURN people.name, Type(relatedTo), relatedTo
```

**Conclusion: Choosing Between SPARQL and Cypher:**
- **Considerations:**
  - **Data Structure:** Analyze your data model. If it's primarily RDF-based, SPARQL is the natural choice. For graph databases, especially those involving relationships, Cypher is the preferred option.
  - **Complexity of Queries:** Evaluate the complexity of your queries. For straightforward queries on linked data, SPARQL is user-friendly. For intricate relationship patterns, Cypher's expressive syntax makes complex queries manageable.




### Additional Resources:
- [Euclid Project Chapter 2](http://euclid-project.eu/modules/chapter2/)
- [GitHub with Query Examples](https://gist.github.com/Xeragus/2319c14d1de69f69af6ffc647ec2d0fa)
- [Sparql and Cypher](https://dzone.com/articles/sparql-and-cypher) 
- [Sparql Cheat Sheet](https://www.iro.umontreal.ca/~lapalme/ift6281/sparql-1_1-cheat-sheet.pdf)
- [Guide Cypher Basics](https://neo4j.com/developer/cypher/guide-cypher-basics)
- [Neo4j Cypher Documentation](https://neo4j.com/developer/cypher/)
- [SPARQL 1.1 Query Language Specification](https://www.w3.org/TR/sparql11-query/)
- [A Deep Dive into Graph Query Languages: Cypher, Gremlin, and SPARQL](https://ts2.space/en/a-deep-dive-into-graph-query-languages-cypher-gremlin-and-sparql/)
- [Cypher-Manual Queries concepts](https://neo4j.com/docs/cypher-manual/current/queries/concepts/)
- [RDF Triple Store vs. Labeled Property Graph: What’s the Difference?](https://neo4j.com/blog/rdf-triple-store-vs-labeled-property-graph-difference/) 
- [Knowledge Graphs: RDF or Property Graphs, Which One Should You Pick?](https://www.wisecube.ai/blog/knowledge-graphs-rdf-or-property-graphs-which-one-should-you-pick/) 
 



