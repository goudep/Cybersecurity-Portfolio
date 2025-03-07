# **SQL Filter Project**

## **Project Description | 项目描述**
This project demonstrates how SQL filtering techniques can be applied to retrieve specific data for security analysis. The dataset includes two tables: `log_in_attempts` and `employees`, which contain information on login events and employee details, respectively. The project covers filtering techniques using:
- **Comparison operators (`>`, `<`, `=`, `!=`)**
- **Logical operators (`AND`, `OR`, `NOT`)**
- **Pattern matching (`LIKE`)**
- **Date and time filtering (`WHERE`, `BETWEEN`)**

本项目展示了如何应用 SQL 过滤技术来获取特定的安全分析数据。数据集包括 `log_in_attempts` 和 `employees` 两个表，分别存储登录事件和员工信息。本项目涵盖了以下 SQL 过滤技术：
- **比较运算符 (`>`, `<`, `=`, `!=`)**
- **逻辑运算符 (`AND`, `OR`, `NOT`)**
- **模式匹配 (`LIKE`)**
- **日期和时间过滤 (`WHERE`, `BETWEEN`)**

---

## **1. Retrieve After-Hours Failed Login Attempts**
📌 **Query:**
```sql
SELECT * 
FROM log_in_attempts 
WHERE login_time > '18:00' AND success = 0;
```
📌 **Explanation:**  
- Retrieves all login attempts that occurred **after 18:00** and were **unsuccessful** (`success = 0`).
- This helps identify potential **unauthorized access attempts** outside business hours.

---

## **2. Retrieve Login Attempts on Specific Dates**
📌 **Query:**
```sql
SELECT * 
FROM log_in_attempts 
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```
📌 **Explanation:**  
- Retrieves all login attempts that occurred **on May 8 and May 9, 2022**.
- The `OR` operator ensures results from **either date** are included.

---

## **3. Retrieve Login Attempts Outside of Mexico**
📌 **Query:**
```sql
SELECT * 
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```
📌 **Explanation:**  
- Filters out login attempts **originating from Mexico**, as country values may be `'MEX'` or `'MEXICO'`.
- The `LIKE` operator combined with `NOT` ensures all non-Mexico entries are returned.

---

## **4. Retrieve Employees in Marketing**
📌 **Query:**
```sql
SELECT * 
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East-%';
```
📌 **Explanation:**  
- Retrieves employees in the **Marketing** department who are located in offices **within the East building**.
- The `LIKE` pattern `'East-%'` matches office names like `'East-170'` and `'East-320'`.

---

## **5. Retrieve Employees in Finance or Sales**
📌 **Query:**
```sql
SELECT * 
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```
📌 **Explanation:**  
- Filters employees who work in **either the Finance or Sales** department.
- The `OR` operator ensures employees from **both departments** are included.

---

## **6. Retrieve All Employees Not in IT**
📌 **Query:**
```sql
SELECT * 
FROM employees
WHERE NOT department = 'Information Technology';
```
📌 **Explanation:**  
- Filters out employees who belong to the **Information Technology (IT)** department.
- The `NOT` operator ensures all employees **except IT staff** are returned.

---

## **Summary | 总结**
This project applied **SQL filtering techniques** to retrieve security-related data effectively. The filtering methods covered include:
- **Boolean filtering (`success = 0`)** for failed logins.
- **Date filtering (`WHERE login_date = 'YYYY-MM-DD'`)** for time-sensitive queries.
- **Pattern matching (`LIKE 'MEX%'`)** for flexible text filtering.
- **Logical operators (`AND`, `OR`, `NOT`)** for combining multiple conditions.

By leveraging these SQL techniques, security analysts can extract relevant information efficiently to detect security threats and manage organizational resources.

本项目应用 **SQL 过滤技术** 以有效提取安全相关数据。涵盖的方法包括：
- **布尔值过滤 (`success = 0`)** 以查找失败的登录尝试。
- **日期过滤 (`WHERE login_date = 'YYYY-MM-DD'`)** 以获取特定时间的记录。
- **模式匹配 (`LIKE 'MEX%'`)** 以实现灵活的文本匹配。
- **逻辑运算符 (`AND`, `OR`, `NOT`)** 以组合多个条件筛选数据。

通过掌握这些 SQL 技术，安全分析师可以高效提取关键信息，帮助检测安全威胁并优化企业资源管理。
