<img width="622" height="404" alt="image" src="https://github.com/user-attachments/assets/5f73f668-1e7d-4eab-a178-a07755ae08d1" />

# Functional Dependency in DBMS

## 1. Definition

**English Definition:**

A Functional Dependency is a relationship between two attributes (columns) in a database table where one attribute uniquely determines the value of another attribute.

**Simple English:**

If we know the value of one column, we can uniquely identify the value of another column.

**বাংলা অর্থ:**

একটি Column-এর Value জানা থাকলে অন্য একটি Column-এর Value uniquely identify করা গেলে তাকে Functional Dependency বলে।

## 2. Functional Dependency Notation

Functional Dependency is represented as:

<img width="389" height="209" alt="image" src="https://github.com/user-attachments/assets/7f3ecc11-9e0e-48cd-8557-1323a1dadb72" />

Where:

- **X:** Determinant (নির্ধারক Attribute)
- **Y:** Dependent Attribute (নির্ভরশীল Attribute)
- **→:** Functionally determines

It means X determines Y.

## 3. Example

Consider the following Student table:

| Student_ID | Student_Name | Department |
|---|---|---|
| 101 | Abdullah | CSE |
| 102 | Rahim | ICT |
| 103 | Karim | SWE |
| 104 | Hasan | CSE |

Here:

\[
Student\_ID \rightarrow Student\_Name
\]

\[
Student\_ID \rightarrow Department
\]

**Explanation:**

- If we know Student_ID = 101, we can uniquely identify Student_Name = Abdullah.
- If we know Student_ID = 101, we can uniquely identify Department = CSE.

Therefore, Student_ID functionally determines Student_Name and Department.

**Important:** Student_ID is the Determinant, while Student_Name and Department are Dependent Attributes.

## 4. Types of Functional Dependency

### 1. Trivial Functional Dependency

A Functional Dependency is trivial if the right-hand side (RHS) attributes are a subset of the left-hand side (LHS) attributes.

**Example:**
<img width="504" height="123" alt="image" src="https://github.com/user-attachments/assets/8c6bf00e-40f6-4112-8e1b-1406c4eb9b2d" />


### 2. Non-Trivial Functional Dependency

A Functional Dependency is non-trivial if the right-hand side attribute is not a subset of the left-hand side attributes.

**Example:**

<img width="485" height="125" alt="image" src="https://github.com/user-attachments/assets/875c6bff-840c-434e-b04a-19fd23dd31af" />


Here, Student_Name is not part of the left-hand side.

### 3. Full Functional Dependency

A Full Functional Dependency occurs when a non-key attribute depends on the entire composite key, not just a part of it.

**Example:**

Consider the following Student_Course table:

| Student_ID | Course_ID | Marks |
|---|---|---|
| 101 | C01 | 85 |
| 101 | C02 | 90 |
| 102 | C01 | 78 |

<img width="648" height="274" alt="image" src="https://github.com/user-attachments/assets/1eb0cca8-f12b-4548-a770-41819bc255ce" />

**Explanation:**

- Student_ID alone cannot determine Marks.
- Course_ID alone cannot determine Marks.
- Both Student_ID and Course_ID are required to determine Marks.

Therefore, Marks is fully functionally dependent on the entire composite key.

### 4. Partial Functional Dependency

A Partial Functional Dependency occurs when a non-key attribute depends on only a part of a composite candidate key, rather than the entire key.

**Example:**

<img width="514" height="210" alt="image" src="https://github.com/user-attachments/assets/82205a19-f670-441d-ac93-f822de8bda06" />


**Explanation:**

Student_Name depends only on Student_ID, which is a part of the composite key.

Therefore, Student_Name has Partial Functional Dependency.

### 5. Transitive Functional Dependency

A Transitive Functional Dependency occurs when one non-key attribute determines another non-key attribute through an intermediate attribute.
যখন একটি Attribute অন্য একটি Attribute-কে সরাসরি নির্ধারণ না করে, মাঝখানে অন্য একটি Attribute-এর মাধ্যমে পরোক্ষভাবে নির্ধারণ করে, তখন তাকে Transitive Functional Dependency বলে।
**Example:**

Consider the following Student table:

| Student_ID | Department_ID | Department_Name |
|---|---|---|
| 101 | D01 | Computer Science |
| 102 | D02 | Information Technology |

**Dependencies:**
<img width="461" height="387" alt="image" src="https://github.com/user-attachments/assets/22849696-099f-4ed4-a55f-02ebe4997c04" />


**Explanation:**

Student_ID indirectly determines Department_Name through Department_ID.

This is called Transitive Functional Dependency.

## 5. Why is Functional Dependency Important?

1. Helps identify Candidate Keys and Primary Keys.
2. Helps eliminate data redundancy.
3. Helps prevent insertion, deletion, and update anomalies.
4. Helps perform database normalization (1NF, 2NF, 3NF, BCNF).

