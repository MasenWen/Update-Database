
# <p align="center">PDS Project2 Report</p>
# <p align="center">ParseTree and Injection Attack部分</p>

**<p align="center">Masen Wen</p>**
**<p align="center">2025-12-05</p>**


* 实验代码&实验报告已上传Github
  * https://github.com/MasenWen



---

## 实验设计
  * The Experiments Are Based On code and data Zip And Is About Injection Attack.
    * We First Experiment The Injection Attack And Defence.
    * Then We Recap By Using ParseTree To See How DataBase Build Queries Into Trees And How Injection Attack Is Avoided By Securing Query Structure In The First Place.


* **实验程序设计**
  * DataManipulation接口
    * 包含一组数据库操作接口
    * 例如：String findMovieById(int id)
    * 可扩展。例如：String findMovieByTitleLimited10(String like)
  * DatabaseManipulation类
    * DataManipulation接口的实现类，对PostgreSQL DB进行访问封装
    * 需要实现findMovieByTitleLimited10(String like)等接口
  * Client.java
	  * 测试程序，模拟注入攻击的代码在此
	  * 例如：dm.findMoviesByLimited10("'aba';drop table movies;--") 注入 DROP TABLE 语句

![image.png](60b1bee9-189f-456e-87a2-12e9f954f277.png)


---

## 实验1：注入Drop Table

![image.png](033e3dd2-c1fc-417c-9643-654ba11a823a.png)
![image.png](31a53a55-126a-4bbf-be0f-f6a580849cda.png)
![image.png](2139c815-3ba5-4177-bc6f-5921e3519ed5.png)
![image.png](bf51b3f2-1245-4b39-88ab-a640997fc761.png)


---

## Theory: Syntax Analysis Tree in DataBase

The database system's query processing workflow is a complex and ordered process, primarily encompassing three critical stages: **Query Parsing**, **Query Optimization**, and **Query Execution**. Central to this workflow is the conversion of human-readable SQL text into machine-executable instructions, relying on various "tree" structures for representation and transformation.

##### Structure and Core Theory of Database Query Processing
1.  **Query Parsing Stage:**
    * **Input:** The raw **SQL query string**.
    * **Steps:** Lexical Analysis → **Syntax Analysis** → Semantic Analysis.
    * **Output/Tree Properties:** Syntax analysis constructs the **Syntax Analysis Tree (Parse Tree)**, which is the structure we have visualized. The **property** of this tree is that it consists of **non-terminal nodes** (grammar class nodes, representing the SQL statement structure) and **terminal nodes** (leaf nodes, representing actual data or keywords). Semantic analysis then converts the Syntax Tree into a **Query Tree** based on relational algebra, which serves as the output for this stage.

2.  **Query Optimization Stage:**
    * **Input:** The Query Tree (semantically validated).
    * **Output:** The optimal **Query Execution Plan**, determined through various logical equivalence transformations.

**The diagrams used in our experiment** are a **simplified representation** of the **Syntax Analysis Tree** generated during the **Query Parsing stage**.

**The goal of the experiment** is to use this simplified Parse Tree to **visually illustrate the essence of a successful SQL Injection attack**: When an application uses insecure string concatenation (e.g., `Statement`), the database parser misidentifies malicious SQL keywords and symbols (like semicolons or `OR`) within the user input as **structural nodes**, thereby **tampering with** the structure of the original query's Syntax Analysis Tree. Conversely, the defense mechanism of `PreparedStatement` ensures that all user input is parsed strictly as a **single data literal (a leaf node)** on the tree, fundamentally protecting the integrity of the Parse Tree structure.

---
####

![image.png](ac4118a0-c2e1-4901-ad0b-098e19d84f93.png)
![image.png](6abd9069-7ae1-4b69-8c6c-f007242bd423.png)





---

## 实验2：注入Drop Table的防御

![image.png](01a21cfa-fa59-4828-8753-6aaccfbd40fc.png)

### Original Query
![image.png](6840f050-8223-454c-940b-20eba5921cbc.png)

### Injection Attack
  * Using: Drop Table movies;
![image.png](6726a316-d9a4-4d08-960c-1407f04d1fbd.png)

### Defending Check: Found Invalid Input
![image.png](8b325655-3d21-4d87-a926-cd7235f8943b.png)


---


## 实验3：注入Drop Table的防御

Practice: Complete the **Full Tree** by adding **From** according to the **Query**.
Original Query
![image.png](4ff9d90b-d5cb-4786-92f8-8e5a34ee7896.png)

### Injection Attack

  * Using: Drop Table movies;
![image.png](7bd54d58-f215-4f29-8cc9-6909651ee2e4.png)

### Defending Check: Found Invalid Input

![image.png](f3de42bf-2475-4f55-8653-26b9d3100481.png)

---


## 实验4：注入OR TURE的防御

Practice: This Query is not implemented, complete the code following the Tree
![image.png](9e7e4f8a-342c-4326-a22b-20ce2c119aee.png)

Original Query
![image.png](86367f73-281b-4bf1-8ecc-070bd17ac6d6.png)

### Injection Error
  * Using: TRUE; that spoils the query.
![image.png](d9ae978c-deab-4846-9a45-69bdf8e2ace3.png)

### Defending Check: Found Invalid Input
![image.png](c8db684e-67bd-4021-ab7e-27d702d813e8.png)


---


## 实验5：No-input-query can't be injected

![image.png](8b124bd9-2403-48a9-ba66-876e7251784f.png)
![image.png](37c3bb0c-fd87-485a-b420-bdcba360f79e.png)

### No-input-query can't be injected.
![image.png](1680a63c-6cd8-4f07-9bb1-11d016757615.png)

### About
  * PSQL don't really use this format of trees, though very similar.
  * However, format like this can be used in miniob.
  * This format is introduced from this link, **Read** to learn more:
  * https://dbgroup.cs.tsinghua.edu.cn/ligl/courses/slides10.pdf

