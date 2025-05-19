# Employee-Management-System - Oracle SQL

This project is a comprehensive **Human Resource Management System** built entirely using **Oracle SQL**. It includes a normalized relational schema, advanced PL/SQL procedures, triggers, views, indexes, and a data population script. The goal is to demonstrate the design and implementation of a live HR database that models real-world employee, organization, and role-based data.

---

## 🗂️ Database Structure

The schema consists of the following core entities:

- `ADDRESS_TYPE`
- `EMPLOYEE_TYPE`
- `EMPLOYEE_ROLE`
- `ORGANIZATION`
- `PERSON`
- `EMPLOYEE`

These are interrelated through primary/foreign key constraints to maintain data integrity.

---

## ⚙️ Key Features

### 🔁 Triggers
- `update_person`: Ensures no person under 18 can be inserted or updated into the `PERSON` table.

### 📦 PL/SQL Package
**`HR_PACKAGE`** encapsulates all major operations, including:

- Insert procedures for all tables
- Business logic validation
- Utility procedures:
  - `DeleteAllObjects` — dynamically drops tables, views, and procedures in the schema
  - `DESCRIBER` — prints column metadata for all major tables
- Utility functions:
  - `get_employee_full_name(emp_id)`
  - `get_role_name(role_id)`

### 👀 Views
- `EMPLOYEE_DETAILS`: A consolidated view showing personal, employment, and organizational details in a readable format.

### 📊 Indexes
- `IDX_ID`: Index created on `EMPLOYEE(PERSON_ID)` to speed up joins and searches.

---

## 🧪 Sample Data

The script inserts:
- 3 address types
- 3 employee types
- 3 employee roles
- 3 organizations
- 15 persons and their corresponding employee records

This data is programmatically inserted using loops and conditional logic to simulate diversity across records.

---

## 📄 Example Query

```sql
SELECT First_Name, COUNT(*) 
FROM EMPLOYEE_DETAILS 
GROUP BY First_Name 
HAVING COUNT(*) > 2;
