
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 04 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m4) 
===========================================================================
> # [TASK_4.1 04 DBA](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m4)


> 1. Download MySQL server for your OS on VM.

> 2. Install MySQL server on VM.

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)

> 3. Select a subject area and describe the database schema, (minimum 3 tables)

[![*Report in screenshots*](shreenshot/2.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)

> 4. Create a database on the server through the console.

[![*Report in screenshots*](shreenshot/3.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)

> 5. Fill in tables.

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


      -- -----------------------------------------------------
          -- Table `ostapenko_task4`.`LESSON`
          -- -----------------------------------------------------
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

### SELECT  ... where

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

### insert  ... 