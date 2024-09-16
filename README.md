	


DDL AND INSERT STATEMENTS
DROP TABLE Course_Type;
DROP TABLE Room;
DROP TABLE Trainer;
DROP TABLE Allocated_Student;
DROP TABLE Current_Course;
DROP TABLE Allocation;


--Course_Type Table--
CREATE TABLE Course_Type ( 
	Course_Code  VARCHAR(20) NOT NULL,
	Course_Title VARCHAR(200) NOT NULL,
	Course_Cost NUMERIC(20) NOT NULL,
CONSTRAINT Course_Type_Course_Code_PK PRIMARY KEY(Course_Code));



--Room Table--
CREATE TABLE Room(
    Room_No   VARCHAR(20) NOT NULL,
    Room_Type VARCHAR(70) NOT NULL,
CONSTRAINT Room_Room_No_PK PRIMARY KEY(Room_No)
);



--Trainer Table--
CREATE TABLE Trainer(
    Trainer_ID   VARCHAR(20) NOT NULL,
    Trainer_Name VARCHAR(150) NOT NULL,
    Course_Title VARCHAR(300) NOT NULL,
CONSTRAINT Trainer_Trainer_ID_PK PRIMARY KEY (Trainer_ID)
 );


--Allocated Student Table--
CREATE TABLE Allocated_Student(
    Student_ID VARCHAR(20) NOT NULL,
    Student_Name VARCHAR(200) NOT NULL,
CONSTRAINT Allocated_Student_Student_ID_PK PRIMARY KEY(Student_ID)
);


--Current_Course Table--
CREATE TABLE Current_Course(
    Current_Course_ID VARCHAR(20) NOT NULL,
    Course_Code VARCHAR(20) NOT NULL,
    Trainer_ID VARCHAR(20) NOT NULL,
    Room_No VARCHAR(20) NOT NULL,
    Start_Date DATE NOT NULL,
    End_date DATE NOT NULL,
    Period NUMERIC(20) NOT NULL,
    Limit_of_Students NUMERIC(20) NOT NULL,
CONSTRAINT Current_Course_Current_Course_ID_PK PRIMARY KEY (Current_Course_ID),
CONSTRAINT Current_Course_Course_Code_FK FOREIGN KEY (Course_Code) REFERENCES Course_Type(Course_Code),
CONSTRAINT Current_Course_Trainer_ID_FK FOREIGN KEY (Trainer_ID) REFERENCES Trainer(Trainer_ID),
CONSTRAINT Current_Course_Room_No_FK FOREIGN KEY (Room_No) REFERENCES Room(Room_No)
    );


--Allocation Table--
CREATE TABLE Allocation(
    Allocation_ID VARCHAR(20) NOT NULL,
    Current_Course_ID VARCHAR(20) NOT NULL,
    Student_ID VARCHAR(20) NOT NULL,
CONSTRAINT Allocation_Allocation_ID_PK PRIMARY KEY (Allocation_ID),
CONSTRAINT Allocation_Current_Course_ID_FK FOREIGN KEY (Current_Course_ID) REFERENCES Current_Course(Current_Course_ID),
CONSTRAINT Allocation_Student_ID_FK FOREIGN KEY (Student_ID) REFERENCES Allocated_Student(Student_ID)
    );


--Insert Values into Course_Type--
INSERT INTO Course_Type VALUES ('PYT101','Introduction to Python','1500');
INSERT INTO Course_Type VALUES ('ART101','Introduction to Artificial Intelligence','1500');
INSERT INTO Course_Type VALUES ('BUS101','Introduction to Business Analysis','1500');
INSERT INTO Course_Type VALUES ('MMO202','Mathematical Modelling In SAS','2000');
INSERT INTO Course_Type VALUES ('ADA202','Advanced Data Analysis','2000');
INSERT INTO Course_Type VALUES ('MAL202','Machine Learning','2000');
INSERT INTO Course_Type VALUES ('EPR202','Essentials In Project Managment','2000');
INSERT INTO Course_Type VALUES ('ACC202','Advanced Cloud Computing','2000');
INSERT INTO Course_Type VALUES ('CYB101','Introduction to Cybersecurity','1500');
INSERT INTO Course_Type VALUES ('DAM101','Data Mining','2000');


--Insert Values into Room Table--
INSERT INTO Room VALUES ('R202','COMPUTING LAB');
INSERT INTO Room VALUES ('R204','CONFERENCE HALL');
INSERT INTO Room VALUES ('R206','LECTURE HALL B');
INSERT INTO Room VALUES ('R208','MEETING ROOM 2');
INSERT INTO Room VALUES ('R210','LECTURE HALL A');
INSERT INTO Room VALUES ('R212','MEETING ROOM 1');


--Insert Values into Trainer Table--
INSERT INTO Trainer VALUES ('T001', 'JOEL HENS','Introduction to Python');
INSERT INTO Trainer VALUES ('T002', 'BRADLEY OWENS','Introduction to Artificial Intelligence');
INSERT INTO Trainer VALUES ('T003', 'NEILS BOHR','Introduction to Business Analysis');
INSERT INTO Trainer VALUES ('T004', 'AMANDA NOEL','Mathematical Modelling In SAS');
INSERT INTO Trainer VALUES ('T005', 'ZAC ORGI', 'Advanced Data Analysis');
INSERT INTO Trainer VALUES ('T006', 'EVANS FRANK','Machine Learning');
INSERT INTO Trainer VALUES ('T007', 'JAMES GARDNER','Essentials In Project Management');
INSERT INTO Trainer VALUES ('T008', 'LOI HUI','Advanced Cloud Computing');
INSERT INTO Trainer VALUES ('T009', 'KIGAN HENRY','Introduction to Cybersecurity');
INSERT INTO Trainer VALUES ('T010', 'JOSEPH HILLS','Data Minig');


--Insert Values into Allocated_Student Table--
INSERT INTO Allocated_Student VALUES ('103122','Amanda Giza');
INSERT INTO Allocated_Student VALUES ('103124','Lola Klitz');
INSERT INTO Allocated_Student VALUES ('103126','Milli Mall');
INSERT INTO Allocated_Student VALUES ('103128','Derrick Oppong');
INSERT INTO Allocated_Student VALUES ('103130','John Bull');
INSERT INTO Allocated_Student VALUES ('103132','Han Marfo');
INSERT INTO Allocated_Student VALUES ('103134','Milli Mall');
INSERT INTO Allocated_Student VALUES ('103136','Burnli Mills');
INSERT INTO Allocated_Student VALUES ('103138','Baah Eben');
INSERT INTO Allocated_Student VALUES ('103140','Ebert Right');
INSERT INTO Allocated_Student VALUES ('103150','Antwi Danso');
INSERT INTO Allocated_Student VALUES ('103152','Hyda Sam');
INSERT INTO Allocated_Student VALUES ('103154','Afua Lily');
INSERT INTO Allocated_Student VALUES ('103158','Anas Anthony');
INSERT INTO Allocated_Student VALUES ('103144','Jonas Kyle');
INSERT INTO Allocated_Student VALUES ('103160','Jimy Chow');
INSERT INTO Allocated_Student VALUES ('103162', 'Levi Dankyi');
INSERT INTO Allocated_Student VALUES ('103164','Nathan Kwow');
INSERT INTO Allocated_Student VALUES ('103168','Eturu Prisca');
INSERT INTO Allocated_Student VALUES ('103170','Beden Joe');
INSERT INTO Allocated_Student VALUES ('103172','Loel Donda');
INSERT INTO Allocated_Student VALUES ('103174','Megan Menu');
INSERT INTO Allocated_Student VALUES ('103176','Muni Maya');
INSERT INTO Allocated_Student VALUES ('103178','Abass Lekwi');
INSERT INTO Allocated_Student VALUES ('103180','Sam Dugan');
INSERT INTO Allocated_Student VALUES ('103182','Willie Hem');
INSERT INTO Allocated_Student VALUES ('103184','Alan Altman');
INSERT INTO Allocated_Student VALUES ('103186','Desire Wan');
INSERT INTO Allocated_Student VALUES ('103188','Suit Mann');
INSERT INTO Allocated_Student VALUES ('103190','Alex Rodd');

--Insert into Current_Course_Table--
INSERT INTO Current_Course VALUES ('AC01','PYT101','T001','R202','10-Jun-23','10-Jun-23','5','10');
INSERT INTO Current_Course VALUES ('AC02','ART101','T002','R204','10-Jun-23','13-Jun-23','3','20');
INSERT INTO Current_Course VALUES ('AC03','BUS101','T003','R206','15-Jul-23','18-Jul-23','3','20');
INSERT INTO Current_Course VALUES ('AC04','MMO202','T004','R208','20-Jun-23','25-Jun-23','5','20');
INSERT INTO Current_Course VALUES ('AC05','ADA202','T005','R210','03-Aug-23','6-Aug-23','3','10');
INSERT INTO Current_Course VALUES ('AC06','MAL202','T006','R212','30-Dec-23','2-Jan-24','3','10');
INSERT INTO Current_Course VALUES ('AC07','EPR202','T007','R202','04-Apr-23','9-Apr-23','5','10');
INSERT INTO Current_Course VALUES ('AC08','ACC202','T008','R204','10-Apr-23','15-Apr-23','5','20');
INSERT INTO Current_Course VALUES ('AC09','CYB101','T009','R206','07-May-23','12-May-23','5','10');
INSERT INTO Current_Course VALUES ('AC10','DAM101','T010','R208','02-Oct-23','5-Oct-24','3','10');
INSERT INTO Current_Course VALUES ('AC11','PYT101','T001','R202','02-Feb-23','7-Feb-24','5','10');
INSERT INTO Current_Course VALUES ('AC12','ART101','T002','R204','05-Mar-23','08-Mar-24','3','10');
INSERT INTO Current_Course VALUES ('AC13','MMO202','T004','R208','08-Jan-23','11-Jan-24','3','10');
INSERT INTO Current_Course VALUES ('AC14','MAL202','T006','R212','05-Feb-23','08-Feb-24','3','10');
INSERT INTO Current_Course VALUES ('AC15','EPR202','T007','R202','04-Aug-24','09-Aug-24','5','20');
INSERT INTO Current_Course VALUES ('AC16','ACC202','T008','R204','23-May-23','28-May-24','5','20');
INSERT INTO Current_Course VALUES ('AC17','DAM101','T010','R208','17-Nov-23','22-Nov-24','5','10');
INSERT INTO Current_Course VALUES ('AC18','BUS101','T003','R206','14-May-23','19-May-24','5','10');


--Insert into Allocation Table--
INSERT INTO Allocation VALUES ('AL0','AC01','103122');
INSERT INTO Allocation VALUES ('AL1','AC02','103122');
INSERT INTO Allocation VALUES ('AL2','AC01','103124');
INSERT INTO Allocation VALUES ('AL3','AC02','103124');
INSERT INTO Allocation VALUES ('AL4','AC03','103126');
INSERT INTO Allocation VALUES ('AL5','AC04','103126');
INSERT INTO Allocation VALUES ('AL6','AC03','103128');
INSERT INTO Allocation VALUES ('AL7','AC04','103128');
INSERT INTO Allocation VALUES ('AL8','AC05','103130');
INSERT INTO Allocation VALUES ('AL9','AC06','103130');
INSERT INTO Allocation VALUES ('AL10','AC05','103132');
INSERT INTO Allocation VALUES ('AL11','AC06','103132');
INSERT INTO Allocation VALUES ('AL12','AC07','103134');
INSERT INTO Allocation VALUES ('AL13','AC08','103134');
INSERT INTO Allocation VALUES ('AL14','AC07','103136');
INSERT INTO Allocation VALUES ('AL15','AC08','103136');
INSERT INTO Allocation VALUES ('AL16','AC09','103138');
INSERT INTO Allocation VALUES ('AL17','AC10','103138');
INSERT INTO Allocation VALUES ('AL18','AC11','103140');
INSERT INTO Allocation VALUES ('AL19','AC10','103140');
INSERT INTO Allocation VALUES ('AL20','AC11','103128');
INSERT INTO Allocation VALUES ('AL21','AC12','103144');
INSERT INTO Allocation VALUES ('AL22','AC13','103150');
INSERT INTO Allocation VALUES ('AL23','AC14','103154');
INSERT INTO Allocation VALUES ('AL24','AC15','103170');
INSERT INTO Allocation VALUES ('AL25','AC16','103158');
INSERT INTO Allocation VALUES ('AL26','AC17','103182');
INSERT INTO Allocation VALUES ('AL27','AC18','103164');







QUESTION 1:

SELECT Course_Code, Start_date 
FROM Current_Course 
ORDER BY Start_Date;
 
 



QUESTION 2:
Select * 
FROM Course_Type
WHERE Course_Title LIKE '%Introduction%';

 
























QUESTION 3:
--Most Expensive--
SELECT * FROM Course_Type WHERE Course_Cost = (SELECT MAX(Course_Cost) FROM (Course_Type));

 

---Least Expensive--
SELECT * FROM Course_Type WHERE Course_Cost = (SELECT MIN(Course_Cost) FROM (Course_Type));

 








QUESTION 4:

SELECT a.Current_Course_ID as "Currently Allocated Courses",
ct.Course_Title as "Course Title",
COUNT(*)"Number of Students"
FROM Allocation a,Current_Course cc,Course_Type ct
WHERE a.Current_Course_ID = cc.Current_Course_ID
AND cc.Course_Code = ct.Course_Code
GROUP BY a.Current_Course_ID,cc.Course_Code,ct.Course_Title 
ORDER BY a.Current_Course_ID;

 
 






QUESTION 5:

SELECT cc.Course_Code,ct.Course_Title,cc.Start_Date
FROM Current_Course cc, Course_Type ct
WHERE cc.Course_Code = ct.Course_Code AND Start_Date BETWEEN '01-APR-23' AND '31-DEC-23';

 
 








QUESTION 6:

SELECT course_Code as "courses Code", count(Current_Course_ID) as "Number of Current Courses Running"
FROM Current_Course
WHERE start_date BETWEEN '01-Jan-2023' AND '31-Dec-2023'
GROUP BY course_Code;

 




QUESTION 7:

SELECT r.Room_No, r.Room_Type, t.Trainer_Name as Trainer, c.Course_Code, c.Start_Date, c.End_date
FROM Room r
LEFT JOIN Current_Course c on r.Room_No = c.Room_No
LEFT JOIN Trainer t on t.Trainer_ID = c.Trainer_ID;

 
 






QUESTION 8:

SELECT a.Student_ID, a.Student_Name, c.Course_Code, c.Start_Date
FROM Allocated_Student a
LEFT JOIN Allocation b on a.Student_ID = b.Student_ID
LEFT JOIN Current_Course c ON c.Current_Course_ID = b.Current_Course_ID
WHERE c.start_date = '20-JUN-23';

 














QUESTION 9:

SELECT
cc.Course_Code as "COURSE CODE",
c.Start_Date as "Run Date",
cc.Course_Cost, 
Count(ca.Student_ID) as "No of Students",
(cc.Course_Cost * Count(ca.Student_ID)) as "Revenue"
FROM Course_Type cc
LEFT JOIN Current_Course c on cc.Course_Code = c.Course_Code
LEFT JOIN Allocation ca on c.Current_Course_ID = ca.Current_Course_ID
GROUP BY cc.Course_Code, c.Start_Date, cc.Course_Cost;


 
 
