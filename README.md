# 50 Essential SQL Server Interview Questions 
 50 Essential SQL Server Interview Questions  MANG & FAANG Style
# 50 SQL Query Interview Questions for Practice
![Blue Gradient Modern Freelancer YouTube Thumbnail ](https://github.com/baliramyadav/50-Essential-SQL-Server-Interview-Questions-/assets/80908177/1d118c46-7af4-4e93-a2a3-cef46d554781)


---Create database
Create database ORG;

--how to use ORG database
Use ORG
----
--how to create table
Create table Worker
(
 WORKER_ID INT IDENTITY(1,1) PRIMARY KEY,
 FIRST_NAME CHAR(25),
 LAST_NAME CHAR(25),
 SALARY INT,
 JOINING_DATE DATETIME,
 DEPARMENT CHAR(25)
);

SELECT * FROM Worker

--DATA INSERT
INSERT INTO Worker(FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARMENT) VALUES
( 'Monika', 'Arora', 100000, '2024-02-20', 'HR'),
( 'Niharika', 'Verma', 80000, '2024-01-11 ', 'Admin'),
( 'Vishal', 'Singhal', 300000, '2024-02-20', 'HR'),
( 'Amitabh', 'Singh', 500000, '2024-02-20 ', 'Admin'),
( 'Vivek', 'Bhati', 500000, '2024-02-11 ', 'Admin'),
( 'Vipul', 'Diwan', 200000, '2024-03-11', 'Account'),
( 'Satish', 'Kumar', 75000, '2024-01-20 ', 'Account'),
( 'Geetika', 'Chauhan', 90000, '2024-02-11', 'Admin');

INSERT INTO Worker(FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) VALUES
( 'Ravi', 'Yadav', 100000, '2021-02-20', 'HR')

-- BONUS
CREATE TABLE Bonus (
	WORKER_REF_ID INT,
	BONUS_AMOUNT INT,
	BONUS_DATE DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);

SELECT * FROM Bonus
INSERT INTO Bonus 
	(WORKER_REF_ID, BONUS_AMOUNT, BONUS_DATE) VALUES
		(005, 5000, '2024-02-20'),
		(002, 3000, '2024-03-11'),
		(003, 4000, '2024-02-20'),
		(005, 4500, '2024-02-20'),
		(002, 3500, '2024-03-11');


CREATE TABLE Title (
	WORKER_REF_ID INT,
	WORKER_TITLE CHAR(25),
	AFFECTED_FROM DATETIME,
	FOREIGN KEY (WORKER_REF_ID)	REFERENCES Worker(WORKER_ID)    ON DELETE CASCADE
);


INSERT INTO Title 
	(WORKER_REF_ID, WORKER_TITLE, AFFECTED_FROM) VALUES
 (009, 'Manager', '2023-02-20 00:00:00'),
 (002, 'Executive', '2023-06-11 00:00:00'),
 (008, 'Executive', '2023-06-11 00:00:00'),
 (005, 'Manager', '2023-06-11 00:00:00'),
 (004, 'Asst. Manager', '2023-06-11 00:00:00'),
 (007, 'Executive', '2023-06-11 00:00:00'),
 (006, 'Lead', '2023-06-11 00:00:00'),
 (003, 'Lead', '2023-06-11 00:00:00');

 ----
 sELECT * FROM Worker
 SELECT * FROM Bonus
 SELECT * FROM Title

 ------------------------------------50 SQL QUERY-------------------------
 --Q-1. Write an SQL query to fetch “FIRST_NAME” from the Worker table using the alias name <WORKER_NAME>.

 SELECT FIRST_NAME AS WORKER_NAME FROM Worker

 --Q-2. Write an SQL query to fetch “FIRST_NAME” from the Worker table in upper case.
  SELECT UPPER(FIRST_NAME)FIRST_NAME   FROM Worker

  --Q-3. Write an SQL query to fetch unique values of DEPARTMENT from the Worker table.
  SELECT DISTINCT DEPARTMENT FROM Worker

  ---hOW TO CHANGE COLOUMN NAME 
  EXEC SP_RENAME 'Worker.DEPARMENT','DEPARTMENT','COLUMN'

  --Q-4. Write an SQL query to print the first three characters of  FIRST_NAME from the Worker table. SELECT FIRST_NAME  FROM Worker
  SELECT SUBSTRING(FIRST_NAME,3,3) AS FIRST_NAME FROM Worker
  
  --Q-5. Write an SQL query to find the position of the alphabet (‘a’) in the first name column ‘Amitabh’ from the Worker table.
    --SELECT FIRST_NAME  FROM Worker WHERE FIRST_NAME='Amitabh'
	SELECT CHARINDEX('n',FIRST_NAME) AS NAME FROM Worker WHERE FIRST_NAME='Monika' 
 
	--Q-6. Write an SQL query to print the FIRST_NAME from the Worker table after removing white spaces from the right side.
	SELECT RTRIM(FIRST_NAME)FIRST_NAME  FROM Worker
 
	--Q-7. Write an SQL query to print the FIRST_NAME from the Worker table after removing white spaces from the LEFT side.
	SELECT LTRIM(FIRST_NAME)FIRST_NAME  FROM Worker
 
	--Q-8. Write an SQL query that fetches the unique values of DEPARTMENT from the Worker table and prints its length.
	SELECT DISTINCT DEPARTMENT,LEN(DEPARTMENT) AS LENGTH FROM Worker
 
	--Q-9. Write an SQL query to print the FIRST_NAME from the Worker table after replacing ‘a’ with ‘A’.
	SELECT REPLACE(FIRST_NAME,'a','A')FIRST_NAME FROM Worker
 
	--Q-10. Write an SQL query to print the FIRST_NAME and LAST_NAME from the Worker table into a single column COMPLETE_NAME. A space char should separate them.
	SELECT (FIRST_NAME+LAST_NAME) AS COMPLETE_NAME FROM Worker
 
	--Q-11. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending.
	SELECT * FROM Worker ORDER BY FIRST_NAME ASC
 
	--Q-12. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.
	SELECT * FROM Worker ORDER BY FIRST_NAME ASC,DEPARTMENT DESC
 
	---Q-13. Write an SQL query to print details for Workers with the first names “Vipul” and “Satish” from the Worker table.
	SELECT * FROM Worker WHERE FIRST_NAME IN('VIPUL','SATISH','CODER')
 
	----Q-14. Write an SQL query to print details of workers excluding first names, “Vipul” and “Satish” from the Worker table.
	SELECT * FROM Worker WHERE FIRST_NAME  NOT IN('VIPUL','SATISH')
 
	--Q-15. Write an SQL query to print details of Workers with DEPARTMENT name as “Admin”.
	SELECT * FROM Worker WHERE DEPARTMENT='ADMIN'
	SELECT * FROM Worker WHERE DEPARTMENT LIKE 'ADMIN%'
 
	--Q-16. Write an SQL query to print details of the Workers whose FIRST_NAME contains ‘a’.
	SELECT * FROM Worker WHERE FIRST_NAME LIKE '%a%'
 
	--Q-17. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘a’.
	SELECT * FROM Worker WHERE FIRST_NAME LIKE '%A'
 
	--Q-18. Write an SQL query to print details of the Workers whose 
	--FIRST_NAME ends with ‘h’ and contains six alphabets.
	SELECT * FROM Worker WHERE FIRST_NAME LIKE '_____h'
 
	--Q-19. Write an SQL query to print details of the Workers whose 
	--SALARY lies between 100000 and 500000.
	SELECT * FROM Worker WHERE SALARY BETWEEN 100000 and 500000
 
	--Q-20. Write an SQL query to print details of the Workers who joined in Feb 2021.
	SELECT * FROM Worker WHERE YEAR(JOINING_DATE)=2021 AND MONTH(JOINING_DATE)=2
 
	--Q-21. Write an SQL query to fetch the count of employees working in the department ‘Admin’.
	SELECT COUNT(*)AS 'count of employees' FROM Worker WHERE DEPARTMENT='ADMIN'
 
	--Q-22. Write an SQL query to fetch worker names with salaries >= 50000 and <= 100000.
	SELECT FIRST_NAME,SALARY FROM Worker WHERE SALARY >=50000 AND SALARY<=100000
 
	--Q-23. Write an SQL query to fetch the number of workers for each department in descending order.
	SELECT DEPARTMENT,COUNT(WORKER_ID)AS No_Of_Workers FROM Worker GROUP BY DEPARTMENT	ORDER BY No_Of_Workers DESC
 
	--Q-24. Write an SQL query to print details of the Workers who are also Managers.
	SELECT W.FIRST_NAME,T.WORKER_TITLE FROM Worker AS W
	INNER JOIN Title AS T
	ON W.WORKER_ID=T.WORKER_REF_ID AND T.WORKER_TITLE IN('Manager')
 
	--Q-25. Write an SQL query to fetch duplicate records having matching data in some fields of a table.
	SELECT WORKER_TITLE,AFFECTED_FROM,COUNT(*) AS 'COUNT' FROM Title GROUP BY WORKER_TITLE,AFFECTED_FROM
	HAVING COUNT(*)>1
 
	---Q-26. Write an SQL query to show only odd rows from a table.
	SELECT * FROM Worker  WHERE WORKER_ID%2=1
 
	--Q-27. Write an SQL query to show only even rows from a table.
	SELECT * FROM Worker  WHERE WORKER_ID%2=0
 
	--Q-28. Write an SQL query to clone a new table from another table.
	SELECT * INTO WorkerClone FROM Worker
 
--Q-29. Write an SQL query to fetch intersecting records of two tables.
SELECT * FROM Worker INTERSECT (SELECT * FROM WorkerClone)

--Q-30. Write an SQL query to show records from one table that another table does not have.
SELECT * FROM Worker MINUS SELECT * FROM Title

--Q-31. Write an SQL query to show the current date and time.
SELECT GETDATE()

 ---Q-32. Write an SQL query to show the top n (say 10) records of a table.
 SELECT TOP 2 * FROM Worker ORDER BY SALARY DESC

 --Q-33. Write an SQL query to determine the nth (say n=5) highest salary from a table.
 SELECT TOP 13 SALARY
 FROM
 (
 SELECT DISTINCT TOP 5 SALARY FROM Worker ORDER BY SALARY DESC
 ) AS SALARY
 ORDER BY SALARY ASC
 
 
 --Q-34. Write an SQL query to determine the 5th highest salary without using the TOP or limit method.
 SELECT SALARY FROM Worker W
 WHERE 5=(
 SELECT COUNT(DISTINCT(W2.SALARY)) FROM Worker W2 WHERE W2.SALARY>=W.SALARY
 )

 ----Q-35. Write an SQL query to fetch the list of employees with the same salary.
 SELECT DISTINCT W.WORKER_ID,W.FIRST_NAME,W.SALARY FROM Worker W,Worker W1
 WHERE W.SALARY=W1.SALARY AND W.WORKER_ID!=W1.WORKER_ID

 --Q-36. Write an SQL query to show the second-highest salary from a table.
 SELECT MAX(SALARY)'second-highest salary' FROM Worker
 WHERE SALARY NOT IN(SELECT MAX(SALARY) FROM Worker)

 --Q-37. Write an SQL query to show one row twice in the results from a table.
 SELECT FIRST_NAME,DEPARTMENT FROM Worker W WHERE W.DEPARTMENT='HR'
 UNION ALL
 SELECT FIRST_NAME,DEPARTMENT FROM Worker W WHERE W.DEPARTMENT='HR'

 SELECT * FROM Worker UNION ALL SELECT * FROM Worker

 --Q-38. Write an SQL query to fetch intersecting records of two tables.
 SELECT * FROM Worker INTERSECT (SELECT * FROM WorkerClone)

 --Q-39. Write an SQL query to fetch the first 50% of records from a table.
 SELECT * FROM Worker
 WHERE WORKER_ID<=(SELECT COUNT(WORKER_ID)/2 FROM Worker)


 ---Q-40. Write an SQL query to fetch the departments that have less than five people in them.
 SELECT DEPARTMENT ,COUNT(WORKER_ID)AS 'No_OF_Worker' FROM Worker
 GROUP BY DEPARTMENT HAVING COUNT(WORKER_ID)<5;

 --Q-41. Write an SQL query to show all departments along with the number of people in there.
 SELECT DEPARTMENT, COUNT(DEPARTMENT) AS 'No_OF_Worker' FROM Worker GROUP BY DEPARTMENT

 --Q-42. Write an SQL query to show the last record from a table.
 SELECT * FROM Worker WHERE WORKER_ID=(SELECT MAX(WORKER_ID)FROM Worker)

 --Q-43. Write an SQL query to fetch the first row of a table.
 SELECT * FROM Worker WHERE WORKER_ID=(SELECT MIN(WORKER_ID)FROM Worker)

 --Q-44. Write an SQL query to fetch the last five records from a table.
 SELECT TOP 5 * FROM Worker ORDER BY WORKER_ID DESC
 --Q-45. Write an SQL query to print the names of employees having the highest salary in each department.
 SELECT T.DEPARTMENT,T.FIRST_NAME,T.SALARY FROM(SELECT MAX(SALARY)AS TOTALSALARY, DEPARTMENT FROM Worker
 GROUP BY DEPARTMENT)AS TEMPNEW
 INNER JOIN Worker T ON TEMPNEW.DEPARTMENT=T.DEPARTMENT AND TEMPNEW.TOTALSALARY=T.SALARY


 --Q-46. Write an SQL query to fetch three max salaries from a table.
 SELECT DISTINCT SALARY FROM Worker W WHERE 3>=(SELECT COUNT(DISTINCT SALARY)FROM Worker W1 WHERE 
 W.SALARY<=W1.SALARY) ORDER BY W.SALARY DESC


 --Q-47. Write an SQL query to fetch three min salaries from a table.

 SELECT DISTINCT SALARY FROM Worker W WHERE 3>=(SELECT COUNT(DISTINCT SALARY)FROM Worker W1 WHERE 
 W.SALARY>=W1.SALARY) ORDER BY W.SALARY DESC

 --Q-48. Write an SQL query to fetch nth max salaries from a table.
 SELECT DISTINCT SALARY FROM Worker W1 WHERE 8>=(SELECT COUNT(DISTINCT SALARY) FROM
 Worker W2 WHERE W1.SALARY<=W2.SALARY)ORDER BY W1.SALARY DESC

 --Q-49. Write an SQL query to fetch departments along with the total salaries paid for each of them
 SELECT DEPARTMENT, SUM(SALARY)AS TOT_SALARY FROM Worker GROUP BY DEPARTMENT

 --Q-50. Write an SQL query to fetch the names of workers who earn the highest salary.
 SELECT DISTINCT FIRST_NAME,SALARY FROM Worker WHERE SALARY=(SELECT MAX(SALARY) FROM Worker)

Crack Your SQL Server Interview: 50 Questions Explained & Asked by MANG & FAANG Companies
https://youtu.be/oGhO-6ZB4vw

happy coding :P 
