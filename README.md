# SQL-Queries
SQL QUERIES from Starting

> ***Create DataBase***


```js 
  create DATABASE users
```

> ***use Database***


```js 
    use users
```

> ***show all the tables***

```js
     show tables
```

> ***create table:~***

```js
     create table students(
        name varchar(255),
       email varchar(50),
      code varchar(10),
      batch varchar(30)
     );
```

> ***table content:~***

```js
    describe students
```

> ***Insert in to tables***

```js
     insert into students (name,email,code,batch) values("Anamika","a@gmail.com","pw1_006" ,"pt_web1") ;
```

> ***how to get data of particular tables***

```js
  select * from students
```


> ***how to get single field***

```js
    select name from students
```


> ***how to get multiple fields***

```js
    select name,email from students
```

> ***How to limit the data***

```js
    select name,email from students limit 2
```


> ***NOTE : ~ We store the data in files in DBMS
and we store the data in tables in RDBMS***

> ***How to count all the data***
```js
    select count(*) from students
```

> ***how to use where clause***
```js
    select * from students where name="Anamika"
```


> ***how to use and or operator***

```js
    select * from students where name="Anamika" and batch="pt_web1"
```
```js
select * from students where name="Anamika" or name="Aisha"
```

> ***How to add new column in existing table***
```js
    AlTER TABLE students
    ADD age INT;
```

> ***how to drop column***
```js
    DROP COLUMN age
```


> ***If age is 30 or 35***
```js
    select name,age from students WHERE age in(30,35)
```


> ***if age is in between 30 35*** 
```js
    select name,age from students WHERE age between 30 and 35;
```
> ***Note:~ 30,35 will also be included***

> ***how to print age in desc***
```js
    select name,age from students WHERE age between 30 and 35 order by age desc;
```

> ***how to print age in asc***
```js
    select name,age from students WHERE age between 30 and 35 order by age asc;
```

> ***How to skip and limit***
```js
    select name,age from students WHERE age between 30 and 35 order by age asc limit 1,2;
 ```
> ***NOTE:~ this will skip 1 then print 2***

> ***Select the name whose name start with A***
```js
    select name,age from students WHERE name like "A%" order by age asc limit 1,2;
 ```

> ***Select the name whose name ends with a***
```js
    select name,age from students WHERE name like "%a" order by age asc limit 1,2;
```

> ***Select the name if there is any 'a' in their name***
```js
  select name,age from students WHERE name like "%a%" order by age asc limit 1,2;
```

> ***How to change the particular column_name***
```js
    SELECT DISTINCT name as Student_name from students;
```

> ***How to update the particular field***
```js
    UPDATE students SET age=19 where age=35;
    
```
> ***NOTE:~ Update the age of 35 to 19***

> ***How to update the age if the age is NULL***
```js
    UPDATE students SET age=19 where age IS NULL;
```

> ***how to find min  age from students***
```js
    select MIN(age) from students
```

> ***how to find max  age from students***
```js
    select MAX(age) from students;
```

> ***how to find AVG  age from students***
```js
  select AVG(age) from students;
```

# Assignment:~1


> ***Create DATABASE patients manually***
> ***How to import this sql file***
```js
    mysql -u root -p patients < patients(in that particular folder)
```


> ***GROUP BY :~ The GROUP BY statement groups rows that have the same values***
```js
    select age as AGE from patients GROUP BY age
```

```js select age as AGE,count(*) as Counts from patients GROUP BY age,severity having Counts>3
```

> ***Select severity and count of that particular severity***
```js
    select severity,count(*) as counts from patients group by severity;
```

> ***Nested Query***

```js
    select severity,count(*) as Counts from (SELECT * from patients where age>20) as pat group by severity;
```


> ***Calculate BMI***


```js
    SELECT patient_name,(weight/(height*height)) as patient_bmi ,height,weight from patients order by patient_bmi desc limit 50;
```

> ***select hospital and count of hospital***
```js
    SELECT hospital,count(*) as Counts from patients group by hospital;
```


> ***Select avg age group by hospital***
```js
    SELECT AVG(age) as AVG_AGE,hospital,count(*) as Counts from patients group by hospital;
```

> ***select avg_bmi from patients***
```js
    SELECT AVG(weight/(height*height)) as AVG_BMI from patients
```

> ***select avg_bmi from patients group by hospital***
```js
    SELECT AVG(weight/(height*height)),hospital as AVG_BMI from patients group by hospital;
```

> ***Select avg_bmi from patients group by severity***
```js
    SELECT AVG(weight/(height*height)),severity as AVG_BMI from patients group by severity;
```

> ***Find date (diagnosis date) wise in ascending order total no of patients***
```js
    select date_of_diagnosis,count(*) as Counts from patients as date group by date_of_diagnosis order by  date_of_diagnosis asc;
```

> ***show all users who bmi is between two values ( you can decide the values )***
```js
    select patient_name,(weight/(height*height)) as patient_bmi from patients having patient_bmi between 0.003 and 0.0038;
 ```

> ***NOTE:~ WHERE CLAUSE will not work here***
> ***SQL is evaluated backwards, from right to left. So the where clause is parsed and evaluate prior to the select clause. Because of this the aliasing of u_name to user_name has not yet occurred.***
> ***So when you are going to evaluate something which is renamed and not present in original schema you will get and error since we have renamed it at left side while SQL evaluate from right side. Hence we need to use HAVING Clause in order to get rid of this error.***


> ***```SELECT u_name AS user_name FROM users WHERE user_name = "john"```;
This is WRONG WAY OF DOING , IT WILL GENERATE ERROR;
```SELECT u_name AS user_name FROM users HAVING user_name = "john"```;
This is correct way of doing***

> ***show top 10 weighing patients***
```js
    select patient_name,weight from patients order by weight desc limit 10;
```

> ***show second top 10 weighing patients***
```js
    select patient_name,weight from patients order by weight desc limit 10,10;
```

> ***show count of users with name which start with B***
```js
    select count(*) from patients where patient_name like "B%";
```

> ***show count of users whose name end with E***
```js
    select count(*) from patients where patient_name like "%E";
```

> ***show count of users whose name have LL on it***
```js
select count(*) from patients where patient_name like "%ll%";
```

```js
## Problem 2
- create a country table
- it should have id, and name, id is the primary key
- create a users table
- it needs to have a primary key
- id, name, country id
- id is primary key
- country is a foreign key to country table primary key

```

```js
create database country;
```
```js
  use country;
```
```js
    CREATE TABLE country (  id INT NOT NULL AUTO_INCREMENT, name varchar(255) NOT NULL, PRIMARY KEY (id));
```
```js
CREATE TABLE users (user_id INT NOT NULL AUTO_INCREMENT,
                                      name varchar(255),
                                      country_id INT NOT NULL,
                                      id INT,
                                      PRIMARY KEY (user_id),
                                      FOREIGN KEY (id)
                                     REFERENCES country(id));
```
