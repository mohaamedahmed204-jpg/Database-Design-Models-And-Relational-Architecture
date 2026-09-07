# 🗄️ Database Design Models & Relational Architecture 🚀

Welcome to the **Database Design Models & Relational Architecture** repository! This project serves as a comprehensive visual and structural guide to core relational database design concepts. It covers everything from conceptual ER Diagram (ERD) modelling and relational schema mappings to structural normalisation and real-world sample dataset representations.

---

## 📌 Overview

This repository provides an end-to-end reference for understanding how conceptual entity-relationship models translate into physical, highly structured relational databases. 

Through a series of detailed design diagrams (`.drawio`), this project demonstrates:
* **Unary / Unary-Recursive Relationships**: Modeling self-referencing entities (e.g., employee-manager hierarchies).
* **Multi-Valued Attributes**: Handling attributes with multiple values using dedicated bridge/lookup tables.
* **1:1 Relationships & Foreign Key Constraints**: Securing one-to-one entity associations via key mapping.
* **1:N & N:M Complex Relationships**: Breaking down many-to-many associations using junction (associative) tables with composite keys.
* **Inheritance & Subtyping (IS-A Patterns)**: Implementing OOP-style class inheritance inside relational structures.
* **Ternary Relationships**: Structuring multi-entity dynamic operational workflows (e.g., Student-Course-Teacher enrollment).

---

## ⚡ Core Operations in Detail

### 1️⃣ Unary / Self-Referential Mapping (Hierarchy & Management)
* **Concept**: Entities that relate to other instances within the same table.
* **Operations**:
  * Models hierarchical organizational structures (e.g., `Employees` and their `Managers`).
  * Uses a self-referencing foreign key (`ManagerID`) referencing the primary key (`EmpID`) within the `Employees` table.
  * Facilitates recursive SQL queries (e.g., `WITH RECURSIVE`) to trace organizational trees and managerial chains.

### 2️⃣ Handling Multi-Valued Attributes (1-to-Many Normalization)
* **Concept**: Storing non-atomic attributes (e.g., multiple phone numbers or language proficiencies for a single person).
* **Operations**:
  * Prevents 1NF violations by separating multi-valued attributes into standalone entity tables (`Phones`, `Languages`).
  * Links secondary tables to the primary entity (`Student`) via Foreign Keys (`StudentID`).
  * Ensures efficient querying, scaling, and constraint enforcement without string splitting or redundant column additions.

### 3️⃣ One-to-One (1:1) Key Attachment
* **Concept**: Strict 1-to-1 association where an entity maps uniquely to another single entity.
* **Operations**:
  * Examples: An `Employee` possessing a single security `AccessCard`.
  * Implemented by attaching the Primary Key of one table (`CardID`) as a Foreign Key (with a `UNIQUE` constraint) inside the related table (`Employees`).
  * Ensures data integrity and enforces tight 1:1 hardware/credential allocation rules.

### 4️⃣ One-to-Many (1:N) Relationship Mapping
* **Concept**: A single record in one entity corresponds to multiple records in a secondary entity.
* **Operations**:
  * Example: A `Department` hosting multiple `Employees`.
  * The Primary Key (`DeptID`) of the parent table (`Department`) is embedded as a Foreign Key in the child table (`Employee`).
  * Supports cascading actions (`ON DELETE SET NULL` or `ON DELETE CASCADE`) to preserve referential integrity.

### 5️⃣ Many-to-Many (N:M) & Associative Entities
* **Concept**: Multiple records in Entity A correspond to multiple records in Entity B.
* **Operations**:
  * Example: `Students` enrolling in `Courses`.
  * Resolved by introducing an associative table (`Enrolled` / `Enrollments`).
  * Maps Foreign Keys (`StudentID`, `CourseID`) alongside relationship-specific payload attributes such as `EnrollDate` and `Grade`.

### 6️⃣ Subtyping & Specialization (IS-A Hierarchies)
* **Concept**: Modeling object-oriented inheritance within relational databases.
* **Operations**:
  * Base class table `Person` (contains `PersonID`, `FirstName`, `LastName`, `BirthDate`).
  * Derived sub-tables `Employee` (`EmpID`, `Salary`, `FK PersonID`) and `Secretary` (`SecID`, `TypingSpeed`, `FK EmpID`).
  * Implements table-per-type inheritance, minimizing NULL fields and separating domain-specific behavior.

### 7️⃣ Ternary (3-Way) Relationship Modeling
* **Concept**: Associations connecting three independent entities simultaneously.
* **Operations**:
  * Connects `Student`, `Course`, and `Teacher` into a central `Enrolled` transaction engine.
  * Features composite/unique constraints over `StudentID`, `CourseID`, and `TeacherID`.
  * Tracks historical metrics such as execution date and evaluation scores per unique instructor-course combination.

---

## 🔑 Key Concepts Demonstrated

| Concept | Description |
| :--- | :--- |
| **Referential Integrity** | Enforcing strict Foreign Key relationships across all normalized tables. |
| **Database Normalization** | Eliminating insertion, update, and deletion anomalies through 1NF, 2NF, and 3NF design principles. |
| **Composite Keys & Junctions** | Deconstructing complex relations using associative entity mappings. |
| **Entity Specialization** | Mapping object inheritance (`IS-A` patterns) cleanly to relational schemas. |
| **Attribute Atomic Scope** | Resolving multi-valued properties into scalable, relational child tables. |

---

## 🏗️ Architecture & Design

The repository architecture follows a 3-Tier Database Design Methodology:
    
    +-------------------------------------------------------+
    |                1. Conceptual Model                    |
    |       (Entity-Relationship Diagrams / ERDs)           |
    +-------------------------------------------------------+
                              │
                              ▼
    +-------------------------------------------------------+
    |                 2. Logical Model                      |
    |         (Relational Schemas, PK/FK Mapping)           |
    +-------------------------------------------------------+
                              │
                              ▼
    +-------------------------------------------------------+
    |                3. Physical Dataset                    |
    |      (Sample Tables, Mock Data, Field Constraints)    |
    +-------------------------------------------------------+


### 📁 File Naming & Module Mapping
* **`DB Design 1`**: Self-referential / Unary Management Hierarchy (`Employees` → `ManagerID`).
* **`DB Design 2`**: Multi-valued Attribute Normalization (`Phones`, `Languages`).
* **`DB Design 3`**: One-to-One (1:1) Security Access Mapping (`Employee` ↔ `AccessCard`).
* **`DB Design 4`**: One-to-Many (1:N) Organizational Structure (`Employee` ↔ `Department`).
* **`DB Design 5`**: Many-to-Many (N:M) Academic Enrollment (`Student` ↔ `Course`).
* **`DB Design 6`**: Specialization / Subtyping Hierarchy (`Person` → `Employee` → `Secretary`).
* **`DB Design 7`**: Ternary Relational Execution Engine (`Student` ↔ `Course` ↔ `Teacher`).

---

## 🛠️ Technologies & Tools

* **Diagramming & Design**: Draw.io / Diagrams.net (`.drawio`)
* **Modeling Methodologies**: Entity-Relationship Diagramming (ERD), Crow's Foot Notation, UML
* **Database Management Standards**: Relational Database Management Systems (RDBMS) / SQL Standards
* **Documentation**: Markdown, HTML/CSS layout wrappers

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

This project is part of the Programming Advices Training Track led by:

    👨‍🏫 Dr. Mohamed Abouhadhood
    💻 Platform: Programming Advices
