# Chapter 1: Overview of Database System

## Concepts

### Data

- information (facts / numbers)
- stored electronically or recorded
- not organized to have any meaning

### Information

### Knowledge

### Metadata

### Database

## File Processing Systems

## The database approach

## Data models

## Database Management Systems

## Database systems

## Applications of database systems

# Chapter 2: The entity-relationship Model

## Database Design process from conceptual modeling

- 4 main phases:
  - Requirements collection and analysis (ex: database designers)
  - Conceptual design (ex: the entity-relationship model)
  - Logical design - data model mapping (ex: relational data model)
  - Physical design

From the miniworld, we execute "Requirements collection and analysis" to get requirements from users and environment (func/non-func requirements). This requirement consists of 2 types: Functional requirements and Data requirements. 

- For functional requirement, we will do "Functional Analysis" to determine what kinds of transactions will be executed - "High-level Transaction Specification". This specification about transaction will be fed into: Application Program Design (app-related path) and Physical Design (data-related path). At the step of Application Program Design, a DBMS must be specified so that the backend of both path can develop on. In this step, transaction specifications and logical schema will be used to design our application. Combining with internal schema of the database, we get to "Transaction Implementation" which has the final product is Application Programs
- For data requirements, we develop "Conceptual Design" for determinining entity-relationship as in Conceptual Schema. We then determine the DBMS in the "Logical Design" step. From the Logical Schema, we then create our Physical Design - backbone of our database - internal schema.

## Conceptual Data modeling

- Data modeling: representing data structure - design activity: arranging structure and relationship of data

### Purpose of Data Modeling

- Leverage: neat organization
- Conciseness: directly to the business requirements
- Data quality: consistency in defining data, implementing for definitions ~ create common understanding of each attributes

### Semantic data model

- User-friendly concepts
- Carry application concepts
- For building conceptual schema from data requirements - entity-relationship model

### Conceptual data model

- Expressiveness: distinctions between data, relationship, constraints
- Simplicity: user-friendly in diagram format
- Minimality: use small and basic concepts
- Formality: formal concepts - to determine if the schema is valid or not
- Unique interpration: only 1 meaning

### Logical data model

- Understood by users but for representing database structure (data types, relationships, constraints, operations for transactions)
- Hide details but can be implement directly for some DBMS (relational data model - interaction between tables)

### Database design

- Design logical and physical structures of databases according to users' needs
- Undergo design methodology (Top Down Design, Stepwise Refinement, Bottom Up Design, etc.)
- Define a database schema (should not be replaced later)

#### Goals

- Satisfy user/application requirements (both data and processing~non-func requirements)
- Understandable info structure (diagram)

#### Phase 1: Requirement Collection and Analysis

- Identify application areas
- Study application-related documentations (maybe from customers)
- Study operation environment
  - transactions type / frequencies / info flow
  - I/O format
  - etc.
- Collect written responses from customers
- Understand users as much as possible

#### Phase 2: Conceptual Database design

##### Phasae 2a: Conceptual Schema design

- Figure out database structure, meaning, relationships, constraints
  - Via entity, relationships, attributes ...
- 2 approaches: **centralized** and **view integration**
- Centralized / one-shot schema design
  - requirements of everyone get merged into one before schema design
  - database admin responsible aabout how to merge requirements and the conceptual schema design
  - After the conceptual schema is finished, external schema is extended by dtb admin for each group
  - ~ merge then un-merge
- View integration approach
  - Design schema for each unmerged requirements
  - Then merge these schema into global conceptual schema via dtb admin
  - ~ can un-merge again for some individual views

#### Phase 3: Choice of a DBMS

- Technical factors:
  - DBMS type
  - DBMS's storage structure, UI, query language, etc.
  - DBMS portability for different hardware
- Non-technical factors:
  - cost
  - third-party/vendor services add-on

#### Phase 4: Data model Mapping (Logical Database design)

- Create conceptual schema and external schema
- create DDL statements of DBMS language which specify conceptuaal and external level schema

#### Phase 5: Physical Database design

- Choose most suitable DBMS with structures (storage structure, access path, response time, space util, transaction throughput)
- Estimate record size and length
- Estimate query pattern
- Estimate growth

## The entity-relationship model

## The extended entity-relationship model

