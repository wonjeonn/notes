# Week 8: Entity Relationship Model (ERM)

## Entity Relationship Model (ERM)
- Basis of an entity relationship diagram (ERD).
- ERD depicts the conceptual database as viewed by end users, including its main components:
  - Entities
  - Attributes
  - Relationships
- **"Entity"** refers to the entity set, not to a single entity occurrence.

## Table-Oriented DBMS

| Relational Model | Table-Oriented DBMS | Conventional File Systems | Conceptually Represents  |
|------------------|---------------------|---------------------------|--------------------------|
| Relation         | Table               | File                      | Entity Type              | 
| Tuple            | Row                 | Record                    | Entity Instance          | 
| Attribute        | Column              | Field                     | Property                 | 
| Domain           | Column Type         | Data Type                 | Allowable Values         | 
| Element          | Column Value        | Field Value               | Property Value           | 

## Attributes
- **Required Attribute (e.g., "Birthdate" in a "Person" entity):** Must have a value, cannot be left empty.
- **Optional Attribute (e.g., "Middle Name" in a "Person" entity):** Does not require a value, can be left empty.
- **Domain (e.g., "Gender" in a "Person" entity):** A domain is the set of possible values for an attribute. For instance, "Gender" can have values like "Male," "Female," and "Other."
- **Identifiers (e.g., "StudentID" and "SocialSecurityNumber" in a "Student" entity):** Identifiers are one or more attributes that uniquely identify each entity instance.
- **Composite Identifier (e.g., "CategoryCode" and "ProductCode" in a "Product" entity):** A composite identifier is a primary key composed of more than one attribute.
- **Composite Attribute (e.g., "Address" in a "Customer" entity):** A composite attribute is an attribute that can be subdivided to yield additional attributes, like "Street," "City," "State," and "Zip Code."
- **Simple Attribute (e.g., "Age" in a "Person" entity):** A simple attribute is an attribute that cannot be subdivided.
- **Single-Valued Attribute (e.g., "DateOfBirth" in a "Customer" entity):** A single-valued attribute is an attribute that has only a single value.
- **Multivalued Attributes (e.g., "PhoneNumbers" in a "Contact" entity):** Multivalued attributes are attributes that can have multiple values, such as "Home," "Work," and "Mobile" phone numbers.

## Multivalued Attributes
- Attributes that have many values.
- May require creating several new attributes, one for each component of the original multivalued attribute or a new entity composed of the original multivalued attribute's components.

## Derived Attributes
- Attributes whose values are calculated from other attributes using an algorithm (e.g., "Age" calculated from "Birthdate").
- Advantages and disadvantages of storing derived attributes.

## Relationships
- Associations between entities that operate in both directions.
- **Participants:** Entities that participate in a relationship.
- **Connectivity:** Describes the relationship classification.
- **Cardinality:** Expresses the minimum and maximum
number of entity occurrences associated with one
occurrence of related entity.

## Existence Dependence
- **Existence Dependence:** Entity exists in the database only when associated with another related entity occurrence.
  - **Example:** In a "Dependent" entity, a dependent's existence depends on being associated with an "Employee." If there's no related employee, there's no dependent.
- **Existence Independence:** Entity exists apart from
all of its related entities. "Strong entities" exist independently of related entities.
  - **Example:** A "Customer" entity is existence-independent in a sales database. It can exist on its own and its existence is not dependent on any particular sales transaction.

## Relationship Strength
- **Weak (non-identifying) relationship:** Primary key of the related entity does not contain a
primary key component of the parent entity.
  - **Example:** In an "Order Line" entity, the "Product" entity is weakly related because the "Order Line" can exist without a product. The product's primary key does not include the order line's key.
- **Strong (identifying) relationship:** Primary key of the related entity contains a primary key
component of the parent entity.
  - **Example:** In a "Library Book" entity, the "Book Copy" entity is strongly related because each book copy's primary key includes the book's ISBN, making the book copy's existence dependent on the book's existence.

## Weak Entity
- **Conditions:**
  - **Existence-dependent.**
  - **Has a primary key partially or totally derived from the parent entity in the relationship.**
- **Database designer determines whether an entity is weak based on business rules.**
  - **Example:** In a "Dependent" entity, if the primary key is a combination of "EmployeeID" and "DependentID," and the "Dependent" entity can only exist when associated with an "Employee," it's a weak entity.

## Relationship Participation
- **Optional participation:** One entity occurrence does not require a corresponding entity occurrence in a particular relationship.
  - **Example:** In a "Supplier" and "Product" relationship, a supplier can exist without supplying any product. Optional participation allows for this scenario.
- **Mandatory participation:** One entity occurrence requires a corresponding entity occurrence in a particular relationship.
  - **Example:** In a "Customer" and "Order" relationship, a customer cannot place an order without being part of an order. Participation is mandatory in this case.

## Relationship Degree
- **Unary relationship:** Association is maintained within a single entity.
  - **Example:** In a "Person" entity, a unary relationship could represent "Spouse" where a person is related to another person as their spouse.
- **Recursive relationship:** Exists between occurrences of the same entity set.
  - **Example:** In an "Employee" entity, a recursive relationship could represent "Supervisor" where an employee supervises other employees.
- **Binary relationship:** Two entities are associated.
  - **Example:** In a "Student" and "Course" relationship, a student enrolls in a course, involving two entities.
- **Ternary relationship:** Three entities are associated.
  - **Example:** In a "Doctor," "Patient," and "Diagnosis" relationship, a doctor diagnoses a patient's condition.

## Associative (Composite) Entities
- Used to represent M:N relationships between two or more entities.
  - **Example:** In a "Student" and "Course" relationship, an "Enrollment" entity can be used to represent the many-to-many relationship with additional attributes like enrollment date.

## Components of the ERM

| ENTITY          | RELATIONSHIP       | CONNECTIVITY | ENTITY      |
|-----------------|--------------------|--------------|-------------|
| SCHOOL          | operates           | 1:M          | DEPARTMENT  |
| DEPARTMENT      | has                | 1:M          | STUDENT     |
| DEPARTMENT      | employs            | 1:M          | PROFESSOR   |
| DEPARTMENT      | offers             | 1:M          | COURSE      |
| COURSE          | generates          | 1:M          | CLASS       |
| SEMESTER        | includes           | 1:M          | CLASS       |
| PROFESSOR       | is dean of         | 1:1          | SCHOOL      |
| PROFESSOR       | chairs             | 1:1          | DEPARTMENT  |
| PROFESSOR       | teaches            | 1:M          | CLASS       |
| PROFESSOR       | advises            | 1:M          | STUDENT     |
| STUDENT         | enrolls in         | M:N          | CLASS       |
| BUILDING        | contains           | 1:M          | ROOM        |
| ROOM            | is used for        | 1:M          | CLASS       |

The "ENROLL" entity is a composite entity that implements the many-to-many (M:N) relationship "STUDENT enrolls in CLASS."

## Developing an ER Diagram
- Create a detailed narrative of the organization’s description of operations.
  - **Example:** In a university database, describe how courses, students, professors and departments interact.
- Identify business rules based on the descriptions.
  - **Example:** Define rules like "A course can be offered by multiple departments."
- Identify main entities and relationships from the business rules.
  - **Example:** Identify "Student," "Course," "Professor," and their relationships.
- Develop the initial ERD.
  - **Example:** Create an initial diagram showing entities, attributes and relationships.
- Identify the attributes and primary keys that adequately describe entities.
  - **Example:** For the "Student" entity, attributes like "StudentID," "Name," and "Birthdate" are identified.
- Revise and review ERD.
  - **Example:** Review the ERD to ensure it accurately represents the organization's requirements, making revisions as needed.

## Database Design
- Database design must conform to design standards.
- Balancing processing speed, clean design structures, information generation and transaction speed.
