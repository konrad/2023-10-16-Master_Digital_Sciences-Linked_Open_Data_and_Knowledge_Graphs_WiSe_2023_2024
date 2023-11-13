# The Web Ontology Language

## The Semantic Web 
- extension of the World Wide Web
- focus on machine-readable information
- goal: find ways to present information so that machines can handle it in an effective way
- formed standards to enable the exchange of information between different applications and platforms and enable their interrelation (*interoperability*)
- ontology languages: Web Ontology Language (OWL) and RDF 

## Ontology
- formal description of knowledge as set of concepts within a domain and their relationships
- description includes following components:
  - individuals/instances
  - classes
  - attributes
  - relations
  - restrictions
  - rules
  - axioms
- part of W3C standards for the Semantic Web
- provides structure to link one piece of information to other pieces of information on the Web

## The Web Ontology Language (OWL) - Definition
- standardised as ontology language by W3C in February 2004
- solves limitations of RDF(S)
- based on formal logic and enables implicit knowledge through logical reasoning
- different sublanguages for different needs
- provides varying leves of expressiveness and complexity (scalability)

| OWL Full | OWL DL | OWL Light |
|----------|----------|----------|
| contains OWL DL and OWL Lite    | contains OWL Lite, sublanguage of OWL Full  | sublanguage of OWL DL and OWL Full  |
| contains all of RDFS    | supported by current software tools   | decidable   |
| very expressive    | decidable   | less expressive   |
| undecidable    |   |    |

- two different syntaxes: OWL-RDF-Syntax and abstract OWL-Syntax

## OWL Tools
### Editors
- Protégé : http://protege.stanford.edu/
- SWOOP : http://www.mindswap.org/2004/SWOOP/
- OWL Tools : http://owltools.ontoware.org/

### Inference machines
- Pellet : http://www.mindswap.org/2003/pellet/index.shtml
- KAON2 : http://kaon2.semanticweb.org/
- FaCT++ : http://owl.man.ac.uk/factplusplus/
- RacerPro : http://www.racer-systems.com/
- Cerebra : http://www.cerebra.com/index.html

## OWL Document
![Alt text](owl_document.png)

## Classes
- defined by `owl:Class`, subclass of `rdfs:Class` 
```
<rdf:Description rdf:about="professor">
  <rdf:type rdf:resource="&owl;Class"/>
</rdf:Description>
```

or:

```
<owl:Class rdf:about="professor"/>
```

- using `rdf:about="professor"`, the class is assigned the name `professor`, which can be used for references to the class
- two predefined classes in OWL: 
  - `owl:Thing`: contains everything, most general
  - `owl:Nothing`: empty

## Instances
- individuals can be declared as instances of classes in RDF
```
<rdf:Description rdf:about="RudiStuder">
  <rdf:type rdf:resource="professor"/>
</rdf:Description>
```
or:

```
<Professor rdf:about="RudiStuder"/>
```

## Properties
- abstract property
  - connects instances with instances
```
<owl:ObjectProperty rdf:about="affiliation"/>
```

- concrete property
  - connects instances with concrete data values
```
<owl:DatatypeProperty rdf:about="firstname"/>
```
- ranges, to which roles refer, can be declared with `rdfs:domain` and `rdfs:range`
```
<owl:ObjectProperty rdf:about="affiliation">
  <rdfs:domain rdf:resource="person"/>
  <rdfs:range rdf:resource="organization"/>
</owl:ObjectProperty>

<owl:DatatypeProperty rdf:about="firstname">
  <rdfs:domain rdf:resource="person" />
  <rdfs:range rdf:resource="&xsd;string"/>
</owl:DatatypeProperty>
```
- other xml data types supported in OWL: `xsd:boolean`, `xsd:decimal`, `xsd:float`...


## Class Relations
- classes can be related to each other as in RDF using `rdfs:subClassOf` 
```
<owl:Class rdf:about="professor">
  <rdfs:subClassOf rdf:resource="faculty member"/>
</owl:Class>
```
- others relations: `owl:disjointWith`(declare disjoint), `owl:equivalentClass` (declare equivalent)

### Inference (classes)
- possibility for inference of implicit knowledge

#### `rdfs:subClassOf`
```
<owl:Class rdf:about="professor">
  <rdfs:subClassOf rdf:resource="faculty member"/>
</owl:Class>
<owl:Class rdf:about="faculty member">
  <rdfs:subClassOf rdf:resource="person"/>
</owl:Class>
```

#### `owl:disjointWith`
```
<owl:Class rdf:about="professor">
  <rdfs:subClassOf rdf:resource="faculty member"/>
</owl:Class>

<owl:Class rdf:about="book">
  <rdfs:subClassOf rdf:resource="publication"/>
</owl:Class>

<owl:Class rdf:about="faculty member">
  <owl:disjointWith rdf:resource="publication"/>
</owl:Class>
```
- Inference: `professor` and `book` are disjoint

#### `owl:equivalentClass`
```
<owl:Class rdf:about="book">
  <rdfs:subClassOf rdf:resource="publication"/>
</owl:Class>

<owl:Class rdf:about="publication">
  <owl:equivalentClass rdf:resource="Publikation"/>
</owl:Class>
```
- Inference: `book` is subclass of `Publikation`

### Relationships between Individuals
- different identifiers denote the same individual with `owl:sameAs`:
```
<rdf:Description rdf:about="RudiStuder">
  <owl:sameAs rdf:resource="ProfessorStuder"/>
</rdf:Description>
```

- declare different individuals with `owl:differentFrom`:
```
<rdf:Description rdf:about="RudiStuder">
  <owl:differentFrom rdf:resource="YorkSure"/>
</rdf:Description>
```


- to declare diversity of a set of individuals use `owl:AllDifferent` and `owl:distinctMembers`:

```
<owl:AllDifferent>
  <owl:distinctMembers rdf:parseType="Collection">
    <Person rdf:about="RudiStuder"/>
    <Person rdf:about="YorkSure"/>
    <Person rdf:about="PascalHitzler"/>
  </owl:distinctMembers>
</owl:AllDifferent>
```

#### Inference (individuals)
##### 1. `ProfessorStuder` is a `professor`
```
<professor rdf:about="RudiStuder"/>
<rdf:Description rdf:about="RudiStuder">
  <owl:sameAs rdf:resource="ProfessorStuder"/>
</rdf:Description>
```

##### 2. `SemanticWebBasics` is a `publication`
```
<book rdf:about="SemanticWebBasics">
  <author rdf:resource="YorkSure"/>
  <author rdf:resource="PascalHitzler"/>
</book>

<owl:Class rdf:about="book">
  <rdfs:subClassOf rdf:resource="publication"/>
</owl:Class>
```

### Logical Constructors on Classes
- allow representation of more complex knowledge and relationships: conjunction, disjunction and negation (logical operators)
  - `owl:intersectionOf`, `owl:unionOf` and `owl:complementOf`
- can be arbitrarily nested

####  `owl:intersectionOf`
- conjunction of two classes
- logical operator AND
```
<owl:Class rdf:about="SecretariesOfStuder">
  <owl:intersectionOf rdf:parseType="Collection">
    <owl:Class rdf:about="secretaries"/>
    <owl:Class rdf:about="MembersWGStuder"/>
  </owl:intersectionOf>
</owl:Class>
```
- `SecretariesOfStuders` contains instances, which are `secretaries` and `MemberWGStuder` at the same time

####  `owl:unionOf`
- disjunction of two classes
-logical operator OR
```
<owl:Class rdf:about="professor">
  <rdfs:subClassOf>
    <owl:unionOf rdf:parseType="Collection">
      <owl:Class rdf:about="activelyTeaching"/>
      <owl:Class rdf:about="retired"/>
    </owl:unionOf>
  </rdfs:subClassOf>
</owl:Class>
```
- `professor` is actively teaching or retired (or both)
- in combination with `rdfs:subClassOf`: at least one (`activelyTeaching` or `retired`) must be given

#### `owl:complementOf`
- negation
- logical operator NOT 
```
<owl:Class rdf:about="faculty member">
  <rdfs:subClassOf>
    <owl:complementOf rdf:resource="publication"/>
  </rdfs:subClassOf>
</owl:Class>
```
- no `faculty member` is a `publication`
- synonym to `owl:disjointWith`

### Property Restrictions and Cardinality
- `owl:allValuesFrom`: all examiners must be `professor`s
- `owl:someValuesFrom`: at least one examiner must be a `professor`
```
<owl:Class rdf:about="exam">
     <rdfs:subClassOf>
          <owl:Restriction>
               <owl:onProperty rdf:resource="hasExaminer"/>
               <owl:allValuesFrom rdf:resource="professor"/>
          </owl:Restriction>
     </rdfs:subClassOf>
</owl:Class>
```

#### `owl:maxCardinality`
- set maximum
- a maximum of two examiners for an exam
```
<owl:Class rdf:about="exam">
  <rdfs:subClassOf>
    <owl:Restriction>
      <owl:onProperty rdf:resource="hasExaminer"/>
      <owl:maxCardinality rdf:datatype="&xsd;nonNegativeInteger">
      2
      </owl:maxCardinality>
    </owl:Restriction>
  </rdfs:subClassOf>
</owl:Class>
```

#### `owl:minCardinality`
- set minimum
- exam must at least contain three topics
```
<owl:Class rdf:about="exam">
  <rdfs:subClassOf>
    <owl:Restriction>
      <owl:onProperty rdf:resource="containsTopic"/>
      <owl:minCardinality rdf:datatype="&xsd;nonNegativeInteger">
      2
      </owl:minCardinality>
    </owl:Restriction>
  </rdfs:subClassOf>
</owl:Class>
```

#### `owl:cardinality`
- set exact number
- exam must contain exactly three topics
```
<owl:Class rdf:about="exam">
  <rdfs:subClassOf>
    <owl:Restriction>
      <owl:onProperty rdf:resource="containsTopic"/>
      <owl:cardinality rdf:datatype="&xsd;nonNegativeInteger">
      3
      </owl:cardinality>
    </owl:Restriction>
  </rdfs:subClassOf>
</owl:Class>
```
#### `owl:hasValue`
- set exact value for property
- does not exclude the possibility, that there are other examiner besides `RudiStuder`
```
<owl:Class rdf:about="examWithStuder">
  <rdfs:equivalentClass>
    <owl:Restriction>
      <owl:onProperty rdf:resource="hasExaminer"/>
      <owl:hasValue rdf:resource="RudiStuder"/>
    </owl:Restriction>
  </rdfs:equivalentClass>
</owl:Class>
```

### Property Relations
- define relation between properties

#### `rdfs:subPropertyOf`
- someone is examiner and therefore also an attendant:
```
<owl:ObjectProperty rdf:about="hasExaminers">
  <rdfs:subPropertyOf rdf:resource="hasAttendants"/>
</owl:ObjectProperty>
```

#### `rdfs:equivalentProperty`
```
<owl:ObjectProperty rdf:about="hasChildren">
  <rdfs:equivalentProperty rdf:resource="hasKids"/>
</owl:ObjectProperty>
```

#### `owl:inverseOf`
- roles can be inverse
- same relation with exchanged arguments
```
<owl:ObjectProperty rdf:about="hasExaminer">
  <owl:inverseOf rdf:resource="isExaminer"/>
</owl:ObjectProperty>
```

### Property Characteristics
- transitivity, symmetry, functionality and inverse functionality

```
<owl:ObjectProperty rdf:about="hasCollegue">
     <rdf:type rdf:resource="&owl;TransitiveProperty"/>
     <rdf:type rdf:resource="&owl;SymmetricProperty"/>
</owl:ObjectProperty>
     <owl:ObjectProperty rdf:about="hasProjectLeader">
     <rdf:type rdf:resource="&owl;FunctionalProperty"/>
</owl:ObjectProperty>
<owl:ObjectProperty rdf:about="isProjectLeaderOf">
     <rdf:type rdf:resource="&owl;InverseFunctionalProperty"/>
</owl:ObjectProperty>
<person rdf:about="YorkSure">
     <hasCollegue rdf:resource="PascalHitzler"/>
     <hasCollegue rdf:resource="AnupriyaAnkolekar"/>
     <isProjectLeaderOf rdf:resource="StudentProject"/>
</person>
<project rdf:about="SmartWeb">
     <hasProjectLeader rdf:resource="PascalHitzler"/>
     <hasProjectLeader rdf:resource="HitzlerPascal"/>
</project>
```

#### Symmetry
- if A is in relation to B, B is also to A
```
YorkSure hasCollegue ÀnupriyaAnkolekar
ÀnupriyaAnkolekar hasCollegue YorkSure
```

#### Transitivity
- if A is in relation to B and B in relation to C, then A is in a relation to C
```
AnupriyaAnkolekar hasCollegue YorkSure
YorkSure hasCollegue PascalHitzler

so:

AnupriyaAnkolekar hasCollegue PascalHitzler
```
#### Functionality
- if A is in relation to B and A also to C, then B and C are equal, same as in `owl:sameAs`
- since `hasProjectLeader` is functional, `PascalHitzler` and `HitzlerPascal` are the same

#### Inverse Functionality
- inverse functionality of a property R: property inverse to R is functional

### Open World Assumption (OWA)
- assumption that knowledge base is potentially always incomplete
- in contrast to Closed World Assumption
- useful, since WWW is constantly expanding
  - new knowledge, which add to the current knowledge base
```
<person rdf:about="Anton">
  <likesToWorkWith rdf:resource="Doris"/>
  <likesToWorkWith rdf:resource="Dagmar"/>
</person>

<person rdf:about="Doris">
  <likesToWorkWith rdf:resource="Dagmar"/>
  <likesToWorkWith rdf:resource="Bernd"/>
</person>

<person rdf:about="Gustav">
  <likesToWorkWith rdf:resource="Bernd"/>
  <likesToWorkWith rdf:resource="Doris"/>
  <likesToWorkWith rdf:resource="Desiree"/>
</person>

<person rdf:about="Charles"/>

<owl:Class rdf:about="femaleCollegues">
  <owl:oneOf rdf:parseType="Collection">
    <person rdf:about="Dagmar"/>
    <person rdf:about="Doris"/>
    <person rdf:about="Desiree/>
  </owl:oneOf>
</owl:Class>


<owl:Class rdf:about="class1">
<rdfs:equivalentClass>
    <owl:Restriction>
      <owl:onProperty rdf:resource="likesToWorkWith"/>
      <owl:someValuesFrom rdf:resource="femaleCollegues"/>
    </owl:Restriction>
  </rdfs:equivalentClass>
</owl:Class>
```
- Anton, Doris and Gustav can be assigned to `class1`
- one cannot conclude that Charles is in `class1`
- one can *assume* that Charles could be in relation `likesToWorkWith` with an instance of the class `femaleCollegues`, but there is no proof


## Sources
1. P. Hitzler, M. Krötzsch, S. Rudolph und Y. Sure, Semantic Web: Grundlagen. Berlin: Springer,
2008, isbn: 978-3-540-33993-9. doi: 10.1007/978-3-540-33994-6

2. B. Grimm. Semantic Web Grundlagen OWL - Syntax und Intuition. https://www.uni-ulm.de/fileadmin/website_uni_ulm/iui.inst.090/Lehre/WS_2011-2012/SemWebGrundlagen/v08, 2011. [abgerufen am 27.10.2023]

3. What are Ontologies?. https://www.ontotext.com/knowledgehub/fundamentals/what-are-ontologies/ [abgerufen am 27.10.2023]