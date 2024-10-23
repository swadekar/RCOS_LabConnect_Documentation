# Entity-Relationship Diagrams (ERDs)

Entity-relationship (ER) modeling is a flexible technique for designing databases that provides a high-level overview of the entire database structure. ER diagrams depict the entities involved and the relationships between them. This process is both iterative and visual, emphasizing an object-oriented approach. Data modeling blends scientific methodology with creative design.

## Entities

Entities represent **classes of objects** stored in the database. Their names are typically nouns and plural, and they consist of various attributes.

- **Key Requirement**: Each entity must possess a unique key. A **natural key** is preferred over a synthetic one, with synthetic keys introduced only when necessary.

- **Normalization**: Entities should ideally conform to **Boyce-Codd Normal Form (BCNF)** or, at minimum, **Third Normal Form (3NF)**.

- **Representation**: Entities are generally illustrated as rectangles.

### Entity Attributes

Attributes are characteristics associated with entities. All attributes should be simple and relevant only to the entity they describe.


- **Representation**: Attributes are depicted as ellipses and connected to their respective entities by straight lines. Attributes that are part of a key are underlined.

### Attribute vs. Entity

Attributes are meant to describe entities. If an item does not characterize an entity, it should be treated as a weak entity, regardless of how it appears to be an attribute.

## Relationships

Relationships outline how entities are interconnected. When you see a verb, it often indicates a relationship.

- **Binary Relationships**: These connect two entities and are the most common type. Relationships involving more than two entities are rare.

- **Participation Constraints**: Some relationships dictate that one entity may relate to a specific number of instances of another entity.

  - **Cardinality**: Defines the number of instances of one entity that can relate to another.
    - **One-to-Many**: One entity relates to multiple entities.
    - **One-to-One**: One entity relates to exactly one entity.
    - **Many-to-Many**: Multiple entities relate to multiple entities.
    - **Recursive Relationships**: Connect an instance of an entity to another instance of the same entity.

### Relationship Attributes

Relationships can have zero or more attributes that characterize them, but they do not have a key.

- **Representation**: Relationships are typically represented as diamonds, connected to entities with straight lines. The relationship name should feel intuitive, and participation constraints can be illustrated next to the line or as arrowheads.


### Ternary Relationships

These involve three distinct entities. When determining participation constraints, consider the pairs of attributes: for a specific instance of A and B, there may be zero, one, or multiple instances of C.

### Weak Entities

A weak entity contains a key and a set of attributes, but its key is not unique within the database, requiring support.

- **Supporting Entities**: These assist a weak entity through many-to-one relationships.

  - The combined key of the weak entity and the supporting entities ensures uniqueness within the database.
  - Supporting relationships are illustrated with double lines.


### Entity Subclasses

Entities of similar types can be organized in a hierarchical structure. Attributes and keys are inherited from the parent entity.

## Mapping ER Diagrams to the Relational Model

Converting an ER Diagram into a relational model requires a systematic approach for clarity:

1. **Convert Entities**: Each entity translates into a relation. Map the entity name as the relation's name, assign the entity key as the relation's key, and list all other attributes.

2. **Convert Weak Entities**: A weak entity and its supporting relationships form a new relation. 
   - The relation takes the weak entity's name and attributes.
   - The key consists of the weak entity's key combined with the keys from all supporting entities.
   - **Example**: If "Album" (key: AlbumId) supports "Tracks" (weak key: TrackId, along with other attributes), the resulting relation is `Tracks(AlbumId, TrackId, other attributes)`, with the key being `(AlbumId, TrackId)`.

3. **Convert Relationships Based on Cardinality**:
   - **One-to-Many**: Map to the "many" side entity, which includes keys from the "one" side in its attributes.
     - **Example**: If one B relates to many As: 
       - `A(keyForA, attributesForA, keyForB)` with key `keyForA`
       - `B(keyForB, attributesForB)` with key `keyForB`
   - **One-to-One**: Either entity can include the other's key in its attributes. Prefer the entity with cardinality of always 1 to include the key of the other.
   - **Many-to-Many**: Create a new relation to connect the entities, including keys from all participating entities. This new relation's key must encompass the keys from entities with N participation.
   - **Add Relationship Attributes**: Include any relationship-specific attributes to the mapped relation.

4. **Convert Entity Hierarchies**:
   - **Option 1**: Create separate relations for each subclass entity (if the hierarchy is covering, the parent entity may not need a separate relation).
     - **Pros**: Precise representation. 
     - **Cons**: Redundant information across multiple entities.
   - **Option 2**: Convert the parent entity into its relation and create new relations for each subclass, listing only unique attributes.
     - **Pros**: No repeated data.
     - **Cons**: Requires multiple joins to retrieve complete information.
   - **Option 3**: Flatten the hierarchy into a single entity, adding attributes to identify the class of each entity.
     - **Pros**: Minimizes joins.
     - **Cons**: Can waste space with many empty attributes; may lack elegance and modularity.
