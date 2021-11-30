
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


