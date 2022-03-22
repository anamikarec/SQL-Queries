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

