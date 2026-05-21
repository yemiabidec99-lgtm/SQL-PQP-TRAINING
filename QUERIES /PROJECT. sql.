create database mrs_tishe;
create table manager_tbl(
managerID char(5) primary key not null,
manager_name varchar(30) not null);

insert into manager_tbl
values ('MG08','kunle'),
('MG03','Bright'),
('MG12','Vivian');

CREATE TABLE course_table (
    courseID CHAR(5) PRIMARY KEY NOT NULL,
    course_name VARCHAR(30) NOT NULL
);


insert into course_table
values ('CP01','data analysis'),
('CP02','Web dev'),
('CP03','Cybersecurity'),
('CP04','AI');

CREATE TABLE location_table (
locationID CHAR(5) PRIMARY KEY NOT NULL,
location_name VARCHAR(30) NOT NULL);

insert into location_table
values ('LC01','Abuja'),
('LC02','Lagos');


CREATE TABLE Candidate_tbl (
candidateID varchar(30) primary key not null,
Reg_date date not null,
Opp_type varchar(30) not null,
Success_story varchar(10) null,
success_date date null,
training_session varchar(20) null,
training_type varchar (30) null,
ManagerID char(5) not null,
courseID CHAR (5) NOT NULL,
locationID char(5) not null,
foreign key(managerID) references manager_tbl(managerID),
Foreign key (courseID) references course_table(courseID),
Foreign key (locationID) references location_table(locationID)
);


CREATE TABLE Certificate_tbl (
certificate_ID varchar(20)  not null,
certificate_status varchar(15) null,
mode_of_issues char(5) null,
candidate_ID Varchar(30) not null,
primary key(certificate_ID,Candidate_ID)
);


CREATE TABLE Cand_course_tbl(
candidate_ID varchar(14) primary key not null,
course_ID char(4) not null,
foreign key(candidate_ID) references candidate_tbl(candidateID),
Foreign key (course_ID) references course_table(courseID)
);


CREATE TABLE Trans_tbl(
trans_ID varchar(10) primary key not null,
trans_amount decimal(10,2) check(trans_amount !=0),
promo_code varchar(17) default null,
trans_1st_inst decimal(10,2),
trans_2nd_inst decimal(10,2),
trans_3rd_inst decimal(10,2),
payment_date date not null,
payment_date_2nd date default null,
payment_date_3nd date default null,
cand_ID Varchar(16)not null,
manager_ID char(4)not null,
course_ID char(4)not null,
Location_ID char(4)not null
);


-- Selects all columns (*) and all rows from the candidate_tbl.
SELECT*
FROM candidate_tbl;
-- Selects only the columns 'candID' and 'Opp_type' from the candidate_tbl.
SELECT candidateID as 'CandidateID', Opp_type as 'oppurnity type'
FROM candidate_tbl;
-- Selects all columns from candidate_tbl where the Opp_type is NOT equal to 'Closed won'.
SELECT *
FROM  Candidate_tbl
WHERE opp_type!= "closed won";-- using the comparison operator
SELECT *
FROM candidate_tbl
WHERE NOT (opp_type='closed won');-- using the 'NOT' logic operator

-- Selects all columns from transaction_tbl where Promo_code is 'kezi01' AND -- Instalm_1 is NOT greater than 100000 (i.e., less than or equal to 100000).
SELECT*
FROM trans_tbl
WHERE promo_code = 'kezi01' AND trans_1st_inst <= 100000;
-- Selects all columns from transaction_tbl where Promo_code is one of the listed values -- ('kezi01', 'referals', 'ads') AND Instalm_1 is less than 100000.
SELECT*
FROM trans_tbl
WHERE promo_code IN ('kezi01','referals','ads') AND trans_1st_inst <100000;
-- Selects all columns from transaction_tbl where Instalm_1 is between 50000 and 100000 (inclusive).
SELECT*
FROM trans_tbl
WHERE trans_1st_inst between 50000 and 100000;
-- Selects Promo_code from transaction_tbl where the Promo_code ends with the letter 'k'.
SELECT promo_code
FROM trans_tbl
WHERE promo_code like'%k';

-- Counts the total number of rows in the candidate_tbl.
SELECT count(*) as total_rows
from candidate_tbl;
-- Calculates the sum of all values in the Instalm_1 column.
SELECT SUM(trans_1st_inst)
FROM trans_tbl;
-- Finds the largest value in the Instalm_1 column.

SELECT MAX(trans_1st_inst)
FROM trans_tbl;
-- Finds the smallest value in the Instalm_1 column.
 SELECT MIN(trans_1st_inst)
 FROM trans_tbl;

 
 -- 1 Write a query to fetch the CandID, Reg_date, and Training_type from candidate table.
 SELECT candidateID,Reg_date,Training_type
 from candidate_tbl;

-- 2 Retrieve the CandID and Trainin_session of all candidates whose Training_type is 'Virtual' from the candidate table.
SELECT candidateID,training_session,training_type
from candidate_tbl
WHERE Training_type = 'Virtual';

-- 3 Write a query to find the CertID and CandID of all candidates whose Cert_status is 'Collected' from the certificate table.
SELECT certificate_ID, candidate_ID,certificate_status
FROM certificate_tbl
WHERE certificate_status = 'Collected';

-- 4  Write a query to fetch the TransID, CandID, and Amount for transactions where the Amount is greater than 200000 from the transaction table.
 SELECT Trans_ID,cand_ID,trans_amount 
 FROM trans_tbl
 WHERE trans_amount > 200000;
 
  -- 5 Retrieve the CandID and Loc_ID of candidates who are based in 'Lagos'. Use the Location_tbl for this query.
 SELECT candidateID,candidate_tbl.locationID,location_name
from candidate_tbl
join location_table on candidate_tbl.locationID=location_table.locationID
where location_name = 'lagos';



-- 1 Retrieve the CandidateID and Reg_Date for every candidate in the system.
SELECT candidateID,Reg_date
FROM candidate_tbl;

-- 2 Display a full list of all course IDs and their names.      
SELECT *
FROM course_table;


-- 3 List all candidates who chose Physical as their training type. 
SELECT *
FROM candidate_tbl
WHERE Training_type = 'Physical';

-- 4 Show all transaction records where the total amount paid exceeds ₦50,000.
SELECT *
FROM trans_tbl
WHERE trans_amount > 50000;

 -- 5 how many candidates are based in each training location.Count candidates grouped by Loc_ID.
 SELECT locationID, COUNT(*) AS Total_Candidates
FROM candidate_tbl
GROUP BY locationID;

-- 6 HR needs a report of all candidates who registered within the year 2021 for annual review. 
SELECT*
FROM candidate_tbl
WHERE Reg_Date BETWEEN '2021-01-01' AND '2021-12-31';

-- 7 The admin team wants to see which candidates have physically collected their certificates. -
SELECT *
FROM certificate_tbl
WHERE certificate_status = 'Collected';



 -- 1 Selects all columns from the transaction_tbl and orders the results,Instalm_1 in descending order.
SELECT *
FROM trans_tbl
ORDER BY trans_1st_inst DESC;

-- 2 Selects all columns from the transaction_tbl and orders the results,promo code by ascending order.
SELECT *
FROM trans_tbl
ORDER BY promo_code;

-- 3 Selects all columns from the transaction_tbl and orders the results,Instalm_1 in descending order, and then by Promo_code ascending order
SELECT*
FROM trans_tbl
ORDER BY trans_1st_inst DESC,promo_code;

-- 4 Selects the distinct values of the Opp_type (Opportunity Type).
SELECT distinct opp_type
FROM candidate_tbl;

SELECT OPP_TYPE
FROM candidate_tbl
GROUP BY Opp_type;

-- 5 Selects the Opp_type and counts the number of candidates (CandID)
SELECT opp_type, COUNT(*)
FROM candidate_tbl
GROUP BY Opp_type;

-- 6 Selects the Opp_type, Trainin_type, and counts the number of candidates
SELECT  Opp_type, training_type, count(*)
FROM candidate_tbl
GROUP BY Opp_type,training_type;

-- 7 Selects the Opp_type, Trainin_type, and counts the number of candidates,
-- assigning the alias 'total candidate' to the count.
SELECT Opp_type, Training_type, COUNT(*) AS "total candidate"
FROM candidate_tbl
GROUP BY Opp_type,training_type;

SELECT Opp_type, training_type, COUNT(candidateID) AS "total candidate"
FROM candidate_tbl
GROUP BY Opp_type, training_type;

-- 8 Calculates the sum of Instalm_1 (aliased as 'total of first installment'),
-- and the sum of Instalm_2 (aliased as 'total of second installment'),
-- for each unique Promo_code.

SELECT Promo_code,SUM(trans_1st_inst) AS "total of first installment",SUM(trans_2nd_inst) AS "total of second installment"
FROM trans_tbl
GROUP BY Promo_code;

SELECT Promo_code,
       SUM(trans_1st_inst) AS "total of first installment",
       SUM(trans_2nd_inst) AS "total of second installment"
FROM trans_tbl
GROUP BY Promo_code;

-- 9 Selects all columns from the candidate_tbl and limits the output,
-- to the first 10 rows.

SELECT *
FROM candidate_tbl 
LIMIT 10;

-- 10 Calculates the sum of Instalm_1 for each Promo_code,with the total sum of Instalm_1 greater than 100000.

SELECT Promo_code,SUM(trans_1st_inst) 
FROM trans_tbl
GROUP BY Promo_code
HAVING SUM(trans_1st_inst) > 100000;


SELECT Promo_code,
       SUM(Instalm_1) AS total_instalm_1
FROM transaction_tbl
GROUP BY Promo_code
HAVING SUM(Instalm_1) > 100000;

-- 11 Selects all columns and all rows from the candidate_tbl.

SELECT *
FROM candidate_tbl;

-- 12  Selects all columns and all rows from the transaction_tbl.

SELECT *
FROM trans_tbl;

-- 13 Performs an INNER JOIN between candidate_tbl (aliased as 'can')
-- and transaction_tbl (aliased as 'trans')
-- Selects all columns from the resulting joined table.

SELECT *
FROM candidate_tbl AS c
INNER JOIN trans_tbl AS t
ON c.candidateID=t.cand_ID;

 -- 14 Performs an INNER JOIN between candidate_tbl (aliased as 'can')
-- and transaction_tbl (aliased as 'trans') using the CandID column as the join key.- Selects specific columns: candidate ID from both tables, Registration date,
-- Opportunity type, Payment date 1, and Installment 1 amount.

SELECT c.candidateID,
    t.cand_ID,
    c.Reg_date,
    c.Opp_type,
    t.payment_date,
    t.trans_1st_inst
FROM candidate_tbl AS c
INNER JOIN trans_tbl AS t
ON c.candidateID=t.cand_ID;

-- 1 The registrar wants a list of all candidates and the exact date they enrolled. Retrieve the 
-- candidateID and Reg_Date for every candidate in the system.

SELECT 
    candidateID,
    Reg_Date
FROM candidate_tbl;

 -- 2 A prospective student is asking what programmes are on offer. Display a full list of all course 
-- IDs and their names.

SELECT 
course_name,
courseID
FROM course_table;

-- 3 The facilities team needs to prepare classrooms. List all candidates who chose Physical as 
-- their training type. 

SELECT *
FROM candidate_tbl
WHERE Training_type = 'Physical';

 -- 4 The finance team is reviewing premium payments. Show all transaction records where the 
-- total amount paid exceeds ₦50,000.

SELECT *
FROM trans_tbl
WHERE trans_amount > 50000;

 -- 5 The marketing team wants to know how many candidates are based in each training location. 
-- Count candidates grouped by Loc_ID.

SELECT locationID,
    COUNT(*) AS Total_Candidates
FROM candidate_tbl
GROUP BY locationID;

SELECT locationID,
    COUNT(*) 
FROM candidate_tbl
GROUP BY locationID;

-- 6 HR needs a report of all candidates who registered within the year 2021 for annual review.
SELECT *
FROM candidate_tbl
WHERE Reg_Date BETWEEN '2021-01-01' AND '2021-12-31';


-- 1 from transaction_tbl, display candID and Amount, AND classify payment as:
-- 'high payment' if Amount  > 100,000
-- 'Medium Payment' if Amount between 50,000 AND 100,000
-- 'Low Payment' if Amount  < 50,000

SELECT Cand_ID, trans_amount,
CASE 
WHEN trans_amount > 100000 THEN 'high payment'
WHEN trans_amount between 50000 AND 100000 THEN 'Medium Payment'
WHEN trans_amount < 50000 THEN 'Low Payment'
END AS payment_category
from trans_tbl;






