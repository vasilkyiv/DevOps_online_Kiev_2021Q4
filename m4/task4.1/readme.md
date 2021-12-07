
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 04 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m4) 
===========================================================================
> # [TASK_4.1 04 DBA](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m4)

> # [PART 1](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m4)

> 1. Download MySQL server for your OS on VM.

> 2. Install MySQL server on VM.

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)

> 3. Select a subject area and describe the database schema, (minimum 3 tables)

[![*Report in screenshots*](shreenshot/2.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)

**************************************************

# DDL – Data Definition Language
Data Definition Language (DDL) – это группа операторов определения данных. Другими словами, с помощью операторов, входящих в эту группы, мы определяем структуру базы данных и работаем с объектами этой базы, т.е. создаем, изменяем и удаляем их.

В эту группу входят следующие операторы:

### CREATE – используется для создания объектов базы данных;
### ALTER – используется для изменения объектов базы данных;
### DROP – используется для удаления объектов базы данных.

# DML – Data Manipulation Language
Data Manipulation Language (DML) – это группа операторов для манипуляции данными. С помощью этих операторов мы можем добавлять, изменять, удалять и выгружать данные из базы, т.е. манипулировать ими.

В эту группу входят самые распространённые операторы языка SQL:

### SELECT – осуществляет выборку данных;
### INSERT – добавляет новые данные;
### UPDATE – изменяет существующие данные;
### DELETE – удаляет данные.

# DCL – Data Control Language
Data Control Language (DCL) – группа операторов определения доступа к данным. Иными словами, это операторы для управления разрешениями, с помощью них мы можем разрешать или запрещать выполнение определенных операций над объектами базы данных.

Сюда входят:

### GRANT – предоставляет пользователю или группе разрешения на определённые операции с объектом;
### REVOKE – отзывает выданные разрешения;
### DENY– задаёт запрет, имеющий приоритет над разрешением.


# TCL – Transaction Control Language
Transaction Control Language (TCL) – группа операторов для управления транзакциями. Транзакция – это команда или блок команд (инструкций), которые успешно завершаются как единое целое, при этом в базе данных все внесенные изменения фиксируются на постоянной основе или отменяются, т.е. все изменения, внесенные любой командой, входящей в транзакцию, будут отменены.

Группа операторов TCL предназначена как раз для реализации и управления транзакциями. Сюда можно отнести:

### BEGIN TRANSACTION – служит для определения начала транзакции;
### COMMIT TRANSACTION – применяет транзакцию;
### ROLLBACK TRANSACTION – откатывает все изменения, сделанные в контексте текущей транзакции;
### SAVE TRANSACTION – устанавливает промежуточную точку сохранения внутри транзакции.
***************************************

> 4. Create a database on the server through the console.

[![*Report in screenshots*](shreenshot/3.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)

> 5. Fill in tables.

**************************
# DDL – Data Definition Language
Data Definition Language (DDL) – это группа операторов определения данных. Другими словами, с помощью операторов, входящих в эту группы, мы определяем структуру базы данных и работаем с объектами этой базы, т.е. создаем, изменяем и удаляем их.

В эту группу входят следующие операторы:

### CREATE – используется для создания объектов базы данных;
### ALTER – используется для изменения объектов базы данных;
### DROP – используется для удаления объектов базы данных.
************************

     select user, host from mysql.user;

     show CREATE DATABASE ostapenkot4;

     CREATE DATABASE ostapenkot4;

     drop database ostapenkot4;

     CREATE DATABASE ostapenkot4;

     use ostapenkot4;

     show tables;

     desc student;
     desc teacher;

     show columns from teacher;
     show columns from student;

     create table student(
          studentID int not null auto_increment primary key, 
          studentName varchar(45) not null
     ) ;

     show create table teacher;

     create table teacher(
          teacherID int not null auto_increment primary key, 
          teacherName varchar(45) not null 
     )  ;  

     

     show create table lesson;


          CREATE TABLE IF NOT EXISTS LESSON (
               lessonID INT NOT NULL AUTO_INCREMENT,
               lessonNAME VARCHAR(45) NOT NULL,
               STUDENT_studentID INT NOT NULL,
               TEACHER_teacherID INT NOT NULL,
               PRIMARY KEY (lessonID),
          
          INDEX fk_LESSON_STUDENT_idx (STUDENT_studentID ASC) ,
          INDEX fk_LESSON_TEACHER1_idx (TEACHER_teacherID ASC) ,
          
                         CONSTRAINT fk_LESSON_STUDENT 
                              FOREIGN KEY (STUDENT_studentID)
                                    REFERENCES STUDENT (studentID)
                                             ON DELETE NO ACTION  ON UPDATE NO ACTION,
          
                         CONSTRAINT fk_LESSON_TEACHER
                               FOREIGN KEY (TEACHER_teacherID)
                                    REFERENCES TEACHER (teacherID)
                                              ON DELETE NO ACTION  ON UPDATE NO ACTION
          ) ;

     ALTER TABLE `lesson` DROP COLUMN `date`;

*******************************
### mysql --console -uroot -p < c:\mysql\world.sql 
### - [importing world.sql database from https://dev.mysql.com/doc/index-other.html](https://dev.mysql.com/doc/index-other.html)

### SELECT

     select left(name, 10), continent 
     from country;

     select * from country limit 5;

     select distinct continent materyk from country;

     select  continent from country group by continent;

     select distinct continent, region, sum(population) from country group by 1,2 with rollup;

     select distinct continent as 'континент' from country;

     select left(name,10), population from country limit 5 offset 2;

     select code,left(name,10) from country limit 5;

> 6. Construct and execute SELECT operator with WHERE, GROUP BY and ORDER BY.


******************************
# DML – Data Manipulation Language
     Data Manipulation Language (DML) – это группа операторов для манипуляции данными. С помощью этих операторов мы можем добавлять, изменять, удалять и выгружать данные из базы, т.е. манипулировать ими.

В эту группу входят самые распространённые операторы языка SQL:

### SELECT – осуществляет выборку данных;
### INSERT – добавляет новые данные;
### UPDATE – изменяет существующие данные;
### DELETE – удаляет данные.
******************************

## SELECT  ... where

     select code,left(name,10) from country where code = 'ALB';

     select code,left(name,10), population from country where surfacearea > 1000000 and surfacearea < 4000000;

     select code,left(name,10), population from country where surfacearea between 1000000 and 4000000;

     select name, district from city where name like 'Ky%';

     select name, district from city where name like '__i%';

     select name, population from city where name in ('Kyiv', 'Lviv');

     select name, population from city order by name desc limit 50; 

     select name, population from city order by population  limit 50;  

     select name, population from city order by population  desc limit 50;

     select name, population from city order by rand()   limit 5;

     select name, population from city order by rand()  desc limit 5;

     select continent from country group by continent;

     select continent, sum(population) from country group by 1;

     select continent, region, sum(population) from country order by 1,2 group by 1,2;

     select continent, region, sum(population) from country group by 1,2 order by 1,2;

     select continent, region, sum(population) from country group by 1,2 with rollup;

     select continent, sum(population) from country group by 1 having sum(population) > 400000000;

     select continent, sum(population)  into outfile 'c:/mysql/query.txt' from country group by 1 having sum(population) > 400000000;

     select sum(population) into @count from country;
     select @count;

## insert  ... 
**************************************************

                    CREATE DATABASE ostapenkot4;

                    create table student(
                              studentID int not null auto_increment primary key, 
                              studentName varchar(45) not null
                    ) ;

     insert  into student values (null, 'student1'),
     (null,'Student2'),
     (null,'Student3'),
     (null,'Student4'),
     (null,'Student5'),
     (null,'Student6');

     select * from student;
*****************************************************************************
                         create table teacher(
                                   teacherID int not null auto_increment primary key, 
                                   teacherName varchar(45) not null 
                              )  ;  
     insert  into teacher values (null, 'teacher1'),
     (null,'teacher2'),
     (null,'teacher3'),
     (null,'teacher4'),
     (null,'teacher5'),
     (null,'teacher6'); 

     select * from teacher;
*****************************************************************************
     CREATE TABLE IF NOT EXISTS `ostapenkot4`.`LESSON` (
     `lessonID` INT NOT NULL AUTO_INCREMENT,
     `lessonNAME` VARCHAR(45) NOT NULL,
     `STUDENT_studentID` INT NOT NULL,
     `TEACHER_teacherID` INT NOT NULL,
     PRIMARY KEY (`lessonID`, `TEACHER_teacherID`),

     INDEX `fk_LESSON_STUDENT_idx` (`STUDENT_studentID` ASC) VISIBLE,
     INDEX `fk_LESSON_TEACHER1_idx` (`TEACHER_teacherID` ASC) VISIBLE,

     CONSTRAINT `fk_LESSON_STUDENT`
     FOREIGN KEY (`STUDENT_studentID`)
     REFERENCES `ostapenkot4`.`STUDENT` (`studentID`)
     ON DELETE NO ACTION
     ON UPDATE NO ACTION,

     CONSTRAINT `fk_LESSON_TEACHER1`
     FOREIGN KEY (`TEACHER_teacherID`)
     REFERENCES `ostapenkot4`.`TEACHER` (`teacherID`)
     ON DELETE NO ACTION
     ON UPDATE NO ACTION)

     select * from lesson;


     INSERT INTO lesson (lessonNAME,STUDENT_studentID,TEACHER_teacherID) VALUES ("linux",1,1);

     select * from teacher 
     left join lesson
     on teacher.teacherid=lesson.teacher_teacherid;

     select user from mysql.user;

     INSERT INTO student select null, user from mysql.user;

     load data 
               infile 'c:/mysql/folder/data.txt' 
               into table  student
               fields terminated by ','
               lines terminated by '\n'

     select * from student order by studentid desc limit 5;

## update  & replace

     UPDATE  student
     SET studentName = studentName +'100'
     WHERE studentID = 1;

     select * from student;

     UPDATE  teacher
     SET teacherName = column (teacherName) +'100'
     WHERE teacherID = 1;
     select * from teacher;

     REPLACE INTO student VALUES (2, 'student20000');
     select * from student;

     REPLACE INTO teacher VALUES (2, 'teacher2220000');
     select * from teacher where teacherID = 2;

 ## delete  & load XML

     mysql -uroot -pmysql ostapenkot4 --xml -e 'SELECT * FROM ostapenkot4.student' > c:/mysql/folder/student.xml

     mysql -uroot -pmysql ostapenkot4 --html -e 'SELECT * FROM ostapenkot4.student' > c:/mysql/folder/student.html

     delete from student 
     where studentid = '3';
     select * from student;

         delete from student 
         order by studentid desc
          limit  1;
          
     select  studentid
     from student
     order by studentid desc
     limit 5;

     LOAD XML INFILE 'c:/mysql/folder/student.xml' INTO TABLE student;
************************************
## functions
# [man](https://dev.mysql.com/doc/refman/8.0/en/aggregate-functions.html)

select avg(LifeExpectancy) from country;

select count(LifeExpectancy) from country;

select count(code) from country;

select count(*) from country;

select count(distinct continent) from country;

select group_concat(name)
from country
where population between 10000 and 50000;

show warnings;

select max(surfacearea) from country;

select name, max(surfacearea) 
from country
group by name;

select continent, region, max(surfacearea) 
from country
group by 1,2;

select name, surfacearea 
from country
order by 2 desc 
limit 1;

select min(surfacearea) from country;

select continent,  sum(surfacearea) 
from country
group by continent;

## forign key
# [man](https://dev.mysql.com/doc/refman/8.0/en/create-index.html) [man](https://dev.mysql.com/doc/refman/8.0/en/create-table-foreign-keys.html)
***************************************
drop tables if not exist parent;
drop tables if not exist child;

CREATE TABLE parent (
    id INT NOT NULL,
    PRIMARY KEY (id)
) ENGINE=INNODB;

CREATE TABLE child (
    id INT, parent_id INT, INDEX par_ind (parent_id), 
    FOREIGN KEY (parent_id) REFERENCES parent(id) ON DELETE CASCADE
) ENGINE=INNODB;

insert into parent values (234), (238);
insert into child values (1,234), (2,234), (3,238);

select * from parent;
select * from child;

delete from child where id=3;
delete from parent where id=234;
***************************************

drop table if exists parent;
drop table if  exists child;

CREATE TABLE parent (
    id INT NOT NULL,
    PRIMARY KEY (id)
) ENGINE=INNODB;

CREATE TABLE child (
    id INT,
    parent_id INT, INDEX par_ind (parent_id), 
    FOREIGN KEY (parent_id)  REFERENCES parent(id) ON DELETE RESTRICT 
) ENGINE=INNODB;

insert into parent values (234), (238);
insert into child values (1,234), (2,234), (3,238);

select * from parent;
select * from child;

delete from child where id=3;
delete from parent where id=234;

show create table child;
*****************************************
drop table if exists parent;
drop table if  exists child;

CREATE TABLE parent (
    id INT NOT NULL,
    PRIMARY KEY (id)
) ENGINE=INNODB;

CREATE TABLE child (
    id INT,
    parent_id INT, INDEX par_ind (parent_id), 
    FOREIGN KEY (parent_id)  REFERENCES parent(id) ON DELETE set null 
) ENGINE=INNODB;

insert into parent values (234), (238);
insert into child values (1,234), (2,234), (3,238);

select * from parent;
select * from child;

delete from child where id=3;
delete from parent where id=234;

show create table child;

https://www.youtube.com/watch?v=4lYs-LsgY0c

https://www.youtube.com/watch?v=fiO9XNOakf8&t=217s

************************************
# JOIN
select code, name, capital
from country
order by rand()
limit 1;

 SAU  | Saudi Arabia |    3173


select id, ci.name
from city ci inner join country co
on id = capital 
where co.name = 'Turkey';

select id, ci.countrycode, ci.name
from city ci inner join country co
on id = capital 
where co.name = 'Turkey';

select language
from city ci inner join countrylanguage cl
using (countrycode)
where ci.name = 'Ankara';

************************************
CREATE TABLE costumer (
    id INT NOT NULL,
    firstName varchar(100),
    PRIMARY KEY (id)
) ENGINE=INNODB;

CREATE TABLE order (
    id INT,
    costumer_id INT, INDEX costumer_ind (costumer_id), 
    FOREIGN KEY (costumer_id)  REFERENCES costumer(id) ON DELETE set null 
) ENGINE=INNODB;

**********************************
use world;
CREATE TABLE costumer (
    idcostumer INT auto_increment NOT NULL,
    firstName varchar(100),
    PRIMARY KEY (idcostumer)
) ENGINE=INNODB;

CREATE TABLE `order` (
    idorder INT auto_increment,
    costumer_id INT, 
    PRIMARY KEY (idorder)
) ENGINE=INNODB;
desc costumer;
desc `order`;

select id, ci.name 
from city ci inner join country co
on id = capital 
where co.name = 'Turkey';

select id, ci.name 
from city ci inner join country co
using id = capital 
where co.name = 'Turkey';

select id, countrycode, ci.name 
from city ci inner join country co
on id = capital 
where co.name = 'Turkey';

select language 
from city ci inner join countrylanguage co
using (countrycode)
where ci.name = 'Ankara';

********************** 

use ostapenkot4;

drop table if exists costomer; 
drop table if exists `order`; 

CREATE TABLE costomer (
    idcostomer INT auto_increment NOT NULL,
    firstName varchar(100),
    PRIMARY KEY (idcostomer)
) ENGINE=INNODB;

CREATE TABLE `order` (
    idorder INT auto_increment,
    costomer_id INT, 
    PRIMARY KEY (idorder)
) ENGINE=INNODB;
desc costomer;
desc `order`;

insert into costomer(firstname) 
values ('Vasia'),('Petia'),('Kolia');

insert into `order`(costomer_id) 
values (1),(1),(3),(4);

select * from costomer;
select * from `order`;

select * 
from costomer left join `order`
on costomer_id =  idcostomer;

select * 
from costomer inner join `order`
on costomer_id =  idcostomer;

select * 
from costomer right join `order`
on costomer_id =  idcostomer;

select language, Percentage
from country inner join countrylanguage 
on (code = countrycode)
where name = 'Canada'
order by 2 desc;