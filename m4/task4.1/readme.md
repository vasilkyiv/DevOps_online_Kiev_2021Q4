
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 04 DBA](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m4) 
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

###  [importing world.sql database from https://dev.mysql.com/doc/index-other.html](https://dev.mysql.com/doc/index-other.html)

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

# [man](https://dev.mysql.com/doc/refman/8.0/en/create-index.html) 

# [man](https://dev.mysql.com/doc/refman/8.0/en/create-table-foreign-keys.html)
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

 # [videotutorial](https://www.youtube.com/watch?v=4lYs-LsgY0c)

 # [videotutorial](https://www.youtube.com/watch?v=fiO9XNOakf8&t=217s)

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

******************************
use ostapenkot4;
CREATE TABLE articles (
          id INT UNSIGNED AUTO_INCREMENT NOT NULL PRIMARY KEY,
          title VARCHAR(200),
          body TEXT,
          FULLTEXT (title,body)
        ) ENGINE=InnoDB;

 INSERT INTO articles (title,body) VALUES
        ('MySQL Tutorial','DBMS stands for DataBase ...'),
        ('How To Use MySQL Well','After you went through a ...'),
        ('Optimizing MySQL','In this tutorial, we show ...'),
        ('1001 MySQL Tricks','1. Never run mysqld as root. 2. ...'),
        ('MySQL vs. YourSQL','In the following database comparison ...'),
        ('MySQL Security','When configured properly, MySQL ...');

SELECT * FROM articles
where match (title,body)
against ('database' in natural language mode);

SELECT id,left(title,10),left(body,20)
FROM articles
where match (title,body)
against ('following' in natural language mode);

CREATE TABLE my_stopwords(value VARCHAR(30)) ENGINE = INNODB;
INSERT INTO my_stopwords(value) VALUES ('system');
SET GLOBAL innodb_ft_server_stopword_table = 'world/my_stopwords';

drop  INDEX `title` ON articles;
CREATE FULLTEXT INDEX `title` ON articles(title, body);

  # [videotutorial](https://www.youtube.com/watch?v=auzGI_qal40use) 

 # Підготовлені запроси
 # [videotutorial](https://www.youtube.com/watch?v=q1OlBnn0m50)

 # [man](https://dev.mysql.com/doc/refman/5.7/en/sql-statements.html)
 # [man](https://dev.mysql.com/doc/refman/5.7/en/sql-prepared-statements.html)

PREPARE stmt1 FROM 'SELECT SQRT(POW(?,2) + POW(?,2)) AS hypotenuse';
SET @a = 3;
SET @b = 4;
EXECUTE stmt1 USING @a, @b;

DEALLOCATE PREPARE stmt1;

PREPARE stmt1 FROM 'SELECT SQRT(POW(?,2) + POW(?,2)) AS hypotenuse';
SET @a = 6;
SET @b = 8;
EXECUTE stmt1 USING @a, @b;

use world;
SET @table = 'country';
SET @query = concat('select count(*) from ', @table) ;
PREPARE stmt2 FROM @query;
EXECUTE stmt2;
DEALLOCATE PREPARE stmt2;

 # create event

 # [man] (https://dev.mysql.com/doc/refman/8.0/en/create-event.html)

drop table goods;
 create table goods (
      id int primary key auto_increment,
      title varchar(100),
      price decimal(6,2)
 );

 insert into goods values
 (null,'Tovar1',100), 
 (null,'Tovar2',200), 
 (null,'Tovar3',300), 
 (null,'Tovar4',400),
 (null,'Tovar5',500);
 
 select * from goods;

 CREATE EVENT myevent
    ON SCHEDULE AT CURRENT_TIMESTAMP + INTERVAL 1 second
    DO
      UPDATE ostapenkot4.goods SET price = price + 1.1;
      
 select * from goods;
 show variables like '%event_scheduler%';

 set global event_scheduler = 0;
 show variables like '%event_scheduler%';

  set global event_scheduler = 1;
 show variables like '%event_scheduler%';

  CREATE EVENT myevent2
    ON SCHEDULE every 10 second
    DO
      UPDATE ostapenkot4.goods SET price = price + 1.1;

 select * from goods;
alter event myevent2 disable;

 select * from goods;
alter event myevent2 enable;
 select * from goods;

 drop event myevent;
 drop event myevent2;

show variables like '%event_scheduler%';

 drop event if exists myevent;
  delimiter |
  CREATE EVENT myevent
    ON SCHEDULE every 10 second
    DO
 begin
     set @seconds = second(now());
     set @query = concat('select * into outfile \'C:/mysql/folder/goods',@seconds,'.txt\' from goods');
     prepare stmt from  @query;
     execute stmt;
 end|
 delimiter ;


  # union

select 'first';
select 'second';

select 'first'
union
select 'second';

use world;

select c1.name
from city c1 inner join city c2
on c1.name = c2.name
where c1.id <> c2.id;

select name 
from world.city
where name like 'San Jose'
union all
select 'second'
union all
select name 
from world.city
where name like 'Victoria';


select name 
from world.city
where name like 'San Jose'
union all
select 'second'
union all
(select name 
from world.city
where name like 'Victoria'
limit 2);

select 'aaaaaaaaaaa'
union
select 'bbbbbbbbbbbbbbbbbbbb'
union
select 'ccccccccccccc'
order by 1;

(select name from city order by name limit 5)
union
(select name from country order by name desc limit 5);


(
select name 
from city 
order by name 
limit 5
)
union
(
select name into outfile 'C:/mysql/folder/test18.txt'
from country 
order by name
desc limit 5);


(
select name, population 
from city 
order by name 
limit 5
)
union
(
select name, 23123
from country 
order by name
desc limit 5
)
union
(
   select 'streeng', 1000  
);


  # подзапроси
 # [man](https://dev.mysql.com/doc/refman/8.0/en/subqueries.html)

  use world;

  select name 
  from country
  where code = (
       select countrycode
       from city
       order by population desc
       limit 1
  );

  select name 
  from country
  where code in (
       select countrycode 
       from city
       where population > 5e6
       order by population desc
  );

    select name 
  from country
  where code = any (
       select countrycode 
       from city
       where population > 5e6
       order by population desc
  );


select countrycode, name
from city
order by rand()
limit 2;

-- TUR
-- USA

    select name, population
  from city
  where population > any (
       select population 
       from city
       where countrycode = 'TUR'
) and countrycode = 'USA';

   select name, population
  from city 
  where countrycode = 'USA';


      select name, population
  from city
  where population > all (
       select population 
       from city
       where countrycode = 'USA'
) and countrycode = 'TUR';


      select name, population
  from city
  where population < all (
       select population 
       from city
       where countrycode = 'TUR'
) and countrycode = 'USA';

  # create view

  
# [man](https://dev.mysql.com/doc/refman/8.0/en/create-view.html)

use world;
select database();
show tables;


select code, name, population
from country
order by 3 desc
limit 10;

drop view if exists country_top_population;
create view country_top_population
as
select code, name, population
from country
order by 3 desc
limit 10;

show tables;
show create table  country_top_population;

select * from   country_top_population;

drop view if exists asia;
create view asia
as
select * 
from country
where continent = 'Asia';

select name, population from asia;

select * from country
order by rand() limit 1;

select name, population
from country
where code = 'SJM';

drop view if exists europe;
create view europe
as
select *
from country
where continent = 'europe';

update europe
set population = population + 1e6
where code = 'DEU';

select name, population
from europe
where code = 'DEU';

 # процедури та функції
[videotutorial](https://www.youtube.com/watch?v=bMLOgmsp588

# [man](https://dev.mysql.com/doc/refman/8.0/en/create-procedure.html)

drop procedure if exists sf_foo;
delimiter $$
create procedure sp_foo()
begin
     select count(*)
     from city;
end$$
delimiter ;
call sp_foo();



drop procedure if exists get_city_by_code();
delimiter $$
create procedure get_count_city_by(in c char(3))
begin
     select count(*)
     from city
     where countrycode = c;
end$$
delimiter ;
call get_count_city_by('USA');


drop procedure if exists get_city_by_code();
delimiter $$
create procedure get_city_by_code(in c char(3), out num smallint)
begin
     select count(*)
     from city
     where countrycode = c;
end$$
delimiter ;
call get_city_by_code('USA', @some);
select @some;


drop function if exists get_city_by_code;
delimiter $$
create function get_city_by_code(c char(3))
returns smallint
DETERMINISTIC
begin
     declare num smallint default 0;
     select count(*) into num
     from city
     where countrycode = c;
     return num;
end$$
delimiter ;

select get_city_by_code('CHN');

\s
\h show
\h create function

SHOW PROCEDURE CODE get_city_by_code;

use information_schema;
show tables;

desc routines;
desc routines\G;


--show all 
select 
ROUTINE_NAME,
ROUTINE_TYPE,
ROUTINE_DEFINITION
from information_schema.routines
where ROUTINE_SCHEMA = 'world' and 
ROUTINE_TYPE = 'PROCEDURE' ;

 # процедури та функції part 2

# [man](https://dev.mysql.com/doc/refman/8.0/en/functions.html)

 # [man](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html)

 # [man](https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html)
 
 # [man](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html)


 select concat(Name,'-', Continent) 
 from country;

  select 
  floor(lifeexpectancy), 
  round(lifeexpectancy), 
  ceil(lifeexpectancy) 
  from country
  limit 10;

  SELECT DAYNAME('2021-12-29');

  show variables like '%lc%';

  set lc_time_names='ru_RU';
  show variables like '%lc%';

    set lc_time_names='en_US';
  show variables like '%lc%';

      set lc_time_names='en_US';
  show variables like '%lc%';

select if(3,4,5);


select         
          if (population < 2e7,    
                    'small ',      
                    if(population >= 1e8, 'big', 'medium')) 'krainy',
 count(*)
from country
group  by 1;


select         
          if (population < 2e7,    
                    'small ',      
                    if(population >= 1e8, 'big', 'medium')) 'krainy'
from country;

 # if case

# [videotutorial](https://www.youtube.com/watch?v=IaIHUNo5TII&list=PLOQDek48BpZFeW02dfJM77FY4Fp5ilJ6n&index=23)

# [man](https://dev.mysql.com/doc/refman/5.7/en/flow-control-statements.html)


drop function if exists fizzbuzz;
DELIMITER |
CREATE FUNCTION fizzbuzz(n smallint)
  RETURNS VARCHAR(1000)
DETERMINISTIC
  BEGIN
     set @str = '';

     if n % 3 = 0
          then set @str = concat(@str, 'fizz');
     end if;
    if n % 5 = 0
          then set @str = concat(@str, 'buzz');
     end if;
    if n % char_length(@str)
          then return @str;
     end if;

     return n;
  END |
DELIMITER ;

select fizzbuzz(3);
select fizzbuzz(5);
select fizzbuzz(15);
select fizzbuzz(7);




drop function if exists fizzbuzz2;
DELIMITER |
CREATE FUNCTION fizzbuzz2(n smallint)
  RETURNS VARCHAR(1000)
DETERMINISTIC
  BEGIN
     set @str = '';

CASE 1
      WHEN n % 3 = 0 and n % 5 = 0 THEN set @str = concat(@str, 'fizzbuzz');
      WHEN n % 3 = 0 THEN set @str = concat(@str, 'fizz');
      WHEN n % 5 = 0 THEN set @str = concat(@str, 'buzz');
      else set @str = n;
END CASE;
     
 return @str;
END |
DELIMITER ;

select fizzbuzz2(3);
select fizzbuzz2(5);
select fizzbuzz2(15);
select fizzbuzz2(7);

# цикли

drop function if exists fib;
delimiter //
CREATE function fib(n INT)
returns varchar(5000)
DETERMINISTIC
BEGIN
         SET @x1 = 0;
         SET @x2 = 1;
         SET @x3 = 0;
         set @i = 2;

create temporary table tmp(
     num int
);
          insert into tmp value(@x1);
          insert into tmp value(@x2);
         REPEAT
         
           SET @x3 = @x2 + @x1;
           insert into tmp value(@x3);
           set @x1=@x2;
           set @x2=@x3;
           set @i=@i+1;
           UNTIL @i = n END REPEAT;

         select group_concat(num) into @result from tmp;
          drop temporary table tmp;

         return @result;
END//
delimiter ;

select fib(10);


drop function if exists fib2;
delimiter //
CREATE function fib2(n INT)
returns varchar(5000)
DETERMINISTIC
BEGIN
         SET @x1 = 0;
         SET @x2 = 1;
         SET @x3 = 0;
         set @i = 2;

create temporary table tmp(
     num int
);
          insert into tmp value(@x1);
          insert into tmp value(@x2);

WHILE @i < n DO
    
           SET @x3 = @x2 + @x1;
           insert into tmp value(@x3);
           set @x1=@x2;
           set @x2=@x3;
           set @i=@i+1;
END WHILE;
         
         select group_concat(num) into @result from tmp;
          drop temporary table tmp;

         return @result;
END//
delimiter ;

select fib2(10);

************************************
************************************

# DCL – Data Control Language
Data Control Language (DCL) – группа операторов определения доступа к данным. Иными словами, это операторы для управления разрешениями, с помощью них мы можем разрешать или запрещать выполнение определенных операций над объектами базы данных.

Сюда входят:

### GRANT – предоставляет пользователю или группе разрешения на определённые операции с объектом;
### REVOKE – отзывает выданные разрешения;
### DENY– задаёт запрет, имеющий приоритет над разрешением.

> 8. Create a database of new users with different privileges. Connect to the database

CREATE USER 'ovo'@'192.168.138.69' IDENTIFIED BY 'mysql';
CREATE USER 'ovo'@'localhost' IDENTIFIED BY 'mysql';
GRANT ALL PRIVILEGES ON *.* TO 'ovo'@'localhost';
GRANT ALL ON *.* TO 'ovo'@'192.168.138.69';

GRANT SELECT ON db2.invoice TO 'jeffrey'@'localhost';
ALTER USER 'jeffrey'@'localhost' WITH MAX_QUERIES_PER_HOUR 90;

create USER 'root'@'192.168.138.69' IDENTIFIED BY 'mysql';
GRANT ALL PRIVILEGES ON *.* TO 'ovo'@'192.168.138.69';

SELECT host FROM mysql.user WHERE User = 'root';
SELECT host FROM mysql.user WHERE User = 'ovo';
CREATE USER 'root'@'192.168.138.69' IDENTIFIED BY 'mysql';

CREATE USER 'root'@'192.168.138.161' IDENTIFIED BY 'mysql';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'ip_address';

FLUSH PRIVILEGES;

****************************************

> # [PART 2](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m4)

> 10.Make backup of your database.

mysqldump.exe -uroot -pmysql --all-databases > 2.sql

> 11.Delete the table and/or part of the data in the table. 
12.Restore your database.

mysql -uroot -pmysql   <c:\mysql\folder\2.sql

> 13.Transfer your local database to RDS AWS.

mysql -uroot -p -h ostapenko.cj200uvdjahq.eu-central-1.rds.amazonaws.com --all-databases > awsdump.sql

# [man](https://aws.amazon.com/getting-started/hands-on/move-to-managed/migrate-my-sql-to-amazon-rds/)

# [man](https://eu-central-1.console.aws.amazon.com/rds/home?region=eu-central-1#databases:)

[![*Report in screenshots*](shreenshot/3.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)


> # [PART 3](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m4)

mysql -uroot -p -h ostapenko.cluster-cj200uvdjahq.eu-central-1.rds.amazonaws.com < C:/mysql/folder/1.sql

mysql -uroot -p -h ostapenko.cluster-cj200uvdjahq.eu-central-1.rds.amazonaws.com

[![*Report in screenshots*](shreenshot/4.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)

