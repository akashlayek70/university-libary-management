# university-libary-management

/* Create the EMPLOYEE table */

CREATE TABLE EMPLOYEE (	


EmployeeID CHAR (3) NOT NULL,

EmployeeName VARCHAR (100) NOT NULL,

EmployeeAddress VARCHAR (100) NOT NULL,

EmployeeEmail VARCHAR (100) NOT NULL,
EmployeeBlok  VARCHAR (100) NOT NULL,

			

CONSTRAINT EmployeePK	PRIMARY KEY (EmployeeID)							

);



/*Insert records into EMPLOYEE*/


INSERT INTO EMPLOYEE(EmployeeID , EmployeeName , EmployeeAddress,EmployeeEmail,EmployeeBlok)
VALUES
  ('01081', 'Basar Iqbal', 'saltlake sector-3','iqbalbashar420@gmail.com','Block-1'),
  ('01080', 'Raju Mondal', 'saltlike sector-3','mandalr70@gmail.com','Block-4'),
  ('01079', 'Arya Kanta',  'saltlake sector-3','kantaarya1@gmail.com','Block-5'),
  ('01078', 'Avisikta Das','saltlake sector-3','siktavi50@gmail.com', 'Block-3'),
  ('01077', 'Abhi   Roy',  'saltlake sector-3','royabhi49@gmail.com','Block-2');


			

/* Create the STUDENT table */

CREATE TABLE STUDENT (	


StudentID CHAR (5) NOT NULL,

StudentName VARCHAR (100) NOT NULL,

StudentAddress VARCHAR (150)  NULL,

StudentEmail VARCHAR (50) NOT NULL,

			

CONSTRAINT StudentPK	PRIMARY KEY (StudentID)
						
);	


/*Insert records into STUDENT*/



INSERT INTO STUDENT(StudentID , StudentName, StudentAddress,StudentEmail)
VALUES 
('10001', 'Souvik Saha',  '32-SC Mullick Road','sousa@ju.edu'),
('10002', 'Saheli Ghosh', '32-SC Mullick Road','sag@ju.edu'),
('10003', 'Brian Paul',   '32-SC Mullick Road','brian@ju.edu'),
('10004', 'subha Layek',  '32-sc Mullick Road','layeks70@ju.edu'),
('10005', 'Kevin Ronald', '32-SC Mullick Road','ronaldkelvin@cat.edu');

	

/* Create the PUBLISHER table */

CREATE TABLE PUBLISHER (	


PublisherID CHAR (5) NOT NULL,

PublisherName VARCHAR (100) NOT NULL,

PublisherAddress VARCHAR (150)  NULL,

PublisherEmail VARCHAR (50) NOT NULL,

Publishercity VARCHAR(100) 

			

CONSTRAINT PublisherPK	PRIMARY KEY (PublisherID)							

);


/*Insert records into PUBLISHER*/


INSERT INTO PUBLISHER(PublisherID , PublisherName , PublisherAddress,PubEmail,Publishercity)
VALUES 
('20001', 'Ryan Jason', '352 Palmer Road','rj@cat.edu','London'),
('20002', 'Gary Eric', '141 Washington Ave','ge@cat.edu','New York'),
('20003', 'Larry Scott', '279 Troy Road','ls@cat.edu','california'),
('20004', 'Rachel Debra', '4975 Transit Road','rd@cat.edu','Washington DC'),
('20005', 'Ruth Janet', '161 Berlin Road','rj@cat.edu',');




/* Create the AUTHOR table */

CREATE TABLE AUTHOR (	



AuthorID CHAR (5) NOT NULL,

AuthorName VARCHAR (100) NOT NULL,

AuthorAddress VARCHAR (100)  NULL,

AuthorEmail VARCHAR (100) NOT NULL,

AuthorPhnumber CHAR (100) NOT NULL,			

CONSTRAINT AuthPK PRIMARY KEY (AuthorID)						

);


/*Insert records into AUTHOR*/


INSERT INTO AUTHOR(AuthorID , AuthorName , AuthorAddress ,AuthorEmail, AuthorPhnumber)
VALUES 
('30001', 'Jose Henry', '235 Queen St','jh@ju.edu','1234567890'),
('30002', 'Nathan Douglas', '164 Danbury Rd','nd@ju.edu','2457895320'),
('30003', 'Victoria Olivia', '80 Town Line Rd','vo@ju.edu','1356786796'),
('30004', 'Kyle Walter', '970 Torringford Street','kw@ju.edu','4678933476'),
('30005', 'Jeremy Ethan', '844 No Colony Road','je@ju.edu','2389812675');



/* Create the BOOK table */

CREATE TABLE BOOK (	


BookID CHAR (5) NOT NULL,

BookName VARCHAR (100) NOT NULL,

BookPages INT  NOT NULL,

ISBNNum VARCHAR (100) NOT NULL,

StudentID CHAR (5)  NULL,

EmployeeID CHAR (5)  NULL,

PublisherID CHAR (5) NOT NULL,

			

CONSTRAINT BookPK   PRIMARY KEY (BookID),



CONSTRAINT BookFK1  FOREIGN KEY (StudentID) REFERENCES STUDENT (StudentID)

								ON UPDATE CASCADE

								ON DELETE NO ACTION	

,

CONSTRAINT BookFK2  FOREIGN KEY (EmployeeID) REFERENCES EMPLOYEE (EmployeeID)

								ON UPDATE CASCADE

								ON DELETE NO ACTION

,								

CONSTRAINT BookFK3  FOREIGN KEY (PublisherID) REFERENCES PUBLISHER (PublisherID)

								ON UPDATE CASCADE

								ON DELETE NO ACTION							

);



/*Insert records into BOOK*/


INSERT INTO BOOK(BookID , BookName ,BookPages,ISBNNum, StudentID ,EmployeeID,PublisherID )
VALUES 
('40001', 'The Bell Jar', '110','817525766-0','10001','01081','20001'),
('40002', 'Calvin', '230','716578901-4','10002','01080','20002'),
('40003', 'Displacement', '360','998456723-4','10003','01079','20003'),
('40005', 'The Fifth Risk', '650','756489762-1','10005','01077','20005');




/* Create the BOOK_AUTH table */

CREATE TABLE BOOK_AUTH (	


BookAuthorID CHAR (5) NOT NULL,

BookID CHAR (5) NOT NULL,

AuthorID CHAR (5) NOT NULL,

			

CONSTRAINT BookAuthPK	PRIMARY KEY (BookAuthID),



CONSTRAINT BookAuthFK1	FOREIGN KEY (BookID) REFERENCES BOOK (BookID)

								ON UPDATE CASCADE

								ON DELETE NO ACTION	

,

CONSTRAINT BookAuthkFK2	FOREIGN KEY (AuthorID) REFERENCES AUTHOR (AuthorID)

								ON UPDATE CASCADE

								ON DELETE NO ACTION

					
);


/*Insert records into BOOK_AUTH*/


INSERT INTO BOOK_AUTH (BookAuthorID  ,BookID, AuthorID  )
VALUES 
('50001', '40001','30001');
('50002', '40002','30002');
('50003', '40003','30003');
('50004', '40004','30004');
('50005', '40005','30005');
