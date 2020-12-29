# Database Documentation

The database

This databaseis made to manage the data needed for an Educational Blog site. It is consist of five (5) tables which are students, borrows, books, authors and types of book. In this database I decided that this was the database I would make because I knew it would used in school. In this database, here you will find out who goes to the library and who does not. In this database only admin can login to monitor students. Because in my experience at the Assupmtion, students first need to borrow books before the librarian sign the clearance. And this is good example for students to get used reading books and not just based on the internet. This system is operated in a RDBMS (Relational Database Management System) called MySQL using the PhpMyAdmin platform.

# Entity Relationship Diagram (EDR)

An entity relationship diagram describes interrelated things of interest in a specific domain of knowledge. A ERD is composed of entity types and specifies relationship that can exist between entities.

![entity relationship](https://user-images.githubusercontent.com/73123638/103289471-47dde500-4a22-11eb-82f3-434f5b8e6212.png)

# Entity Tables and Description

Students- is responsible for storing necessary data upon entering library.

Borrows- is responsible for storing necessary data when students borrowed books.

Books- is responsible for storing necessary data upon the books was borrowed.

Authors- is responsible for storing necessary data upon the books was delivered at library and who are the author of the book.

Types- is responsible for storing necessary data of what types of books it is.

# Database Dependency Diagram 

A set of functional Dependencies for a data model can be documented in a Functional Dependency Diagram. In a Functional Dependency Diagram each attribute is shown in a rectangle with arrow indicating the direction of the dependency.

![ddd](https://user-images.githubusercontent.com/73123638/103289746-e10cfb80-4a22-11eb-8a90-e41fee16b215.png)

# Queries associated with the database

Here are a list of queries with their sample output from the DBRMS:

1.	Query

Select * from books

where pageCount between 100 and 200

*It  is important for the admin to know the pageCount of each book, so that if it is returned with a defeat, students will need tp replace it.

Output:
![1](https://user-images.githubusercontent.com/73123638/103289808-131e5d80-4a23-11eb-8f22-df9bf46f3492.png)

2.  Query

Select * from students
where (class = '11' or class = '12')
and gender='M'

*This is important because here we will know how many all male students go to the library.

Output:
![2](https://user-images.githubusercontent.com/73123638/103289890-3fd27500-4a23-11eb-9eb3-c4eb0db830bc.png)

3. Query

Select * from books where pageCount=
(Select max(pageCount) from books)

*This is important to know which book has a biggest pageCount.

Output:
![3](https://user-images.githubusercontent.com/73123638/103289943-60023400-4a23-11eb-8353-80917218552e.png)

4. Query

Select distinct class
from students

*It is important for the admin to know how many classes are all in one school.

Output:
![4](https://user-images.githubusercontent.com/73123638/103289993-760ff480-4a23-11eb-8e90-f13c54afe7d8.png)

5. Query

Select class,count(*) as StudentCount 
from students 
group by class

*It is important for the admin to know how many students are in each class and for it to monitor.

Output:
![5](https://user-images.githubusercontent.com/73123638/103290029-8b851e80-4a23-11eb-884d-542cfb2909ed.png)

6. Query

Select class,gender,count(*) as StudentCount 
from students 
group by gender,class

*it is important to know how many femala and male students in every class.

Output:
![6](https://user-images.githubusercontent.com/73123638/103290064-a2c40c00-4a23-11eb-81a6-9a89a2ed6d07.png)

7. Query

select class, gender, count(*) as StudentCount 
from students where gender='F' group by gender, class

*It is important to know the list of female student and how many female in every class.

Output:
![7](https://user-images.githubusercontent.com/73123638/103290102-b8393600-4a23-11eb-8ed7-a059bace6e33.png)

8. Query

Select students.name as studentName,students.surname,books.name as BookName,takenDate 
from students 
join borrows on students.studentId = borrows.studentId 
join books on books.bookId = borrows.bookId 
where class='11'

*It is important to determined who are the students, what books and what day was it borrowed.

Output:
![8](https://user-images.githubusercontent.com/73123638/103292632-31875780-4a29-11eb-9371-2f90c219db31.png)

9. Query

Select name,surname,count(*) BookCount 
from students 
join borrows on students.studentId = borrows.studentId 
group by students.studentId,name,surname

*It is important to know what the favorite booksto read of every students.

Output:
![9](https://user-images.githubusercontent.com/73123638/103292680-45cb5480-4a29-11eb-821b-ed72ec586ffc.png)

10. Query

Select name,surname,count(*) BookCount 
from students 
join borrows on students.studentId = borrows.studentId 
group by students.studentId,name,surname
order by BookCount

*They are the list of name of students and the number of books they are sorted to read.

Output:
![10](https://user-images.githubusercontent.com/73123638/103292712-5976bb00-4a29-11eb-8c23-0dda5a2d6918.png)

11. Query

Select students.* from students 
left join borrows on students.studentId = borrows.studentId 
where borrowId is null

*It is important to know who are students who are not read books.

Output:
![11](https://user-images.githubusercontent.com/73123638/103292760-6dbab800-4a29-11eb-95a6-8175b6944fe4.png)

12. Query

Select name,surname,takenDate from students 
join borrows on students.studentId = borrows.studentId

*It is important to know when the students borrowed books.

Output:
![12](https://user-images.githubusercontent.com/73123638/103292803-82974b80-4a29-11eb-90d1-82e76e62ce83.png)

13. Query

Select students.name,surname,books.name,takenDate 
from students 
join borrows on students.studentId = borrows.studentId 
join books on books.bookId = borrows.bookId

*It is important because we need to record what book are borrowed and the time was borrowed.

Output:
![13](https://user-images.githubusercontent.com/73123638/103292832-9773df00-4a29-11eb-907b-9d98e201dc9a.png)

14. Query
	
Select name,surname,takenDate 
from students 
left join borrows on students.studentId = borrows.studentId

*It is important because we need to monitor our student if they read the books or not.

Output:
![14](https://user-images.githubusercontent.com/73123638/103292874-b3778080-4a29-11eb-82c4-add392618b3f.png)

15. Query

Select * from books 
where pageCount=(Select max(pageCount) from books)

*This is the list of book with most page number.

Output:
![15](https://user-images.githubusercontent.com/73123638/103292995-f20d3b00-4a29-11eb-8834-b2078fe19c9c.png)

16.Query

Select * from students 
where studentId not in 
(Select studentId from borrows)

*In this query this is the students who have not read books.

Output:
![16](https://user-images.githubusercontent.com/73123638/103292914-ca1dd780-4a29-11eb-9aae-d4291d7b50f1.png)

17. Query
	
  Insert into authors(name,surname) to authors table
	
  *It is important because if there are new books it will be immedietely add on the list.
	
  Output:
	![17](https://user-images.githubusercontent.com/73123638/103293043-0fdaa000-4a2a-11eb-92e5-875c12754005.png)

18. Query

Select students.name as studentName,students.surname,books.name as BookName,takenDate,types.name as TypeName, authors.name as AuthorName,authors.surname as AuthorSurname 
from students 
join borrows on students.studentId = borrows.studentId 
join books on books.bookId = borrows.bookId 
join types on books.typeId = types.typeId 
join authors on authors.authorId = books.authorId

*This is the list of all students name,surname, takenbook, the taken date and authors.

Output:
![18](https://user-images.githubusercontent.com/73123638/103293093-2aad1480-4a2a-11eb-8818-2649cee6804a.png)

19.Query

Select students.name as studentName,students.surname,books.name as BookName,takenDate,types.name as TypeName 
from students 
join borrows on students.studentId = borrows.studentId 
join books on books.bookId = borrows.bookId 
join types on books.typeId = types.typeId

*This is the list of all student name, surname, taken date, taken book, and the book’s type.

Output:
![19](https://user-images.githubusercontent.com/73123638/103293148-431d2f00-4a2a-11eb-8466-6348258db969.png)

20.Query
	
Delete from students 
where studentId not in (Select studentId from borrows)

*It is important to delete student who are not entering school library becauseit is not good in the system. 

Output:
![20](https://user-images.githubusercontent.com/73123638/103293188-59c38600-4a2a-11eb-8b34-a38247b02cee.png)

Happy New Year and Godbless po!


