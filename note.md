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

#### Phase 6: Database System Implementation and Tuning

- Create dtb schema with empty files - dtb admin
- Reformat for load new dtb if needed
- Implement transaction / test
- Tuning continues with new requirements

## The entity-relationship model

- Natural view of realworld entities, relationships, attributes
- Data independce + set theory, relation theory
- Provide unified view of data
- entity-relationship diagram is a tool for dtb design

- Entity set: collection of entities of an entity types
- Key attribute: value are distinct for each entity in entity set - identify - unique
  - could be formed with several attributes
- Complex attribute: Composite and multivalued ~ denoted using multivalued symbol
- Weak entity type: entity types that don't have key attribute of their own

## The enhanced entity-relationship model

- Specialization
  - Define subclass (with new attributes / relationships for each)
- Generalization
  - Supress difference among class - merge into 1 parent class
- Union types
- Disjoint (d): subclass must be disjoint (no entity in common)
- Overlapping (o): not constraint to be disjoint

# Chapter 3: The Relational Data Model

## Concepts

Data model = data structure type + operators + integrity rule

### Schema-based (explicit) constraints

#### Domain constraints

Within each tuple, each attribute A must be an atomic value from dom(A) (domain)

#### Key constraints

- Key uniqueness ~ minimal superkey
- Can have more than 1 key (candidate keys: primary key and secondary keys)

#### Entity integrity constraints

No primary key value can be NULL

#### Referential integrity constraint

Between 2 relation schema R1 and R2
Foreign key (a set of attributes) of R1 that references R2:
- dom(FK,R1) = dom(PK,R2)
- FK can be null

## Relation Schemas relations

## Mapping an entity-relationship schema into a relational dtb schema

| ER Model | Relational Model |
|---|---|
| Entity type | Entity relation |
| 1:1 or 1:N relationship type | Foreign key (or relationship relation) |
| M:N relationship type | relationship relation and 2 foreign keys |
| n-ary relationship type | relationship relation and n foreign keys |
| simple attribute | attribute |
| composite attribute | set of simple component attributes |
| Multivalued attribute | relation and foreign key |
| value set | domain |
| key attribute | Primary/secondary key |

### Step 1: Mapping of Regular Entity type

- Create relation R of entity type E with all atributes of E (only simple component of a composite attribute)
- Choose one of the primary key of E as of R (if it is composite in E -> convert into set in R)

### Step 2: Mapping of Weak Entity Type

- For weak entity type W of owner E, create R include all simple attributes (if it is composite -> split into all simple) as attributes of R
- Primary key = PK of owner + partial key of W
- FK = PK of owner

### Step 3: Mapping of Binary 1:1 Relationship Types

- Foreign key approach: choose S (better to chose one with total participation) FK of S includes PK of T. All simple attributes of R will be attributes of S
- Merged relation approach: merge 2 entity type (possible when both are total participation)
- Cross-reference or relationship relation approach: set up new R for cross-ref PK of S and T (required for M:N relationship). R can be called lookup-table. FK(R_S), FK(R_T) = PK(S), PK(T). PK(R) can be either of the FK(R) and the other is unique key - this will need extra join operation

## The relational algebra

