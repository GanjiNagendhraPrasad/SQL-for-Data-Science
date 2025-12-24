

<hr>

<h2>1. Introduction to SQL</h2>
<p>
SQL (Structured Query Language) is a standard language used to interact with
relational databases. It allows users to store, retrieve, manipulate, and manage
data efficiently.
</p>

<p><b>Uses of SQL:</b></p>
<ul>
  <li>Create and manage databases</li>
  <li>Create tables and relationships</li>
  <li>Insert, update, delete data</li>
  <li>Retrieve data using queries</li>
  <li>Control transactions</li>
</ul>

<hr>

<h2>2. Installation of SQL Server & SSMS</h2>
<ul>
  <li>Install SQL Server (Developer / Express Edition)</li>
  <li>Database Engine stores actual data</li>
  <li>Install SQL Server Management Studio (SSMS)</li>
  <li>SSMS is used to write and execute SQL queries</li>
</ul>

<p><b>Note:</b> SQL Server = Backend, SSMS = User Interface</p>

<hr>

<h2>3. DDL Operations (Data Definition Language)</h2>
<p>DDL commands define and modify database structure.</p>

<h3>CREATE</h3>
<pre>
CREATE DATABASE CompanyDB;

CREATE TABLE Employee (
  EmpId INT,
  EmpName VARCHAR(50),
  Salary MONEY
);
</pre>

<h3>ALTER</h3>
<pre>
ALTER TABLE Employee ADD Age INT;
ALTER TABLE Employee ALTER COLUMN EmpName VARCHAR(100);
ALTER TABLE Employee DROP COLUMN Age;
</pre>

<h3>SP_RENAME</h3>
<pre>
EXEC sp_rename 'Employee.EmpName', 'EmployeeName';
</pre>

<h3>TRUNCATE</h3>
<pre>
TRUNCATE TABLE Employee;
</pre>

<h3>DROP</h3>
<pre>
DROP TABLE Employee;
</pre>

<hr>

<h2>4. SQL Data Types</h2>

<h3>INT</h3>
<p>Stores whole numbers.</p>
<pre>Age INT</pre>

<h3>STRING</h3>
<p>Stores text data.</p>
<pre>EmpName VARCHAR(50)</pre>

<h3>FLOAT</h3>
<p>Stores decimal values.</p>
<pre>Marks FLOAT</pre>

<h3>MONEY</h3>
<p>Stores currency values.</p>
<pre>Salary MONEY</pre>

<hr>

<h2>5. DML Operations (Data Manipulation Language)</h2>

<h3>INSERT</h3>
<pre>
INSERT INTO Employee VALUES (1, 'Ravi', 45000);
INSERT INTO Employee (EmpId, EmpName) VALUES (2, 'Anil');
</pre>

<h3>UPDATE</h3>
<pre>
UPDATE Employee
SET Salary = 50000
WHERE EmpId = 1;
</pre>

<h3>DELETE</h3>
<pre>
DELETE FROM Employee WHERE EmpId = 1;
</pre>

<hr>

<h2>6. Difference Between DELETE & TRUNCATE</h2>
<table border="1">
<tr>
<th>DELETE</th>
<th>TRUNCATE</th>
</tr>
<tr>
<td>Deletes selected rows</td>
<td>Deletes all rows</td>
</tr>
<tr>
<td>WHERE clause allowed</td>
<td>WHERE not allowed</td>
</tr>
<tr>
<td>Rollback possible</td>
<td>Rollback not possible</td>
</tr>
<tr>
<td>Identity not reset</td>
<td>Identity reset</td>
</tr>
</table>

<hr>

<h2>7. IDENTITY</h2>
<p>Automatically generates incremental values.</p>
<pre>
EmpId INT IDENTITY(1,1)
</pre>

<hr>

<h2>8. SQL SET Concepts</h2>

<h3>UNION</h3>
<pre>
SELECT Name FROM A
UNION
SELECT Name FROM B;
</pre>

<h3>UNION ALL</h3>
<pre>
SELECT Name FROM A
UNION ALL
SELECT Name FROM B;
</pre>

<h3>EXCEPT</h3>
<pre>
SELECT Name FROM A
EXCEPT
SELECT Name FROM B;
</pre>

<h3>INSERT with SELECT</h3>
<pre>
INSERT INTO TableB
SELECT * FROM TableA;
</pre>

<hr>

<h2>9. DQL Operations (Data Query Language)</h2>

<h3>Selection Method</h3>
<pre>
SELECT * FROM Employee WHERE Salary > 40000;
</pre>

<h3>Projection Method</h3>
<pre>
SELECT EmpName, Salary FROM Employee;
</pre>

<hr>

<h2>10. Joins</h2>

<h3>ANSI Joins</h3>

<h4>INNER JOIN</h4>
<pre>
SELECT *
FROM Emp E
INNER JOIN Dept D
ON E.DeptId = D.DeptId;
</pre>

<h4>LEFT OUTER JOIN</h4>
<pre>
SELECT *
FROM Emp E
LEFT JOIN Dept D
ON E.DeptId = D.DeptId;
</pre>

<h4>RIGHT OUTER JOIN</h4>
<pre>
SELECT *
FROM Emp E
RIGHT JOIN Dept D
ON E.DeptId = D.DeptId;
</pre>

<h4>FULL OUTER JOIN</h4>
<pre>
SELECT *
FROM Emp E
FULL JOIN Dept D
ON E.DeptId = D.DeptId;
</pre>

<h4>CROSS JOIN</h4>
<pre>
SELECT * FROM Emp CROSS JOIN Dept;
</pre>

<h3>Non-ANSI Joins</h3>

<h4>Equi Join</h4>
<pre>
SELECT *
FROM Emp, Dept
WHERE Emp.DeptId = Dept.DeptId;
</pre>

<h4>Non-Equi Join</h4>
<pre>
SELECT *
FROM Emp E, Grade G
WHERE E.Salary BETWEEN G.MinSal AND G.MaxSal;
</pre>

<hr>

<h2>11. Memory Allocation</h2>

<h3>CHAR vs VARCHAR</h3>
<table border="1">
<tr>
<th>CHAR</th>
<th>VARCHAR</th>
</tr>
<tr>
<td>Fixed length</td>
<td>Variable length</td>
</tr>
<tr>
<td>Consumes full memory</td>
<td>Consumes required memory</td>
</tr>
</table>

<hr>

<h2>12. Primary Key & Foreign Key</h2>

<h3>Primary Key</h3>
<pre>
EmpId INT PRIMARY KEY
</pre>

<h3>Foreign Key</h3>
<pre>
DeptId INT
FOREIGN KEY (DeptId) REFERENCES Dept(DeptId)
</pre>

<h3>Operations</h3>
<ul>
  <li>INSERT: FK value must exist</li>
  <li>UPDATE: Restricted</li>
  <li>DELETE: Restricted unless cascade applied</li>
</ul>

<hr>

<h2>13. Cascade Rules</h2>
<pre>
ON DELETE CASCADE
ON UPDATE CASCADE
</pre>

<hr>

<h2>14. NULL</h2>
<p>NULL represents unknown or missing value.</p>

<pre>
SELECT * FROM Employee WHERE Salary IS NULL;
SELECT * FROM Employee WHERE Salary IS NOT NULL;
</pre>

<hr>

<h2>15. TCL Operations</h2>

<h3>BEGIN</h3>
<pre>BEGIN TRANSACTION;</pre>

<h3>COMMIT</h3>
<pre>COMMIT;</pre>

<h3>ROLLBACK</h3>
<pre>ROLLBACK;</pre>

<h3>SAVEPOINT</h3>
<pre>
SAVE TRANSACTION sp1;
ROLLBACK TRANSACTION sp1;
</pre>

<hr>

<h2>16. Ranking in SQL</h2>

<h3>Row-wise Ranking</h3>
<pre>
SELECT *,
ROW_NUMBER() OVER(ORDER BY Salary DESC) AS Rn
FROM Employee;
</pre>

<h3>Group-wise Ranking</h3>
<pre>
SELECT *,
RANK() OVER(PARTITION BY DeptId ORDER BY Salary DESC) AS Rnk
FROM Employee;
</pre>

<h3>Ranking Functions</h3>
<ul>
  <li>ROW_NUMBER()</li>
  <li>RANK()</li>
  <li>DENSE_RANK()</li>
</ul>

<hr>

<h2>17. Clauses</h2>

<h3>GROUP BY</h3>
<pre>
SELECT DeptId, SUM(Salary)
FROM Employee
GROUP BY DeptId;
</pre>

<h3>HAVING</h3>
<pre>
SELECT DeptId, SUM(Salary)
FROM Employee
GROUP BY DeptId
HAVING SUM(Salary) > 100000;
</pre>

